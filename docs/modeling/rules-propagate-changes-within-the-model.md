---
title: 規則によって変更内容がモデル内に反映される
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3e1abc17e9675423359c6f850056a2fedf062e01
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567023"
---
# <a name="rules-propagate-changes-within-the-model"></a>規則によって変更内容がモデル内に反映される
1 つの要素から Visualization and Modeling SDK (VMSDK) の間の変更を伝達するストア ルールを作成することができます。 ストア内の任意の要素を変更する場合は、ルールは、通常、最も外側のトランザクションがコミットされたときに実行される予定です。 要素の追加や削除などのイベントのさまざまな種類のルールの種類があります。 ルールは、特定の種類の要素、図形、またはダイアグラムをアタッチできます。 多くの組み込み機能がルールによって定義されます。 など、規則では、モデルが変更されたときに、ダイアグラムが更新されることを確認します。 独自のルールを追加することで、ドメイン固有言語をカスタマイズできます。

 ストアの規則は、プロパティをモデル要素、リレーションシップ、図形またはコネクタ、およびそのドメインに変更には、ストア内の変更の反映に特に便利です。 ルールは、ユーザーが元に戻す/やり直しコマンドを呼び出したときに実行されません。 代わりに、トランザクション マネージャーにより、ストアの内容が正しい状態に復元されることを確認します。 ストアの外部リソースへの変更を反映する場合は、イベントの格納を使用します。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。

 たとえば、ユーザー (またはコード) は、型 ExampleDomainClass の新しい要素を作成するたびに、モデルの別の部分に、別の型の別の要素が作成されるかを指定するとします。 AddRule を記述して ExampleDomainClass に関連付けます。 その他の要素を作成するルールでコードを記述します。

```csharp
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

    // Code here propagates change as required - for example:
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
>  ルールのコードは、ストア内の要素のみの状態を変更する必要があります。つまり、ルールでは、モデル要素、リレーションシップ、図形、コネクタ、図、またはそれらのプロパティのみを変更する必要があります。 ストアの外部リソースへの変更を反映する場合は、イベントの格納を定義します。 詳細については、次を参照してください[イベント ハンドラー反映されるまで変更 Outside the モデル。](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>規則を定義するには

1.  クラスが接頭辞としてルールを定義、`RuleOn`属性。 属性は、ドメイン クラス、リレーションシップ、または図の要素のいずれかのルールを関連付けます。 ルールは、このクラスは、抽象にすることがありますの各インスタンスに適用されます。

2.  によって返されるセットに追加して、ルールを登録`GetCustomDomainModelTypes()`ドメイン モデル クラス。

3.  ルールの抽象クラスのいずれかのルール クラスを派生し、実行メソッドのコードを記述します。

 次のセクションでは、これらの手順の詳細について説明します。

### <a name="to-define-a-rule-on-a-domain-class"></a>ドメイン クラスの規則を定義するには

-   カスタム コード ファイルでクラスを定義し、プレフィックス、<xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>属性。

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   最初のパラメーターでサブジェクトの種類のドメイン クラス、ドメイン リレーションシップ、図形、コネクタ、またはダイアグラムを使用できます。 通常、ドメイン クラスとリレーションシップにルールを適用します。

     `FireTime`通常`TopLevelCommit`します。 これにより、トランザクションのすべての主な変更が行われた後にのみ、ルールが実行されます。 選択肢は次のインラインで、変更後すぐにルールを実行します。LocalCommit で、(これは、最も外側できない可能性があります)、現在のトランザクションの最後にルールを実行します。 そのキューで順序付けに影響するルールの優先順位を設定することもできますが、これは必要とする結果を実現するための信頼性の低いメソッド。

-   抽象クラスは、サブジェクトの種類として指定できます。

-   ルールは、サブジェクト クラスのすべてのインスタンスに適用されます。

-   既定値`FireTime`TimeToFire.TopLevelCommit です。 これにより、最も外側のトランザクションがコミットされた場合に実行されるルールです。 別の方法では、TimeToFire.Inline です。 これにより、トリガー起動イベント後すぐに実行されるルールです。

### <a name="to-register-the-rule"></a>ルールを登録するには

-   によって返される型の一覧に、ルール クラスを追加`GetCustomDomainModelTypes`ドメイン モデルで。

    ```csharp
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

-   ドメイン モデル クラスの名前の確信できない場合は、ファイルを調べる**Dsl\GeneratedCode\DomainModel.cs**

-   このコードを DSL プロジェクト内のカスタム コード ファイルに記述します。

### <a name="to-write-the-code-of-the-rule"></a>ルールのコードを記述するには

-   ルール クラスを次の基本クラスのいずれかから派生します。

    |基底クラス|トリガー|
    |----------------|-------------|
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|要素、リンク、または図形が追加されます。<br /><br /> これを使用して、新しい要素だけでなく、新しいリレーションシップを検出します。|
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|ドメイン プロパティの値を変更します。 このメソッドの引数は、新旧の値を提供します。<br /><br /> 図形は、このルールがトリガーされたときに、組み込み`AbsoluteBounds`プロパティの変更、図形が移動された場合。<br /><br /> 多くの場合、オーバーライドする方が便利です`OnValueChanged`または`OnValueChanging`プロパティ ハンドラーでします。 変更の前後にすぐに、これらのメソッドは呼び出されます。 これに対し、ルールは、トランザクションの最後に通常実行されます。 詳細については、次を参照してください。[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)します。 **注:** のリンクを作成または削除されたときは、このルールはトリガーされません。 代わりに、書き込み、`AddRule`と`DeleteRule`ドメイン リレーションシップ。|
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|要素またはリンクが削除しようとトリガーされます。 ModelElement.IsDeleting プロパティは、トランザクションが終了するまでは。|
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|要素またはリンクが削除されたときに実行されます。 その他のすべてのルールが実行されたら、DeletingRules を含むルールが実行されます。 ModelElement.IsDeleting が false になり、ModelElement.IsDeleted は true。 後続の元に戻すには、要素は、実際に削除されませんをメモリからが Store.ElementDirectory から削除されます。|
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|要素は、別に 1 つのストアのパーティションから移動されます。<br /><br /> (図形の位置をグラフィカルにこの関係はしないことに注意してください)。|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|このルールは、ドメイン リレーションシップにのみ適用されます。 リンクの両端をモデル要素を明示的に割り当てた場合、その関数がトリガーされます。|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|要素またはリンクの順序が変更のリンク、MoveBefore または MoveToIndex メソッドを使用するときにトリガーされます。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|トランザクションの作成時に実行します。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|トランザクションがコミットされるときに実行します。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|トランザクションがロールバックするときに実行されます。|

-   各クラスには、オーバーライドするメソッドがあります。 型`override`で検出するクラス。 このメソッドのパラメーターは、変更する要素を識別します。

 ルールについては、次の点に注意してください。

1.  トランザクションで変更のセットには、多くのルールをトリガー可能性があります。 通常、ルールは、最も外側のトランザクションがコミットされたときに実行されます。 不特定の順序で実行されます。

2.  ルールは、トランザクション内で常に実行されます。 そのため、変更を加えるには新しいトランザクションを作成することはありません。

3.  トランザクションがロールバックされるとき、または元に戻す/やり直し操作を実行すると、ルールは実行されません。 これらの操作は、以前の状態のストアのすべての内容をリセットします。 そのため、ルールには、ストアの外部の状態が変更された場合、可能性があります保持されません synchronism をストアとのコンテンツ。 を、ストア外の状態を更新するには、イベントを使用することをお勧めします。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)します。

4.  モデルがファイルから読み込まれるときに、いくつかのルールが実行されます。 読み込みまたは保存が進行中かどうかを調べるには`store.TransactionManager.CurrentTransaction.IsSerializing`します。

5.  ルールのコードでは、複数のルールのトリガーを作成する場合、起動リストの末尾に追加され、トランザクションが完了する前に実行されます。 DeletedRules は、その他のすべてのルールの後に実行されます。 1 つのルールは、変更ごとに 1 回のトランザクションで何度もを実行できます。

6.  内の情報を格納する、規則との情報を渡すため、`TransactionContext`します。 これは、トランザクション中に保持されている辞書だけです。 トランザクションが終了すると、破棄されます。 各ルールのイベント引数は、それへのアクセスを提供します。 ルールが予測可能な順序でない実行されることに注意してください。

7.  その他の代替手段を検討した後の規則を使用します。 たとえば、値が変更されたときにプロパティを更新する場合は、計算されるプロパティを使用して検討してください。 サイズまたは図形の場所を制限する場合は、使用、`BoundsRule`します。 プロパティ値の変更に応答する場合は、追加、`OnValueChanged`プロパティ ハンドラー。 詳細については、次を参照してください。[への対応および変更の反映](../modeling/responding-to-and-propagating-changes.md)します。

## <a name="example"></a>例
 次の例は、2 つの要素をリンクするドメイン リレーションシップがインスタンス化されるときに、プロパティを更新します。 このルールがだけでなくユーザーを作成とリンクを図もプログラム コードのリンクを作成する場合にトリガーされます。

 この例をテストするには、Task Flow ソリューション テンプレートを使用して DSL を作成し、Dsl プロジェクト内のファイルに次のコードを挿入します。 ビルド、ソリューションを実行し、デバッグ プロジェクトでサンプル ファイルを開きます。 コメントのシェイプとフロー要素間には、コメントのリンクを描画します。 コメント内のテキストは、レポートに接続している最も新しい要素を変更します。

 実際には、すべて AddRule 用、DeleteRule に記述した通常します。

```csharp
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

## <a name="see-also"></a>関連項目

- [イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)
- [BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)