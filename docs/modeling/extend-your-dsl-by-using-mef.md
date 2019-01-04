---
title: MEF による DSL の拡張
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 6e6c790677ea49ad784e7ff5d48326a1d5e216ad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53986168"
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF による DSL の拡張

Managed Extensibility Framework (MEF) を使用して、ドメイン固有言語 (DSL) を拡張できます。 または他の開発者は、DSL 定義とプログラム コードを変更することがなく、DSL の拡張機能を記述することがなります。 このような拡張機能には、メニュー コマンド、ドラッグ アンド ドロップ ハンドラー、および検証が含まれます。 ユーザーは、DSL をインストールし、その拡張機能を必要に応じてインストールすることになります。

さらに、DSL で MEF を有効にするとできます簡単に、DSL の機能の一部を記述する場合でも、すべて DSL と共に構築されます。

MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)します。

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>MEF で拡張する DSL を有効にするには

1.  という名前の新しいフォルダーを作成する**MefExtension**内で、 **DslPackage**プロジェクト。 次のファイルを追加します。

     ファイル名: `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > GUID を GUID CommandSetId DslPackage\GeneratedCode\Constants.tt で定義されているのと同じにするのには、このファイルの設定します。

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    ファイル名: `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    ファイル名: `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    ファイル名: `ValidationExtensionRegistrar.tt`

    このファイルに追加する場合、必要がありますで有効にする検証 DSL を少なくとも 1 つのスイッチを使用して**EditorValidation** DSL エクスプ ローラーでします。

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    ファイル名: `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2.  という名前の新しいフォルダーを作成する**MefExtension**内で、 **Dsl**プロジェクト。 次のファイルを追加します。

     ファイル名: `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    ファイル名: `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    ファイル名: `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3.  という名前の既存のファイルに次の行を追加**dslpackage \commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    既存の後の行を挿入`<Include>`ディレクティブ。

4.  開いている*DslDefinition.dsl*します。

5.  DSL エクスプ ローラーで選択**発します**します。

6.  [プロパティ] ウィンドウでプロパティの少なくとも 1 つという名前を確認します**使用**は`true`します。

7.  **ソリューション エクスプ ローラー**ツールバーで、をクリックして**すべてのテンプレートの変換**します。

     各追加したファイルの下にある関連会社のファイルが表示されます。

8.  ビルドおよびがまだ動作していることを確認するソリューションを実行します。

DSL は、MEF-有効になっているようになりました。 MEF 拡張機能としては、メニュー コマンド、ジェスチャ ハンドラー、および検証制約を作成できます。 その他のカスタム コードと共に、DSL ソリューションでは、これらの拡張機能を記述できます。 さらに、か、他の開発者は、DSL を拡張する別の Visual Studio 拡張機能を記述できます。

## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>MEF が有効な DSL の拡張機能の作成

自分または他のユーザーによって作成された MEF が有効な DSL へのアクセスがあれば、その拡張機能を記述できます。 メニュー コマンド、ジェスチャ ハンドラー、または検証制約を追加する拡張機能を使用できます。 これらの拡張機能を作成するには、Visual Studio の拡張機能 (VSIX) ソリューションを使用します。 ソリューションに 2 つの部分: クラス ライブラリ プロジェクト、コード アセンブリをビルドして、アセンブリをパッケージ化した VSIX プロジェクト。

#### <a name="to-create-a-dsl-extension-vsix"></a>DSL 拡張 VSIX を作成するには

1. 新しいクラス ライブラリ プロジェクトを作成します。 これを実行する、**新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**または**Visual c#** 選び**クラス ライブラリ**します。

2. 新しいクラス ライブラリ プロジェクトでは、DSL のアセンブリへの参照を追加します。

   - このアセンブリは通常で終わる名前を持つ"。Dsl.dll"。

   - DSL プロジェクトへのアクセスがある場合は、ディレクトリの下のアセンブリ ファイルを検索できます**Dsl\bin\\\\***

   - DSL の VSIX ファイルにアクセスする場合は、".zip"VSIX ファイルのファイル名拡張子を変更することでアセンブリを見つけることができます。 .Zip ファイルを圧縮解除します。

3. 次の .NET アセンブリへの参照を追加します。

   -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   -   System.ComponentModel.Composition.dll

   -   System.Windows.Forms.dll

4. 同じソリューションで VSIX プロジェクトを作成します。 これを実行する、**新しいプロジェクト** ダイアログ ボックスで、展開**Visual Basic**または**Visual c#**、 をクリックして**Extensibility**、しを選択します。**VSIX プロジェクト**します。

5. ソリューション エクスプ ローラーで VSIX プロジェクトを右クリックし をクリックし、**スタートアップ プロジェクトとして設定**します。

6. 新しいプロジェクトで開く**source.extension.vsixmanifest**します。

7. クリックして**コンテンツ追加**します。 ダイアログ ボックスで、次のように設定します。**コンテンツの種類**に**MEF コンポーネント**、および**ソース プロジェクト**クラス ライブラリ プロジェクトにします。

8. DSL への参照を VSIX に追加します。

   1. **Source.extension.vsixmanifest**、 をクリックして**参照の追加**

   2. ダイアログ ボックスで、次のようにクリックします。**追加ペイロード**し、DSL の VSIX ファイルを見つけます。 VSIX ファイルは、DSL ソリューション内で構築された * * DslPackage\bin\\\\* * *。

       これにより、ユーザーが同時に、DSL と拡張機能をインストールできます。 ユーザーが DSL をインストールしてある場合は、拡張機能がインストールされます。

9. 確認の他のフィールドを更新して**source.extension.vsixmanifest**します。 クリックして**エディションの**正しい Visual Studio のエディションを設定することを確認します。

10. コードをクラス ライブラリ プロジェクトに追加します。 次のセクションの例をガイドとして使用します。

     任意の数のコマンド、ジェスチャ、および検証クラスを追加することができます。

11. 拡張機能をテストするには、キーを押して**F5**します。 Visual Studio の実験用インスタンスを作成または DSL の例は、ファイルを開きます。

## <a name="writing-mef-extensions-for-dsls"></a>Dsl 用の MEF 拡張機能の記述

別の DSL 拡張機能ソリューションのアセンブリのコード プロジェクトでは、拡張機能を記述できます。 DSL の一部として、コマンド、ジェスチャ、および検証コードを記述する便利な方法として、DslPackage プロジェクト内の MEF を使用することもできます。

### <a name="menu-commands"></a>メニュー コマンド

メニュー コマンドを書き込むを実装するクラスを定義<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>という、DSL で定義されている属性を持つクラスをプレフィックスと*YourDsl*`CommandExtension`します。 1 つ以上のメニュー コマンド クラスを記述することができます。

`QueryStatus()` ダイアグラムを右クリックしたときに呼び出されます。 現在の選択範囲を検査し、設定する必要がありますが`command.Enabled`をコマンドが該当する場合を示します。

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>ジェスチャ ハンドラー

ジェスチャ ハンドラーは、内で任意の場所、または Visual Studio の外部からの図にドラッグしたオブジェクトを扱うことができます。 次の例は、Windows エクスプ ローラーから対象のファイルを図にドラッグできますを示しています。 ファイル名を格納している要素を作成します。

他の DSL モデルおよび UML モデルからの障壁に対処するためのハンドラーを記述することができます。 詳細については、「[方法 :ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)します。

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>検証制約

検証メソッドがによってマークされている、 `ValidationExtension` 、DSL ともによって生成される属性<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>します。 メソッドは、属性でマークされていないすべてのクラスで表示できます。

詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)です。

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>関連項目

- [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)
- [MEF (Managed Extensibility Framework)](/dotnet/framework/mef/index)
- [方法: ドラッグ アンド ドロップ ハンドラーを追加します。](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)
