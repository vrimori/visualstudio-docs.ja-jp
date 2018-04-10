---
title: MEF を使用して、DSL を拡張 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 735de60d18bc5cbca7dc2ba509372d81622038be
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="extend-your-dsl-by-using-mef"></a>MEF による DSL の拡張
Managed Extensibility Framework (MEF) を使用して、ドメイン固有言語 (DSL) を拡張することができます。 か、他の開発者は、DSL 定義とプログラム コードを変更することがなく、DSL の拡張機能を記述することができます。 このような拡張機能には、メニュー コマンド、ドラッグ アンド ドロップ ハンドラー、および検証が含まれます。 ユーザーは、DSL をインストールして、その拡張機能を必要に応じてインストールを可能になります。  
  
 さらに、DSL の MEF を有効にするとだということ、DSL の機能の一部を記述を簡単に行う場合でも、すべて DSL と共に構築されます。  
  
 MEF の詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)です。  
  
### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>DSL MEF には拡張を有効にするには  
  
1.  という名前の新しいフォルダーを作成する**MefExtension**内、 **DslPackage**プロジェクト。 次のファイルを追加します。  
  
     ファイル名: `CommandExtensionVSCT.tt`  
  
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
  
     このファイルを追加すると、必要があります有効にした場合の検証、DSL のスイッチの少なくとも 1 つを使用して**EditorValidation** DSL のエクスプ ローラーでします。  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>  
    ```  
  
     ファイル名: `PackageExtensionEnablement.tt`  
  
    ```  
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>  
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>  
    ```  
  
2.  という名前の新しいフォルダーを作成する**MefExtension**内、 **Dsl**プロジェクト。 次のファイルを追加します。  
  
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
  
3.  名前は既存のファイルに次の行を追加**DslPackage\Commands.vsct**:  
  
    ```  
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>  
    ```  
  
     既存の後に、行を挿入`<Include>`ディレクティブです。  
  
4.  `Open DslDefinition.dsl.`  
  
5.  DSL のエクスプ ローラーで選択**Editor\Validation**です。  
  
6.  [プロパティ] ウィンドウで、という名前の少なくとも 1 つのプロパティのことを確認してください**を使用しています.**は`true`します。  
  
7.  ソリューション エクスプ ローラー ツールバーで **すべてのテンプレートの変換**です。  
  
     下に追加するファイルの各関連会社のファイルが表示されます。  
  
8.  ビルドおよびがまだ動作していることを確認するようにソリューションを実行します。  
  
 DSL は、MEF-有効になっているようになりました。 MEF 拡張機能としては、メニュー コマンド、ジェスチャ ハンドラー、および検証制約を作成できます。 その他のカスタム コードと共に DSL ソリューションでは、これらの拡張機能を記述できます。 さらに、するおよび他の開発者は、書き込み個別[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]DSL を拡張します。  
  
## <a name="creating-an-extension-for-a-mef-enabled-dsl"></a>MEF が有効な DSL の拡張機能の作成  
 自分または他のユーザーによって作成された MEF が有効な DSL へのアクセスがあれば、その拡張機能を記述できます。 メニュー コマンド、ジェスチャ ハンドラー、または検証制約を追加する拡張機能を使用できます。 これらの拡張機能を作成するには、使用する、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Extension (VSIX) ソリューションです。 このソリューションには 2 つの部分: コード アセンブリを作成するクラス ライブラリ プロジェクトとアセンブリをパッケージする VSIX プロジェクト。  
  
#### <a name="to-create-a-dsl-extension-vsix"></a>DSL 拡張機能の VSIX を作成するには  
  
1.  新しいクラス ライブラリ プロジェクトを作成します。 これを行うで、**新しいプロジェクト**ダイアログ ボックスで、 **Visual Basic**または**Visual c#**し、**クラス ライブラリ**です。  
  
2.  新しいクラス ライブラリ プロジェクトでは、DSL のアセンブリへの参照を追加します。  
  
    -   このアセンブリは通常で終わる名前を持つ"です。Dsl.dll"です。  
  
    -   DSL プロジェクトへのアクセスがある場合は場合、は、ディレクトリの下にあるアセンブリ ファイルを検索できる**Dsl\bin\\\***  
  
    -   DSL VSIX ファイルにアクセスする場合は、".zip"VSIX ファイルのファイル名拡張子を変更することによって、アセンブリを見つけることができます。 .Zip ファイルを圧縮解除できません。  
  
3.  次の .NET アセンブリへの参照を追加します。  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll  
  
    -   Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll  
  
    -   System.ComponentModel.Composition.dll  
  
    -   System.Windows.Forms.dll  
  
4.  同じソリューションで VSIX プロジェクトを作成します。 これを行うで、**新しいプロジェクト** ダイアログ ボックスで、展開**Visual Basic**または**Visual c#**、 をクリックして**機能拡張**をクリックして**VSIX プロジェクト**です。  
  
5.  ソリューション エクスプ ローラーで、VSIX プロジェクトを右クリックし、をクリックして**スタートアップ プロジェクトとして設定**です。  
  
6.  新しいプロジェクトで開きます**source.extension.vsixmanifest**です。  
  
7.  をクリックして**コンテンツを追加**です。 ダイアログ ボックスで、次のように設定します。**コンテンツ タイプ**に**MEF コンポーネント**、および**ソース プロジェクト**クラス ライブラリ プロジェクトにします。  
  
8.  DSL への参照を VSIX に追加します。  
  
    1.  **Source.extension.vsixmanifest**をクリックして**参照の追加**  
  
    2.  ダイアログ ボックスで、をクリックして**追加ペイロード**し、DSL の VSIX ファイルを見つけます。 VSIX ファイルがソリューションでは、DSL でビルドされた**DslPackage\bin\\\***です。  
  
         これにより、ユーザーは、同時に、DSL と拡張機能をインストールします。 ユーザーがまだインストールされて、DSL、拡張機能がインストールされます。  
  
9. 確認しの他のフィールドを更新**source.extension.vsixmanifest**です。 をクリックして**エディションの**ことを確認し、正しい[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]エディションが設定されます。  
  
10. クラス ライブラリ プロジェクトにコードを追加します。 次のセクションで例をガイドとして使用します。  
  
     コマンド、ジェスチャ、および検証クラスの任意の数を追加することができます。  
  
11. 拡張機能をテストするには、キーを押して**f5 キーを押して**です。 実験用インスタンスで[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を作成または DSL の例は、ファイルを開きます。  
  
## <a name="writing-mef-extensions-for-dsls"></a>Dsl の MEF 拡張機能の記述  
 DSL 拡張機能ソリューションの別のアセンブリのコード プロジェクトで拡張機能を記述できます。 DSL の一部として、コマンド、ジェスチャ、および検証コードを記述する便利な手段として DslPackage プロジェクトで、MEF を使用することもできます。  
  
### <a name="menu-commands"></a>メニュー コマンド  
 記述するには、メニュー コマンドを実装するクラスを定義する<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>、DSL、という名前で定義されている属性を持つクラスをプレフィックスと*YourDsl*`CommandExtension`です。 1 つ以上のメニュー コマンド クラスを記述することができます。  
  
 `QueryStatus()` ユーザーは、ダイアグラムを右クリックしたときに呼び出されます。 現在の選択範囲を検査し、設定か`command.Enabled`コマンドが適用可能なことを示すです。  
  
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
 ジェスチャ ハンドラーが内側または外側に、図に、どこからでもドラッグ オブジェクトが対処できる[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 次の例により、ユーザーは、図に、Windows エクスプ ローラーからファイルをドラッグできます。 ファイル名を含む要素を作成します。  
  
 他の DSL モデルおよび UML モデルからのドラッグが対処できるハンドラーを作成できます。 詳細については、次を参照してください。[する方法: ドラッグ アンド ドロップのハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)です。  
  
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
 検証メソッドがによってマークされて、 `ValidationExtension` 、DSL ともによって生成される属性<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute>です。 メソッドは、属性でマークされていない任意のクラスに表示できます。  
  
 詳細については、次を参照してください。[ドメイン固有言語で検証](../modeling/validation-in-a-domain-specific-language.md)です。  
  
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
 [Visual Studio 拡張機能の配布](../extensibility/shipping-visual-studio-extensions.md)   
 [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)   
 [方法: ドラッグ アンド ドロップのハンドラーを追加](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [ドメイン固有言語における検証](../modeling/validation-in-a-domain-specific-language.md)