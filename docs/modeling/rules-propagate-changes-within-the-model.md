---
title: "ルールには、モデル内の変更が反映されるまでください。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ドメイン モデルをプログラミングのドメイン固有言語"
  - "ドメイン固有言語の規則"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# ルールには、モデル内の変更が反映されるまでください。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

別の視覚化およびモデリング SDK \(VMSDK\) で 1 つの要素から変更を伝達するストアのルールを作成することができます。 ストア内の任意の要素に変更する場合は、ルールは、最も外側のトランザクションがコミットされるときに通常実行される予定です。 さまざまな種類の要素を追加または削除するなどのイベントの種類のルールがあります。 ルールは、特定の種類の要素、図形、または図をアタッチできます。 多くの組み込み機能は、ルールによって定義されます。 など、ルールでは、モデルが変更されたときに、ダイアグラムが更新されることを確認します。 独自の規則を追加することで、ドメイン固有言語をカスタマイズできます。  
  
 ストアの規則は、プロパティをモデル要素、リレーションシップ、図形またはコネクタ、およびそのドメインに変更は、– ストア内の変更を反映するために特に便利です。 ルールは、ユーザーは、Undo または Redo のコマンドを呼び出したときに実行されません。 代わりに、トランザクション マネージャーにより、ストアの内容が正しい状態に復元されたことを確認します。 ストア外のリソースに変更を反映する場合は、イベントの格納を使用します。 詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
 たとえば、ユーザー \(または、コード\) は、型 ExampleDomainClass の新しい要素を作成するときに、モデルの別の部分に別の型の別の要素が作成されるように指定するとします。 AddRule を記述し、ExampleDomainClass に関連付けることでした。 その他の要素を作成するルールではコードを記述します。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  ルールのコードは、ストア内の要素のみの状態を変更する必要があります。つまり、ルールでは、モデル要素、リレーションシップ、図形、コネクタ、図、またはそれらのプロパティのみを変更する必要があります。 ストア外のリソースに変更を反映する場合は、保存のイベントを定義します。 詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
### ルールを定義するには  
  
1.  クラスが始まると、ルールを定義、 `RuleOn` 属性です。 属性は、ドメイン クラス、リレーションシップ、図の要素のいずれかをルールを関連付けます。 このルールは、抽象可能性のあるこのクラスの各インスタンスに適用されます。  
  
2.  によって返されるセットに追加して、ルールを登録 `GetCustomDomainModelTypes()` ドメイン モデル クラスにします。  
  
3.  抽象の規則クラスのいずれかの規則クラスを派生し、実行メソッドのコードを記述します。  
  
 次のセクションでは、これらの手順の詳細について説明します。  
  
### ドメイン クラスのルールを定義するには  
  
-   カスタム コード ファイルにクラスを定義し、前にプレフィックス、 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 属性。  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   最初のパラメーターで、サブジェクトの種類には、ドメイン クラス、ドメイン リレーションシップ、図形、コネクタ、またはダイアグラムができます。 通常、ドメイン クラスとリレーションシップにルールを適用します。  
  
     `FireTime` は通常 `TopLevelCommit`です。 これにより、トランザクションのすべての主な変更が加えられた後にのみ、ルールを実行します。 その他の方法はインラインで、変更後すぐに、ルールを実行します。LocalCommit で、\(最も外側できない可能性があります\) を現在のトランザクションの最後に規則を実行します。 キューでは、順序に影響するルールの優先順位を設定することもできますが、これは必要とする結果を実現するための信頼性の低いメソッド。  
  
-   抽象クラスは、サブジェクトの種類として指定できます。  
  
-   ルールは、サブジェクト クラスのすべてのインスタンスに適用されます。  
  
-   既定値 `FireTime` TimeToFire.TopLevelCommit です。 これにより、最も外側のトランザクションがコミットされるときに実行されるルールです。 別の方法は、TimeToFire.Inline です。 これにより、トリガーを起動するイベントの直後に実行されるルールです。  
  
### ルールを登録するには  
  
-   によって返される型の一覧にルール クラスを追加 `GetCustomDomainModelTypes` ドメイン モデルで。  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   ドメイン モデル クラスの名前がない場合は、ファイルを調べる **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   このコードを DSL プロジェクト内のカスタム コード ファイルに記述します。  
  
### ルールのコードを記述するには  
  
-   次の基本クラスのいずれかの規則クラスを派生します。  
  
    |基底クラス|トリガー|  
    |-----------|----------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|要素、リンク、または図形が追加されます。<br /><br /> これを使用して、新しい要素に加え、新しいリレーションシップを検出します。|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|ドメイン プロパティの値を変更します。 このメソッドの引数は、新旧の値を提供します。<br /><br /> 図形は、この規則がトリガーされたときに、組み込み `AbsoluteBounds` プロパティが変更された、図形が移動された場合。<br /><br /> 多くの場合、オーバーライドする方が便利です `OnValueChanged` または `OnValueChanging` プロパティ ハンドラーでします。 変更の前後にすぐに、これらのメソッドは呼び出されます。 これに対し、通常、ルールが、トランザクションの最後に実行します。 詳細については、「[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)」を参照してください。 **Note:**  リンクを作成または削除されたときに、このルールはトリガーされません。 代わりに、書き込み、 `AddRule` と `DeleteRule` ドメイン リレーションシップにします。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|要素またはリンクが削除されようとしてのときにトリガーします。 ModelElement.IsDeleting プロパティは、トランザクションの終わりまで true です。|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|要素またはリンクが削除されたときに実行されます。 その他のすべてのルールの実行後、DeletingRules を含め、ルールが実行されます。 ModelElement.IsDeleting が false の場合と ModelElement.IsDeleted です。 後続の元に戻すには、要素は実際には削除されず、メモリから Store.ElementDirectory から削除されます。|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|要素は、別のストアを 1 つのパーティションから移動されます。<br /><br /> \(これは、関連していないこと、グラフ上の図形の位置に注目してください\)。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|このルールは、ドメイン リレーションシップにのみ適用されます。 これは、ような状況は、リンクの先頭または末尾にモデル要素を明示的に割り当てる場合にトリガーされます。|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|要素またはリンクの順序が変更のリンク、MoveBefore または MoveToIndex メソッドを使用すると発生します。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|トランザクションの作成時に実行します。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|トランザクションがコミットされると実行されます。|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|トランザクションがロールバックされると実行されます。|  
  
-   各クラスには、オーバーライドするメソッドがあります。 型 `override` 検出には、クラスにします。 このメソッドのパラメーターは、変更する要素を識別します。  
  
 ルールは次の点に注意してください。  
  
1.  一連の変更をトランザクションには、多くのルールをトリガー可能性があります。 通常、ルールは、最も外側のトランザクションがコミットされるときに実行されます。 不特定の順序で実行されます。  
  
2.  規則は常に、トランザクションの内部実行します。 そのためを変更する新しいトランザクションを作成する必要はありません。  
  
3.  トランザクションがロールバックされるときに、または元に戻す\/やり直しの操作が実行されたルールは実行されません。 これらの操作は、ストアのすべてのコンテンツを以前の状態にリセットされます。 そのため、ルールには、ストアの外部の状態が変更された場合していない可能性がない synchronism をストアとのコンテンツ。 ストア以外の状態を更新するには、イベントを使用することをお勧めします。 詳細については、「[イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)」を参照してください。  
  
4.  モデルがファイルから読み込まれるときに、いくつかのルールが実行されます。 読み込みまたは保存は、進行中かどうかを確認するに `store.TransactionManager.CurrentTransaction.IsSerializing`します。  
  
5.  ルールのコードでは、複数のルールのトリガーを作成する場合、起動リストの末尾に追加され、トランザクションが完了する前に実行されます。 DeletedRules は、その他のすべてのルールの後に実行されます。 1 つのルールは、変更ごとに 1 回のトランザクションで何度もを実行できます。  
  
6.  内の情報を格納するルールとの情報を渡すため、 `TransactionContext`です。 これは、トランザクション中に保持されている辞書だけです。 トランザクションが終了すると、破棄されます。 各ルールのイベント引数は、それにアクセスを提供します。 予測可能な順序でルールが実行されるしないことに注意してください。  
  
7.  他の方法を検討した後の規則を使用します。 たとえば、値が変更されたときにプロパティを更新する場合は、計算されるプロパティを使用して検討してください。 サイズまたは図形の場所を制限する場合を使用して、 `BoundsRule`です。 プロパティの値の変更に反応する場合は、追加、 `OnValueChanged` プロパティ ハンドラー。 詳細については、「[変更内容への対応および変更内容の反映](../modeling/responding-to-and-propagating-changes.md)」を参照してください。  
  
## 使用例  
 次の例は、2 つの要素をリンクするドメインの関係がインスタンス化されるときに、プロパティを更新します。 だけでなく、ユーザーを作成すると、リンク、ダイアグラムに以外にもプログラム コードのリンクを作成する場合、ルールを起動します。  
  
 この例をテストするには、Task Flow ソリューション テンプレートを使用して DSL を作成し、Dsl プロジェクト内のファイルに次のコードを挿入します。 構築し、ソリューションを実行し、デバッグ プロジェクトでサンプル ファイルを開きます。 コメントの図形とフロー要素間には、コメントのリンクを描画します。 コメント内のテキストは、レポートに接続している最新の要素を変更します。  
  
 実際には、通常すべて AddRule のため、DeleteRule に記述するとします。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## 参照  
 [イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)