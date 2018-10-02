---
title: 読み取り専用セグメントを作成するロック ポリシーの定義 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8af4722d76b9d68f4e880175bccdb1730b6e163b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545043"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>ロック ポリシーの定義と読み取り専用セグメントの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[読み取り専用セグメントを作成するロックのポリシーを定義する](https://docs.microsoft.com/visualstudio/modeling/defining-a-locking-policy-to-create-read-only-segments)します。  
  
不変性 API、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK のロックの一部またはすべてのドメイン固有言語 (DSL) モデルをプログラムを保存できるため、読み取りが変更されていないことができます。 この読み取り専用オプションされる可能性があります、たとえば、ユーザーが仕事仲間の注釈を付け、DSL モデルを確認するように依頼できますが、元の変更を禁止することができますようにします。  
  
 さらに、作成者は、DSL の定義、*ロック ポリシー。* ロックのポリシーは、どのロックが許可されている、許可されない、または必須を定義します。 たとえば、DSL を発行するときに、サード パーティの開発者に新しいコマンドでは拡張をお勧めすることができます。 モデルの指定した部分の読み取り専用の状態を変更することを防ぐためにロック ポリシーを使用することもできます。  
  
> [!NOTE]
>  リフレクションを使用してロックのポリシーを回避することができます。 サードパーティの開発者は、明確な境界を提供しますが、強力なセキュリティは提供されません。  
  
 詳細およびサンプルについてでご利用いただけますが、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) Web サイト。  
  
## <a name="setting-and-getting-locks"></a>設定とロックの取得  
 ストア、パーティション、または個々 の要素は、ロックを設定できます。 たとえば、このステートメントは、モデル要素が削除されないようにするともにより、そのプロパティの変更です。  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 その他のロックの値は、関係、要素の作成、パーティション、およびロールの再注文リンク間の移動の変更を防ぐために使用できます。  
  
 ロックには、ユーザーの操作とプログラム コードの両方が適用されます。 プログラム コードを変更しようとすると、`InvalidOperationException`がスローされます。 元に戻す/やり直し操作では、ロックが無視されます。  
  
 要素を使用して特定セットのすべてのロックを持つかどうかを検出する`IsLocked(Locks)`を使用して現在の要素のロックのセットを取得することができますと`GetLocks()`します。  
  
 トランザクションを使用せず、ロックを設定できます。 ストアの一部でないロック データベース。 ストア内の値の変化への応答でロックを設定する場合など、OnValueChanged でする必要があります変更を許可する元に戻す操作の一部であります。  
  
 これらのメソッドは拡張メソッドで定義されている、<xref:Microsoft.VisualStudio.Modeling.Immutability>名前空間。  
  
### <a name="locks-on-partitions-and-stores"></a>パーティションとストアのロック  
 ロックは、パーティションと、ストアにも適用できます。 パーティションが設定されているロックはパーティション内のすべての要素に適用されます。 したがって、たとえば、次のステートメントはパーティション内のすべての要素削除されないように、独自のロックの状態に関係なく。 ただし、その他のロックなど`Locks.Property`個々 の要素にも設定できます。  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 ストアが設定されているロックは、そのロックのパーティションと、要素の設定に関係なく、そのすべての要素に適用されます。  
  
### <a name="using-locks"></a>ロックを使用します。  
 ロックは、次の例などのスキームを実装するために使用できます。  
  
-   すべての要素および関係のコメントを表すものを除くへの変更を禁止します。 これにより、これを変更することがなく、モデルの注釈を設定できます。  
  
-   既定のパーティションに変更を禁止しますが、ダイアグラムのパーティションの変更を許可します。 ユーザーは、図を並べ替えることができますが、基になるモデルを変更することはできません。  
  
-   別のデータベースに登録されているユーザーのグループを除く、ストアへの変更を禁止します。 他のユーザーの図とモデルは読み取り専用になります。  
  
-   ダイアグラムのブール型プロパティが設定されている場合は、モデルへの変更を許可しないようにを true にします。 そのプロパティを変更するメニュー コマンドを提供します。 これにより、ようにしないユーザーが誤って変更することを確認できます。  
  
-   加算して、要素の削除、および特定のクラスの間のリレーションシップを許可しないが、プロパティの変更を許可します。 これにより、ユーザーが、固定のフォーム プロパティを入力できます。  
  
## <a name="lock-values"></a>ロックの値  
 ロックは、ストア、パーティション、または個々 のモデル要素を設定できます。 ロックは、`Flags`列挙: を使用してその値を組み合わせることができます '&#124;'。  
  
-   倉庫管理ロックには、常にそのパーティションのロックが含まれています。  
  
-   パーティションのロックには、常に、ストアのロックが含まれています。  
  
 パーティションにロックを設定または保存し、同時に、個々 の要素のロックを無効にすることはできません。  
  
|[値]|つまり場合`IsLocked(Value)`が true|  
|-----------|------------------------------------------|  
|なし|制限はありません。|  
|プロパティ|要素のドメインのプロパティを変更できません。 これは、リレーションシップ内のドメイン クラスの役割によって生成されるプロパティには適用されません。|  
|追加|パーティションに新しい要素およびリンクを作成できませんまたは保存します。<br /><br /> 該当しません`ModelElement`します。|  
|移動|要素の場合、パーティション間で移動できません`element.IsLocked(Move)`が true の場合または`targetPartition.IsLocked(Move)`は true。|  
|削除|このロックは、要素自体で設定するかする要素のいずれかで削除が反映されるまで、埋め込まれた要素や図形など、要素を削除できません。<br /><br /> 使用することができます`element.CanDelete()`要素を削除できるかどうかを検出します。|  
|順序を変更します。|Roleplayer にあるリンクの順序を変更できません。|  
|RolePlayer|この要素がソースとリンクのセットを変更できません。 たとえば、新しい要素は、この要素の下に埋め込むことができません。 これには、この要素は、ターゲットのリンクは影響しません。<br /><br /> この要素は、リンクは、そのソースとターゲットは影響しません。|  
|すべて|その他の値のビットごとの OR。|  
  
## <a name="locking-policies"></a>ロック ポリシー  
 DSL の作成者は、定義することができます、*ロック ポリシー*します。 ロックのポリシーは、特定のロックが設定または特定のロックを設定する必要がありますを必須にされているようにするために、SetLocks() の操作を保ちます。 通常、ユーザーまたは開発者は、変数を宣言することができますと同様に、DSL の使用目的を誤って contravening を防ぐためにロック ポリシーを使用`private`します。  
  
 要素の型に依存するすべての要素のロックを設定するのにロックのポリシーを使用することもできます。 これは、ため`SetLocks(Locks.None)`要素が初めて作成したり、ファイルから逆シリアル化されたときに常に呼び出されます。  
  
 ただし、ライフ サイクル中に、要素のロックを変更するのにポリシーを使用することはできません。 その効果を実現するには呼び出しを使用する必要があります`SetLocks()`します。  
  
 ロック ポリシーを定義するには、する必要があります。  
  
-   <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> を実装するクラスを作成します。  
  
-   このクラスを DSL の DocData を介して利用できるサービスに追加します。  
  
### <a name="to-define-a-locking-policy"></a>ロック ポリシーを定義するには  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 次の定義があります。  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 呼び出しが行われたときに、これらのメソッドが呼び出されますが`SetLocks()`ストア、パーティション、またはモデル要素にします。 各メソッドでロックの提案セットが提供されます。 提案のセットを返すことができます、または追加し、ロックを減算できます。  
  
 例えば:  
  
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
  
 その他の場合でも、要素をユーザーがいつでも削除できるかどうかを確認するには、コードの呼び出し `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 MyClass のすべての要素のすべてのプロパティの変更を禁止します。  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>ポリシーをサービスとして使用できるようにするには  
 `DslPackage`プロジェクトに、次の例のようなコードを含む新しいファイルを追加します。  
  
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



