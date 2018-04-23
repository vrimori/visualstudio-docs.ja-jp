---
title: ドメイン固有言語における検証
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 7a196bd384a047328680a140232267b04bcb8f54
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
---
# <a name="validation-in-a-domain-specific-language"></a>ドメイン固有言語における検証
ドメイン固有言語 (DSL) の作成者は、検証制約を定義して、ユーザーが作成したモデルが意味を持つことを確認できます。 たとえば、DSL でユーザーが人々とその先祖の家系図を描くことができる場合、子の誕生日が親の誕生日よりも後であることを確認する制約を作成できます。

 モデルを保存すると、開かれたとき、およびユーザーが明示的に実行するときに実行する検証制約があることができます、**検証**メニュー コマンド。 検証をプログラム制御の下で実行することもできます。 たとえば、プロパティ値またはリレーションシップの変更に応じて検証を実行できます。

 検証は、テキスト テンプレートまたはユーザーのモデルを処理するその他のツールを作成する場合に特に重要です。 検証により、そうしたツールが仮定する事前条件をモデルが満たすことが保証されます。

> [!WARNING]
>  検証制約は、拡張機能メニュー コマンドおよびジェスチャ ハンドラーとともに、DSL の別個の拡張機能内で定義することもできます。 ユーザーは DSL に加えて、こうした拡張機能を選択的にインストールできます。 詳細については、次を参照してください。 [MEF を使用して、DSL、拡張](../modeling/extend-your-dsl-by-using-mef.md)です。

## <a name="running-validation"></a>検証の実行
 ユーザーがモデル、つまりドメイン固有言語のインスタンスを編集しているとき、次の操作により検証を実行できます。

-   ダイアグラムを右クリックし **すべて検証**です。

-   選択、DSL のエクスプ ローラーの最上位ノードを右クリックして**すべての検証**

-   モデルを保存します。

-   モデルを開きます。

-   さらに、たとえばメニュー コマンドの一部として、または変更に応じて検証を実行するプログラム コードを作成できます。

 検証エラーが表示されます、**エラー一覧**ウィンドウです。 ユーザーはエラー メッセージをダブルクリックして、エラーの原因であるモデル要素を選択できます。

## <a name="defining-validation-constraints"></a>検証制約の定義
 DSL のドメイン クラスまたはリレーションシップに検証メソッドを追加することにより、検証制約を定義します。 ユーザーまたはプログラム制御のいずれかにより検証が実行されると、検証メソッドの一部または全部が実行されます。 各メソッドはそのクラスの各インスタンスに適用され、各クラスにはいくつかの検証メソッドを含めることができます。

 各検証メソッドは発見したすべてのエラーを報告します。

> [!NOTE]
>  検証メソッドはエラーを報告しますが、モデルを変更しません。 場合は、調整または特定の変更を防ぐため、参照してください[検証に代わる方法](#alternatives)です。

#### <a name="to-define-a-validation-constraint"></a>検証制約を定義するには

1.  検証を有効にする、 **Editor\Validation**ノード。

    1.  開いている**Dsl\DslDefinition.dsl**です。

    2.  DSL のエクスプ ローラーで、展開、**エディター**ノード**検証**です。

    3.  [プロパティ] ウィンドウで、設定、**を使用して**プロパティを`true`です。 これらのプロパティをすべて設定すると利便性が最高になります。

    4.  をクリックして**すべてのテンプレートの変換**ソリューション エクスプ ローラーのツールバー。

2.  1 つ以上のドメイン クラスまたはドメイン リレーションシップに対して部分クラス定義を作成します。 新しいコード ファイル内でこれらの定義を記述、 **Dsl**プロジェクト。

3.  各クラスのプレフィックスとして次の属性を使用します。

    ```csharp
    [ValidationState(ValidationState.Enabled)]
    ```

    -   既定では、この属性により、派生したクラスの検証も有効になります。 特定の派生クラスについて検証を無効にする場合は、`ValidationState.Disabled` を使用できます。

4.  検証メソッドをクラスに追加します。 各検証メソッドには任意の名前を付けられますが、型 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext> のパラメーターは 1 つです。

     プレフィックスとして 1 つ以上の `ValidationMethod` 属性を使用する必要があります。

    ```csharp
    [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
    ```

     ValidationCategories はメソッドが実行されるタイミングを指定します。

 次に例を示します。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 このコードについては次の点に注意してください。

-   検証メソッドをドメイン クラスまたはドメイン リレーションシップに追加できます。 これらの型コードは、 **Dsl\Generated Code\Domain\*.cs**です。

-   各検証メソッドはそのクラスおよびサブクラスのすべてのインスタンスに適用されます。 ドメイン リレーションシップの場合、各インスタンスは 2 つのモデル要素間のリンクです。

-   検証メソッドは指定された順序で適用されず、各メソッドは予測可能な順序でそのクラスのインスタンスに適用されません。

-   通常、検証メソッドでストア コンテンツを更新するのは、一貫性のない結果を生じる可能性があるため、不適切な処理です。 代わりに、`context.LogError`、`LogWarning`、または `LogInfo` を呼び出すことにより、メソッドはすべてのエラーを報告する必要があります。

-   LogError 呼び出しでは、ユーザーがエラー メッセージをダブルクリックしたときに選択される、モデル要素またはリレーションシップ リンクの一覧を指定できます。

-   プログラム コードでモデルを読み取る方法については、次を参照してください。[を移動すると、プログラム コードでモデルを更新する](../modeling/navigating-and-updating-a-model-in-program-code.md)です。

 例は次のドメイン モデルに適用されます。 ParentsHaveChildren リレーションシップは Child および Parent という名前のロールを含みます。

 ![DSL 定義ダイアグラム&#45;ファミリ ツリー モデル](../modeling/media/familyt_person.png "FamilyT_Person")

## <a name="validation-categories"></a>検証カテゴリ
 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> 属性で、検証メソッドをいつ実行するかを指定します。

|カテゴリ|実行|
|--------------|---------------|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ユーザーが検証メニュー コマンドを呼び出すとき。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|モデル ファイルが開くとき。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ファイルが保存されるとき。 検証エラーがある場合、ユーザーは保存操作を取り消すことができます。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ファイルが保存されるとき。 このカテゴリでメソッドからのエラーがある場合、ユーザーはファイルを再度開くことができない可能性があることを警告されます。<br /><br /> このカテゴリは、読み込みエラーを引き起こす可能性がある、複製された名前または ID、またはその他の条件をテストする検証メソッドに使用します。|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ValidateCustom メソッドが呼び出されるとき。 このカテゴリの検証はプログラム コードからのみ呼び出すことができます。<br /><br /> 詳細については、次を参照してください。[カスタム検証カテゴリ](#custom)です。|

## <a name="where-to-place-validation-methods"></a>検証メソッドを配置する場所
 多くの場合、異なる型に 1 つの検証メソッドを配置することで、同じ効果を得ることができます。 たとえば、次のように、ParentsHaveChildren リレーションシップの代わりに Person クラスにメソッドを追加し、リンクを通して反復することができます。

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...

```

 **検証制約を集計します。** 予測可能な順序で検証を適用するには、モデルのルート要素など、オーナー クラスで単一の検証メソッドを定義します。 この手法により、複数のエラー報告を単一のメッセージに集約することもできます。

 欠点は組み合わされたメソッドが管理しにくいことと、すべての制約が同じ `ValidationCategories` を含む必要があることです。 したがって、可能であれば、各制約を別々のメソッドに維持することをお勧めします。

 **コンテキスト キャッシュ内の値を渡します。** コンテキスト パラメーターは任意の値を配置可能なディクショナリを持っています。 このディクショナリは検証が実行中保持されます。 たとえば、特定の検証メソッドはコンテキスト内でエラー カウントを維持し、繰り返しのメッセージでエラー ウィンドウがあふれることを防ぐために使用できます。 次に例を示します。

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }

```

## <a name="validation-of-multiplicities"></a>多重度の検証
 最小多重度をチェックするための検証メソッドは DSL 用に自動生成されます。 コードを記述する**Dsl\Generated Code\MultiplicityValidation.cs**です。 これらのメソッドでの検証を有効にすると有効になります、 **Editor\Validation** DSL のエクスプ ローラーでノード。

 ドメイン リレーションシップのロールの多重度を 1..* または 1..1 に設定し、ユーザーがこのリレーションシップのリンクを作成しない場合、検証エラー メッセージが表示されます。

 たとえば、DSL がある場合クラスの人と町、およびリレーションシップを持つリレーションシップ PersonLivesInTown **1..\***町ロールにすると、町を持たないユーザーごとに、エラー メッセージが表示されます。

## <a name="running-validation-from-program-code"></a>プログラム コードからの検証の実行
 ValidationController をアクセスまたは作成することにより検証を実行できます。 エラー、エラー ウィンドウにユーザーに表示する場合は、ダイアグラムの DocData に関連付けられている ValidationController を使用します。 たとえば、メニュー コマンドを作成する場合、コマンド セット クラスで `CurrentDocData.ValidationController` を使用できます。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...

```

 詳細については、次を参照してください。[する方法: ショートカット メニューにコマンドを追加](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)です。

 別個の検証コントローラーを作成して、独自にエラーを管理することもできます。 次に例を示します。

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}

```

## <a name="running-validation-when-a-change-occurs"></a>変更発生時の検証実行
 モデルが無効になった直後にユーザーへの警告を表示する場合、検証を実行するストア イベントを定義できます。 ストアのイベントの詳細については、次を参照してください。[イベント ハンドラー反映されるまで変更 Outside the モデル](../modeling/event-handlers-propagate-changes-outside-the-model.md)です。

 検証コードだけでなく、カスタム コード ファイルを追加、 **DslPackage**プロジェクト、コンテンツは次の例に似ています。 このコードはドキュメントにアタッチされる `ValidationController` を使用します。 このコントローラーは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] エラー一覧に検証エラーを表示します。

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}

```

 ハンドラーはリンクまたは要素に影響する、元に戻す操作またはやり直し操作の後でも呼び出されます。

##  <a name="custom"></a> カスタム検証カテゴリ
 「メニュー」や「開く」といった標準の検証カテゴリに加えて、独自のカテゴリを定義できます。 これらのカテゴリをプログラム コードから呼び出すことができます。 ユーザーはそれらを直接呼び出すことができません。

 カスタム カテゴリの一般的な使用法は、モデルが特定のツールの事前条件を満たすかどうかをテストするカテゴリを定義することです。

 特定のカテゴリに検証メソッドを追加するには、プレフィックスとして次のような属性を使用します。

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}

```

> [!NOTE]
>  メソッドのプレフィックスには任意の数の `[ValidationMethod()]` 属性を使用できます。 メソッドをカスタム カテゴリと標準カテゴリの両方に追加できます。

 カスタム検証を呼び出すには次のようにします。

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

##  <a name="alternatives"></a> 検証に代わる方法
 検証制約はエラーを報告しますが、モデルを変更しません。 代わりに、モデルが無効になることを防ぐ場合、他の手法を使用できます。

 ただし、これらの手法は推奨されません。 通常、無効なモデルの修正方法をユーザーに決めてもらう方が適切です。

 **モデルを有効に復元する変更を調整します。** たとえば、ユーザーが許容される最大値を超えてプロパティを設定した場合、プロパティを最大値にリセットできます。 そのためには、規則を定義します。 詳細については、次を参照してください。[ルール反映されるまで変更内で、モデル](../modeling/rules-propagate-changes-within-the-model.md)です。

 **トランザクションをロールバックして無効な変更が試行されるとします。** このため、ルールを定義することもでしたが、場合によってはプロパティ ハンドラーをオーバーライドすることが**OnValueChanging()**、またはメソッドをオーバーライドなど`OnDeleted().`トランザクションをロールバックするには使用`this.Store.TransactionManager.CurrentTransaction.Rollback().`の詳細についてを参照してください[ドメイン プロパティ値変更ハンドラー](../modeling/domain-property-value-change-handlers.md)です。

> [!WARNING]
> 変更が調整またはロールバックされたことをユーザーが認識できるようにします。 たとえば、`System.Windows.Forms.MessageBox.Show("message").` を使用します。

## <a name="see-also"></a>関連項目

- [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [イベント ハンドラーによって変更内容がモデル外に反映される](../modeling/event-handlers-propagate-changes-outside-the-model.md)