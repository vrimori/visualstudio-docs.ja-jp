---
title: "読み取り専用のセグメントを作成するロックのポリシーを定義する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6848f2c0b6c8d25fe7964fdb5519aa3f075bde57
ms.sourcegitcommit: 69b898d8d825c1a2d04777abf6d03e03fefcd6da
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>ロック ポリシーの定義と読み取り専用セグメントの作成
不変性 API、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK により、ドメイン固有言語 (DSL) モデルのロックの一部またはすべてのプログラムの読み取りが変更されていないことができるようにします。 この読み取り専用のオプションでしたするなど、使用できるように、ユーザーが仕事仲間に注釈を付け、DSL モデルの確認を求めることができますが、変更、元の変更を禁止することができます。  
  
 さらに、作成者は、DSL の定義、*ロック ポリシー。* ロックのポリシーは、あるロックが許可されている、許可されていない、または固定を定義します。 たとえば、DSL を発行するときに新しいコマンドで拡張するサード パーティの開発者がように促すことができます。 モデルの指定した部分の読み取り専用の状態を変更できないようにするロックのポリシーを使用することもできます。  
  
> [!NOTE]
>  ロックのポリシーは、リフレクションを使用して回避できます。 クリア境界にサード パーティの開発者が、強力なセキュリティは提供されません。  
  
 詳細およびサンプルについては、Visual Studio で使用可能[Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) Web サイトです。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
  
## <a name="setting-and-getting-locks"></a>設定とロックの取得  
 ストア、パーティション、または個々 の要素は、ロックを設定できます。 たとえば、このステートメントは、モデル要素が削除されないようにすると、また、プロパティ変更されないようにです。  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 その他のロックの値は、関係、要素の作成、パーティション、およびロールの順序を再リンク間の移動の変更を防ぐために使用できます。  
  
 ロックは、ユーザーの操作とプログラム コードの両方に適用されます。 プログラム コードが、変更を試みると、`InvalidOperationException`がスローされます。 元に戻す/やり直し操作では、ロックが無視されます。  
  
 要素を使用して指定されたセット内のロックを保持かどうかを検出できます`IsLocked(Locks)`とを使用して現在の要素のロックのセットを取得できる`GetLocks()`です。  
  
 トランザクションを使用しても、ロックを設定できます。 ロック データベースは、ストアの一部ではありません。 ストア内の値の変化への応答でロックを設定する場合など OnValueChanged にする必要があります変更を許可する元に戻す操作の一部であります。  
  
 これらのメソッドは拡張メソッドで定義されている、<xref:Microsoft.VisualStudio.Modeling.Immutability>名前空間。  
  
### <a name="locks-on-partitions-and-stores"></a>パーティションとストアのロック  
 ロックは、パーティションと、ストアにも適用できます。 パーティションに設定されているロックはパーティション内のすべての要素に適用されます。 そのため、たとえば、次のステートメントはパーティション内のすべての要素削除されないように、独自のロックの状態に関係なく。 ただし、他のロックなど`Locks.Property`でした個々 の要素に設定できます。  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 ストアに設定されているロックは、そのロックのパーティションと、要素の設定に関係なく、そのすべての要素に適用されます。  
  
### <a name="using-locks"></a>ロックを使用します。  
 次の例などのパターンを実装するのにロックを使用できます。  
  
-   すべての要素および関係のコメントを表すものを除くへの変更を許可しないようにします。 これにより、それを変更することがなく、モデルの注釈を設定できます。  
  
-   既定のパーティションに変更を禁止しますが、ダイアグラムのパーティションに変更を許可します。 ユーザーは、図を並べ替えることができますが、基になるモデルを変更することはできません。  
  
-   別のデータベースに登録されているユーザーのグループを除く、ストアへの変更を許可しないようにします。 他のユーザーの図とモデルは読み取り専用になります。  
  
-   ダイアグラムのブール型プロパティが設定されている場合、モデルへの変更が行われないよう true に設定します。 そのプロパティを変更するメニュー コマンドを提供します。 これにより、それらを行わないユーザーが誤って変更します。  
  
-   加算して、要素の削除、および特定のクラスの関係を許可しないが、プロパティの変更を許可します。 これにより、固定フォームのプロパティを埋めることができます。  
  
## <a name="lock-values"></a>ロックの値  
 ロックは、ストア、パーティション、または個々 のモデル要素に設定できます。 ロックは、`Flags`列挙: を使用してその値を組み合わせることができます ' &#124;'。  
  
-   ModelElement のロックには、そのパーティションのロックが常に含まれています。  
  
-   パーティションのロックには、常に、ストアのロックが含まれています。  
  
 パーティション上のロックを設定、格納またはと、同時に、個々 の要素のロックを無効にすることはできません。  
  
|[値]|つまり場合`IsLocked(Value)`が true|  
|-----------|------------------------------------------|  
|なし|制限はありません。|  
|プロパティ|要素のドメインのプロパティを変更することはできません。 これは、リレーションシップ内のドメイン クラスの役割によって生成されるプロパティには適用されません。|  
|追加|パーティションに新しい要素とのリンクを作成できませんまたは保存します。<br /><br /> 適用されません`ModelElement`です。|  
|移動|要素の場合、パーティション間で移動できません`element.IsLocked(Move)`が true である場合、または`targetPartition.IsLocked(Move)`は true です。|  
|削除|か、このロックは要素自体に設定する要素のいずれかの削除は反映されるまで、埋め込まれた要素や図形など、要素を削除できません。<br /><br /> 使用することができます`element.CanDelete()`要素を削除できるかどうかを検出します。|  
|順序を変更します。|Roleplayer にあるリンクの順序を変更できません。|  
|RolePlayer|この要素に基づいているリンクのセットを変更することはできません。 たとえば、新しい要素は、この要素の下で埋め込むことができません。 これには、この要素は、ターゲットへのリンクは影響しません。<br /><br /> この要素は、リンク、そのソースとターゲットは影響しません。|  
|すべて|他の値のビットごとの OR。|  
  
## <a name="locking-policies"></a>ロックのポリシー  
 DSL の作成者は、定義することができます、*ロック ポリシー*です。 ロックのポリシーは、おけば、特定のロックを設定または特定のロックを設定する必要があることを要求できるように、SetLocks() の操作を保ちます。 ユーザーまたは開発者は、同様に、変数を宣言することができます、DSL の用途を誤って contravening を防ぐため、ロックのポリシーを使用する通常、`private`です。  
  
 ロックのポリシーを使用して、要素の型に依存するすべての要素のロックを設定することができますも。 これは、ため`SetLocks(Locks.None)`要素が初めて作成したり、ファイルから逆シリアル化されたときに常に呼び出されます。  
  
 ただし、ライフ サイクル中に要素のロックを変更するのにポリシーを使用することはできません。 その効果を達成するのへの呼び出しを使用する必要があります`SetLocks()`です。  
  
 ロックのポリシーを定義するのには、する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> を実装するクラスを作成します。  
  
-   このクラスを DSL の DocData から使用可能なサービスに追加します。  
  
### <a name="to-define-a-locking-policy"></a>ロックのポリシーを定義するには  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>次の定義があります。  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 呼び出しが行われたときにこれらのメソッドが呼び出されます`SetLocks()`ストア、パーティション、または ModelElement でします。 各メソッドでは、ロックの提案されたセットで提供されます。 提案のセットを返すことができます、または追加してロックを減算します。  
  
 例:  
  
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
  
 他の場合でも、要素をユーザーがいつでも削除できるかどうかを確認するには、コードの呼び出し`SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 MyClass のすべての要素のすべてのプロパティの変更を禁止します。  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>ポリシーをサービスとして使用できるようにするには  
 `DslPackage`プロジェクトで、次の例のようなコードを含む新しいファイルを追加します。  
  
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
