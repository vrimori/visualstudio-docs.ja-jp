---
title: "MEF を使用して、DSL を拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e7be79a-53ab-4d79-863a-bef8d27839bd
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 9a730560e0f19c8e6e58ccc830a95541ae3c5d29
ms.lasthandoff: 02/22/2017

---
# <a name="extend-your-dsl-by-using-mef"></a>MEF による DSL の拡張
Managed Extensibility Framework (MEF) を使用して、ドメイン固有言語 (DSL) を拡張することができます。 か、他の開発者ができる、DSL の DSL 定義とプログラム コードを変更することがなく拡張機能を記述します。 このような拡張機能には、メニュー コマンド、ドラッグ アンド ドロップ ハンドラー、および検証が含まれます。 ユーザーは、DSL をインストールし、その拡張機能を必要に応じてインストールすることになります。  
  
 さらに、DSL で MEF を有効にするとなりますが簡単に、DSL の機能の一部を記述する場合でも、すべて DSL と共にビルドされます。  
  
 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)します。  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>MEF で拡張する DSL を有効にするには  
  
1.  という新しいフォルダーを作成**MefExtension**内、 **DslPackage**プロジェクトです。 次のファイルを追加します。  
  
     ファイル名:`CommandExtensionVSCT.tt`  
  
    > [!IMPORTANT]
    >  DslPackage\GeneratedCode\Constants.tt で定義されている GUID CommandSetId と同じにするには、このファイルで、GUID を設定します。  
  
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
  
     ファイル名:`CommandExtensionRegistrar.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>  
    ```  
  
     ファイル名:`ValidationExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>  
    ```  
  
     ファイル名:`ValidationExtensionRegistrar.tt`  
  
     このファイルを追加する必要があります有効にした場合検証 DSL 内におけるスイッチの少なくとも&1; つを使用して**EditorValidation** DSL エクスプ ローラーでします。  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
    ```  
  
     ファイル名:`PackageExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
    ```  
  
2.  という新しいフォルダーを作成**MefExtension**内、 **Dsl**プロジェクトです。 次のファイルを追加します。  
  
     ファイル名:`DesignerExtensionMetaDataAttribute.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>  
    ```  
  
     ファイル名:`GestureExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>  
    ```  
  
     ファイル名:`GestureExtensionController.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="Dsl\GestureExtensionController.tt" #>  
    ```  
  
3.  という名前の既存のファイルに次の行を追加**\commands.vsct**:  
  
    ```  
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
    ```  
  
     既存の後に、行挿入`<Include>`ディレクティブです。  
  
4.  `Open DslDefinition.dsl.`  
  
5.  DSL エクスプ ローラーで選択**発します**します。  
  
6.  [プロパティ] ウィンドウでプロパティの少なくとも&1; つという名前を確認します**を使用しています.** is `true`.  
  
7.  ソリューション エクスプ ローラー ツールバーで **すべてのテンプレートの変換**します。  
  
     下に追加したファイルの各関連会社のファイルが表示されます。  
  
8.  ビルドしてがまだ動作していることを確認するソリューションを実行します。  
  
 DSL は、MEF を有効にしたようになりました。 MEF の拡張機能としては、メニュー コマンド、ジェスチャ ハンドラー、および検証制約を作成できます。 その他のカスタム コードと共に、DSL ソリューションでは、これらの拡張機能を記述できます。 さらに、他の開発者かを記述できます別[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL を拡張する拡張機能です。  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>MEF が有効な DSL の拡張機能の作成  
 自分または他のユーザーによって作成された MEF が有効な DSL にアクセスできる場合は、その拡張機能を記述できます。 メニュー コマンド、ジェスチャ ハンドラー、または検証制約を追加する拡張機能を使用できます。 これらの拡張機能を作成するを使用する、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension (VSIX) ソリューションです。 このソリューションには&2; つの部分: コード アセンブリを作成するクラス ライブラリ プロジェクトおよびアセンブリをパッケージ化する VSIX プロジェクト。  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>DSL の拡張機能の VSIX を作成するには  
  
1.  新しいクラス ライブラリ プロジェクトを作成します。 そのためを**新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**または**Visual C# の場合**し、**クラス ライブラリ**します。  
  
2.  新しいクラス ライブラリ プロジェクトでは、DSL のアセンブリへの参照を追加します。  
  
    -   このアセンブリは通常で終わる名前を持つ"です。Dsl.dll"です。  
  
    -   DSL プロジェクトへのアクセスがある場合は、ディレクトリの下のアセンブリ ファイルを検索できます**Dsl\bin\\\***  
  
    -   DSL の VSIX ファイルにアクセスできる場合は、".zip"VSIX ファイルのファイル名拡張子を変更することでアセンブリを見つけることができます。 .Zip ファイルを圧縮解除します。  
  
3.  次の .NET アセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
    -   System.ComponentModel.Composition.dll  
  
    -   System.Windows.Forms.dll  
  
4.  同じソリューションで VSIX プロジェクトを作成します。 、そのために、**新しいプロジェクト** ダイアログ ボックスで、展開**Visual Basic**または**Visual c#**、 をクリックして**拡張**、し、 **VSIX プロジェクト**します。  
  
5.  ソリューション エクスプ ローラーで VSIX プロジェクトを右クリックし、をクリックし、**スタートアップ プロジェクトとして設定**します。  
  
6.  新しいプロジェクトを開く**source.extension.vsixmanifest**します。  
  
7.  クリックして**コンテンツを追加**します。 ダイアログ ボックスで、次のように設定します。**コンテンツ タイプ**に**MEF コンポーネント**、および**ソース プロジェクト**クラス ライブラリ プロジェクトにします。  
  
8.  DSL への参照を VSIX を追加します。  
  
    1.  **Source.extension.vsixmanifest**、クリックして**参照の追加**  
  
    2.  ダイアログ ボックスでクリックして**追加ペイロード**し、DSL の VSIX ファイルを見つけます。 VSIX ファイルは DSL ソリューションに組み込まれて**DslPackage\bin\\\***します。  
  
         これにより、ユーザーが同時に、DSL と拡張機能をインストールします。 ユーザーは既に、DSL をインストールして、拡張機能のみがインストールされます。  
  
9. 確認し、その他のフィールドを更新**source.extension.vsixmanifest**します。 をクリックして**エディションの**いることを確認し、正しい[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディションを設定します。  
  
10. コードをクラス ライブラリ プロジェクトに追加します。 次のセクションで例をガイドとして使用します。  
  
     任意の数のコマンド、ジェスチャ、および検証クラスを追加することができます。  
  
11. 拡張機能をテストするには、キーを押して**f5 キーを押して**します。 実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を作成または DSL の例は、ファイルを開きます。  
  
## <a name="writing-mef-extensions-for-dsls"></a>Dsl の MEF 拡張の書き込み  
 別の DSL の拡張機能ソリューションのアセンブリのコード プロジェクトでは、拡張機能を記述できます。 また、DSL の一部として、コマンド、ジェスチャ、および検証コードを記述する便利な方法として、DslPackage プロジェクト内 MEF を使用することができます。  
  
### <a name="menu-commands"></a>メニュー コマンド  
 メニュー コマンドを書き込むを実装するクラスを定義<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>を付けた状態で、DSL、という名前で定義されている属性を持つクラス*YourDsl*`CommandExtension`</xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> 。 1 つ以上のメニュー コマンド クラスを記述することができます。  
  
 `QueryStatus()`ダイアグラムを右クリックしたときに呼び出されます。 現在の選択範囲を検査し、設定か`command.Enabled`コマンドが適用されることを示します。  
  
```  
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
 ジェスチャ ハンドラーの内部または外部から任意の場所を図にドラッグするオブジェクトが対処できる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 次の例では、ユーザーがファイルを Windows エクスプ ローラーから図上へドラッグをできます。 ファイル名を格納している要素を作成します。  
  
 その他の DSL のモデルと UML モデルからドラッグが対処するハンドラーを作成できます。 詳細については、次を参照してください。[方法: ドラッグ アンド ドロップ ハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)します。  
  
```  
  
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
 検証メソッドがによってマークされて、 `ValidationExtension` <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>.</xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>もと、DSL によって生成される属性 このメソッドは、属性でマークされていない任意のクラスで表示できます。  
  
 詳細については、次を参照してください。[ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)します。  
  
```  
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
 [Visual Studio 拡張機能を配布](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)   
 [方法: ドラッグ アンド ドロップ ハンドラーを追加します。](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)
