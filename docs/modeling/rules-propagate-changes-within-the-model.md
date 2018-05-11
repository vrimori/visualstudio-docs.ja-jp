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
ms.openlocfilehash: 7b97151ba98a4d854802d96205aefa59fbbdbfac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>規則によって変更内容がモデル内に反映される
別の視覚化およびモデリング SDK (VMSDK) で 1 つの要素から変更を伝達するストア ルールを作成することができます。 変更された場合、ストア内の要素、ルールは、最も外側のトランザクションがコミットされるときに通常は、実行される予定です。 さまざまな種類の要素を追加または削除するなどのイベントのさまざまな種類のルールがあります。 ルールは、特定の種類の要素、図形、またはダイアグラムをアタッチできます。 多くの組み込み機能がルールによって定義されます。 など、ルールでは、モデルが変更されたときに、ダイアグラムが更新されることを確認します。 独自の規則を追加することで、ドメイン固有言語をカスタマイズできます。

 ストアの規則は、プロパティをモデル要素をリレーションシップ、図形またはコネクタ、およびそのドメインに変更は、-、ストア内の変更を反映するのに特に役立ちます。 ルールは、ユーザーが元に戻す/やり直しのコマンドを呼び出したときに実行されません。 代わりに、トランザクション マネージャーは、ストアの内容が正しい状態に復元されたことを確認します。 ストアの外部リソースへの変更を反映する場合は、イベントの格納を使用します。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

 たとえば、ユーザー (またはコード) は、型 ExampleDomainClass の新しい要素を作成するときに別の型の他の要素が作成されるモデルの別の部分を指定するとします。 AddRule を記述して ExampleDomainClass に関連付けます。 追加の要素を作成するルールにコードを記述します。

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
>  ルールのコードは、ストア内の要素のみの状態を変更する必要があります。つまり、ルールでは、モデル要素をリレーションシップ、図形、コネクタ、図、またはそれらのプロパティのみを変更する必要があります。 ストアの外部リソースへの変更を反映する場合は、保存のイベントを定義します。 詳細については、次を参照してください[イベント ハンドラー反映されるまで変更 Outside the モデル。](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>ルールを定義するには

1.  クラスが付いて、ルールを定義、`RuleOn`属性。 属性は、ドメイン クラス、リレーションシップ、またはダイアグラム要素のいずれかのルールを関連付けます。 ルールは、このクラスは、抽象にすることがありますのすべてのインスタンスに適用されます。

2.  によって返されるセットに追加して、ルールを登録`GetCustomDomainModelTypes()`ドメイン モデル クラスのです。

3.  抽象の規則クラスのいずれかのルール クラスを派生し、実行メソッドのコードを記述します。

 次のセクションでは、これらの手順の詳細について説明します。

### <a name="to-define-a-rule-on-a-domain-class"></a>ドメイン クラスにルールを定義するには

-   カスタム コード ファイルでクラスを定義し、プレフィックス、<xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>属性。

    ```
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

-   最初のパラメーターでサブジェクトの種類には、ドメイン クラス、ドメインの関係、図形、コネクタまたはダイアグラムを指定できます。 通常、ドメイン クラスとのリレーションシップにルールを適用します。

     `FireTime`は通常`TopLevelCommit`です。 これにより、トランザクションのすべての主な変更が加えられた後にのみ、ルールが実行されます。 選択肢は次のインラインで変更後すぐに、ルールを実行します。および LocalCommit で、(最も外側できない可能性があります) を現在のトランザクションの最後に規則を実行します。 キューの順序に影響するルールの優先順位を設定することもできますが、これは必要とする結果を実現するための信頼性の低いメソッド。

-   抽象クラスは、サブジェクトの種類として指定できます。

-   ルールは、サブジェクト クラスのすべてのインスタンスに適用されます。

-   既定値`FireTime`TimeToFire.TopLevelCommit がします。 これにより、最も外側のトランザクションがコミットされるときに実行されるルールです。 代わりには、TimeToFire.Inline です。 これにより、トリガー起動イベントの直後に実行されるルールです。

### <a name="to-register-the-rule"></a>ルールを登録するには

-   ルール クラスをによって返される型の一覧に追加`GetCustomDomainModelTypes`ドメイン モデルで。

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

-   ドメイン モデル クラスの名前のことを確認していない場合は、ファイル内で検索**Dsl\GeneratedCode\DomainModel.cs**

-   DSL プロジェクトでカスタム コード ファイルでこのコードを記述します。

### <a name="to-write-the-code-of-the-rule"></a>ルールのコードを記述するには

-   次の基本クラスのいずれかのルール クラスを派生します。

    |基底クラス|トリガー|
    |----------------|-------------|
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|要素、リンク、または図形が追加されます。<br /><br /> これを使用して、新しい要素だけでなく、新しいリレーションシップを検出します。|
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|ドメイン プロパティの値を変更します。 このメソッドの引数は、新旧の値を提供します。<br /><br /> 図形は、このルールがトリガーされたときに、組み込み`AbsoluteBounds`プロパティが変更された、図形が移動された場合。<br /><br /> 多くの場合、オーバーライドする方が便利です`OnValueChanged`または`OnValueChanging`プロパティ ハンドラーでします。 これらのメソッドは、直前と直後に、変更と呼ばれます。 これに対し、通常、ルールが、トランザクションの最後に実行します。 詳細については、次を参照してください。[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)です。 **注:** のリンクを作成または削除されたときに、このルールはトリガーされません。 代わりに、書き込み、`AddRule`と`DeleteRule`ドメイン リレーションシップです。|
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|要素またはリンクが削除されようとしてがトリガーされます。 ModelElement.IsDeleting プロパティは、トランザクションが終了するまでは true です。|
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|要素またはリンクが削除されたときに実行されます。 その他のすべてのルールの実行後、DeletingRules を含め、ルールが実行されます。 ModelElement.IsDeleting が false になり、ModelElement.IsDeleted は true です。 後続の元に戻すには、要素は、実際に削除されませんをメモリからが Store.ElementDirectory から削除されます。|
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|要素は、別のストアが 1 つのパーティションから移動されます。<br /><br /> (図形のグラフ上の位置にこの関連しないことに注意してください)。|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|このルールは、ドメイン リレーションシップにのみ適用されます。 リンクの両端をモデル要素を明示的に割り当てる場合にトリガーされます。|
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|要素の間のリンクの順序が変更リンク MoveBefore または MoveToIndex メソッドを使用すると発生します。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|トランザクションの作成時に実行します。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|トランザクションがコミットされるときに実行します。|
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|トランザクションをロールバックするときに実行します。|

-   各クラスには、オーバーライドするメソッドがあります。 型`override`検出には、クラスにします。 このメソッドのパラメーターは、変更する要素を識別します。

 規則に関する次の点に注意してください。

1.  一連の変更をトランザクションには、多数のルールをトリガー可能性があります。 通常、ルールは、最も外側のトランザクションがコミットされるときに実行されます。 不特定の順序で実行されます。

2.  ルールは常に、トランザクションの内部実行します。 そのため、変更を加える新しいトランザクションを作成するはありません。

3.  トランザクションがロールバックされたときに、または元に戻す/やり直しの操作が実行されたルールは実行されません。 これらの操作は、以前の状態ストアのすべてのコンテンツをリセットします。 そのため、ルールは、ストアの外部の状態を変更する場合に可能性があります保持しない synchronism をストアとのコンテンツ。 ストア以外の状態を更新するには、イベントを使用することをお勧めします。 詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

4.  一部のルールは、ファイルからモデルを読み込むときに実行されます。 読み込みまたは保存が進行中かどうかを確認するに`store.TransactionManager.CurrentTransaction.IsSerializing`です。

5.  ルールのコードでは、複数のルールのトリガーを作成する場合、起動リストの末尾に追加され、トランザクションが完了する前に実行されます。 DeletedRules は、その他のすべてのルールの後に実行されます。 1 つのルールは、各変更につき 1 回のトランザクションで何度もを実行できます。

6.  ルールとの情報を渡すで情報を格納することができます、`TransactionContext`です。 これは、トランザクション中に保持されているディクショナリだけです。 トランザクションの終了時に、破棄されます。 各ルールでイベント引数へのアクセスを提供します。 ルールが、予測可能な順序でない実行されることに注意してください。

7.  その他のオルタナティブを考慮した後の規則を使用します。 値が変更されたときにプロパティを更新する場合は、たとえば、計算されるプロパティを使用します。 サイズや図形の場所を制限する場合は、使用、`BoundsRule`です。 プロパティ値の変更に応答する場合は、追加、`OnValueChanged`プロパティ ハンドラー。 詳細については、次を参照してください。[への応答と変更を反映する](../modeling/responding-to-and-propagating-changes.md)です。

## <a name="example"></a>例
 次の例は、2 つの要素をリンクするドメインの関係がインスタンス化されるときにプロパティを更新します。 ルールがトリガーされますだけでなく、ユーザーのリンクを作成、ダイアグラムにもプログラム コードのリンクを作成する場合。

 この例をテストするには、テンプレートを使用して、タスク フロー ソリューション、DSL を作成し、Dsl プロジェクト内のファイルに次のコードを挿入します。 ビルドし、ソリューションを実行し、デバッグ プロジェクトでサンプル ファイルを開きます。 コメントの図形とフロー要素間にコメント リンクを描画します。 コメント内のテキストは、レポートに接続されている最新の要素を変更します。

 実際には、通常すべて AddRule の DeleteRule を記述するとします。

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

## <a name="see-also"></a>関連項目

- [イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)
- [BoundsRules によってシェイプの位置とサイズが制限される](../modeling/boundsrules-constrain-shape-location-and-size.md)