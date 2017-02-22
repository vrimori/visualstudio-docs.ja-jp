---
title: "ロック ポリシーの定義と読み取り専用セグメントの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 12
caps.handback.revision: 12
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# ロック ポリシーの定義と読み取り専用セグメントの作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の Visualization and Modeling SDK の不変性 API はセッション状態ではない可能性があるためプログラムの \(DSL\) 一部またはドメイン固有言語モデルをすべてロックできるようにします。  この読み取り専用のオプションを使用できます。たとえばユーザーのコンピューターに指定し確認方法で呼び出すことができるようにDSL モデルは元の変更で禁止できます。  
  
 またDSL の作成者は *ロックのポリシーを*  定義できます *。*ロックが必須与えられたりロックされています。ポリシーを定義します。  たとえばDSL を発行するとサードパーティの開発者が新しいコマンドでそれを拡張する場合に図ることができます。  ただしまたモデルの指定した部分の読み取り専用ステータスの変更を防止するにロックのポリシーを使用できます。  
  
> [!NOTE]
>  ロックのポリシーはリフレクションを使用することで回避できます。  またサードパーティの開発者に明確な境界を提供しますが厳密なセキュリティを提供しません。  
  
 詳細および例では [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の Web サイトから入手できます。[Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128)  
  
## ロックの設定と取得  
 ストアにパーティションまたは個々の要素のロックを設定できます。  たとえば次のステートメントはプロパティが変更されるのを防ぐ削除されるのを防ぐモデル要素の場合 :  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 ロールで他のロックの値はリレーションシップ要素の作成パーティションリンクの順序を変更するのに移動の変更を防止するために使用できます。  
  
 ロックはユーザー アクションとプログラム コードに適用されます。  プログラム コードの変更を行おうとすると `InvalidOperationException` がスローされます。  ロックは元に無視するかまたは操作をやり直してから\/LTCG。  
  
 `GetLocks()` のことを使用して要素に指定された文字列で `IsLocked(Locks)` を使用してロックが要素のロックの現在の設定を取得できるかどうかを検出できます。  
  
 トランザクションを使用せずにロックを設定できます。  ロックのデータベースがストアの一部ではありません。  ストア値の変更に応答してロックを設定するとたとえば OnValueChanged で取り消し操作の一部である変更を許可する必要があります。  
  
 これらのメソッドは <xref:Microsoft.VisualStudio.Modeling.Immutability> の名前空間で定義されている拡張メソッド。  
  
### パーティションストア内のロック  
 ロックはパーティションストアに適用できます。  パーティションに設定されたロックはパーティション内のすべての要素に適用されます。  たとえば次のステートメントはパーティション内のすべての要素が独自のロック状態に関係なく削除されるのを防ぎます。  いずれにしても`Locks.Property` などのロックは個々の要素に設定できます :  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 ストアで設定されたロックはパーティションその要素のロックの設定に関係なくすべての要素に適用されます。  
  
### ロックを使用する  
 次の例のような構成を実行するにはロックを使用する :  
  
-   すべての要素に対する変更およびコメントを表すを除く関係を拒否します。  これはユーザーがデータを変更せずにモデルに注釈を付けることができます。  
  
-   既定のパーティションの変更を許可します。ただし図のパーティションの変更を許可します。  ユーザーが図を再配置できます。基本モデルを変更することはできません。  
  
-   別のデータベースに登録されているユーザーのグループの除外ストアに変更を拒否します。  他のユーザーの場合図とモデルは読み取り専用です。  
  
-   図のブール型プロパティが True に設定モデルへの変更を許可します。  このプロパティを変更するメニュー コマンドを指定します。  これはユーザーが誤って変更しないようにすることができます。  
  
-   要素の追加と削除特定のクラスの関係を拒否します。ただしプロパティの変更を許可します。  これは固定形式プロパティを格納できるかをユーザーに提供できます。  
  
## ロックの値  
 ロックはストア パーティションまたはユーザー ModelElement で設定できます。  ロックは `Flags` の列挙型です : 値を 「を使用して組み合わせることができます。&#124; 」。  
  
-   ModelElement のロックはパーティションのロックが常に含まれています。  
  
-   パーティションのロックはストアのロックが常に含まれています。  
  
 パーティションのロックを設定するか個々の要素でロックを保存し同時に無効にすることはできません。  
  
|値|`IsLocked(Value)` に当てはまる場合です。|  
|-------|-----------------------------------|  
|なし|制約はありません。|  
|プロパティ|要素のドメインのプロパティは変更できません。  これはリレーションシップのドメイン クラスの役割によって生成されるプロパティには適用されません。|  
|追加|新しい要素とリンクを格納またはパーティションに作成できません。<br /><br /> `ModelElement` に適用できません。|  
|移動|要素はパーティションの間で `element.IsLocked(Move)` が true であるかまたは `targetPartition.IsLocked(Move)` 場合は移動できません。|  
|\[削除\]|要素が削除が連結して要素や図形などの要素でこのロックが要素のセットがの場合または削除することはできません。<br /><br /> 要素を削除できるかどうかを確認するために `element.CanDelete()` を使用できます。|  
|\[順番の再変更\]|roleplayer のリンクについては変更できません。|  
|RolePlayer|この要素で指定されているリンクの設定は変更できません。  たとえば新しい要素はこの要素の下に埋め込むことはできません。  この要素がターゲットのリンクには影響しません。<br /><br /> この要素はリンクであるためソースとターゲットは影響を受けません。|  
|すべて|ビットごとの OR 他の値。|  
  
## ポリシーのロック  
 DSL の作成者は *ロックのポリシーを*  定義できます。  ロックのポリシーができるようにSetLocks の演算 \(\) 管理特定のロックは設定になるのを防ぐことまたは特定のロックは設定する必要があることを必須とする。  通常変数を宣言できます `private`誤って DSL の用途に変換することでユーザーまたは開発者にロックするのを防ぐことのポリシーを使用します。  
  
 またすべての要素のロックを要素の型に依存する設定のロックのポリシーを使用できます。  つまり要素はファイルから最初に作成されたときや逆シリアル化されるとき `SetLocks(Locks.None)` が常に呼び出されるためです。  
  
 ただし期間中に要素のロックを変更するためのポリシーを使用できません。  その結果を得るには`SetLocks()` の呼び出しを使用する必要があります。  
  
 ロックのポリシーを定義する必要があります :  
  
-   <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 実装するクラスを作成します。  
  
-   DSL の DocData で使用できるサービスをこのクラスに追加します。  
  
### ロックのポリシーを定義するには  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> は次のシグネチャがあります :  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 これらのメソッドは呼び出しがストア パーティションまたは ModelElement で `SetLocks()` になるときに呼び出されます。  各メソッドで指定された一連のロックされます。  推奨される設定を返すこともロックを加算します。  
  
 次に例を示します。  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 他のコードが `SetLocks(Lock.Delete):` を呼び出してもユーザーが要素を必ず削除できることを確認します。  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 MyClass の各要素のすべてのプロパティの変更を許可するには :  
  
 `return element is MyClass ?  (proposedLocks | Locks.Property) : proposedLocks;`  
  
### ポリシーがサービスとして設定するには  
 `DslPackage` のプロジェクトでは次の例のようなコードを含む新しいファイルを追加します :  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```