---
title: モデリング図にメニュー コマンドを定義 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c211c37817ba996105d7496dc49e91db9fa9298e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809104"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>モデリング図にメニュー コマンドを定義する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio では、UML 図のショートカット メニューに追加のメニュー項目を定義できます。 図上の任意の要素のショートカット メニューに対して、メニュー コマンドを表示して有効にするかどうかを制御できます。また、ユーザーがメニュー項目を選択したときに実行されるコードを記述できます。 これらの拡張機能を[VSIX](http://go.microsoft.com/fwlink/?LinkId=160780)(Visual Studio Integration Extension) にパッケージ化し、他の Visual Studio ユーザーに配布できます。  

## <a name="requirements"></a>必要条件  
 「 [要件](../modeling/extend-uml-models-and-diagrams.md#Requirements)」を参照してください。  

 この機能をサポートする Visual Studio のバージョンを確認するには、「 [アーキテクチャ ツールとモデリング ツールのバージョン サポート](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)」を参照してください。  

## <a name="defining-the-menu-command"></a>メニュー コマンドの定義  
 UML デザイナーのメニュー コマンドを作成するには、コマンドの振る舞いを定義するクラスを作成し、そのクラスを Visual Studio Integration Extension (VSIX) に埋め込む必要があります。 VSIX は、コマンドをインストールできるコンテナーとして機能します。 メニュー コマンドを定義する方法は 2 つあります。  

-   **プロジェクト テンプレートを使用して、独自の VSIX にメニュー コマンドを作成します。** これはより簡単な方法です。 メニュー コマンドの他の種類の拡張機能 (検証拡張機能、カスタム ツールボックス項目、ジェスチャ ハンドラーなど) と組み合わせない場合は、この方法を使用します。  

-   **別のメニュー コマンドと VSIX プロジェクトを作成します。** 複数の種類の拡張機能を同じ VSIX に組み合わせる場合は、この方法を使用します。 たとえば、メニュー コマンドが特定の制約に従うモデルを必要とする場合は、そのモデルを検証メソッドとして同じ VSIX に埋め込むことができます。  

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>メニュー コマンドを独自の VSIX に作成するには  

1. **[新しいプロジェクト]** ダイアログ ボックスの **[モデリング プロジェクト]** で、 **[コマンド拡張機能]** をクリックします。  

2. 新しいプロジェクトで **.cs** ファイルを開き、 `CommandExtension` クラスを変更してコマンドを実装します。  

    詳細については、「 [メニュー コマンドの実装](#Implementing)」を参照してください。  

3. 新しいクラスを定義して、このプロジェクトに追加のコマンドを追加できます。  

4. F5 キーを押してメニュー コマンドをテストします。 詳細については、「 [メニュー コマンドの実行](#Executing)」を参照してください。  

5. メニュー コマンドを別のコンピューターでファイルをコピーしてインストール**bin\\\*\\\*.vsix**は、プロジェクトでビルドしました。 詳細については、「 [拡張機能のインストールとアンインストール](#Installing)」を参照してください。  

   次の手順も使用できます。  

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>メニュー コマンドを個々のクラス ライブラリ (DLL) プロジェクトに作成するには  

1. 新しい Visual Studio ソリューションまたは既存のソリューションにクラス ライブラリ プロジェクトを作成します。  

   1.  **[ファイル]** メニューで、 **[新規]**、 **[プロジェクト]** をクリックします。  

   2.  **[インストールされたテンプレート]** の **[Visual C#]** または **[Visual Basic]** をクリックします。 中央の列で、 **[クラス ライブラリ]** をクリックします。  

   3.  新しいソリューションを作成するか、既に開いている VSIX ソリューションにコンポーネントを追加するかを **[ソリューション]** に指定します。  

   4.  プロジェクトの名前と場所を設定し、[OK] をクリックします。  

2. 以下の参照をプロジェクトに追加します。  


   |                                                                                                    参照                                                                                                    |                                                                                                  実行できる操作                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)を使用してコンポーネントを定義する。                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        モデル要素のプロパティを読み取り、変更する。                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      モデル要素を生成する、図のシェイプを変更する。                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[バージョン]                                                                                  | モデル イベント ハンドラーを定義する。<br /><br /> モデルに対する一連の変更をカプセル化する。 詳細については、次を参照してください。[トランザクションを使用してモデルの更新をリンク UML](../modeling/link-uml-model-updates-by-using-transactions.md)します。 |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[バージョン]<br /><br /> (必須ではない)                                                             |                                                                                   ジェスチャ ハンドラーの追加の図要素にアクセスする。                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> レイヤー図上のコマンドにのみ必要。 詳細については、次を参照してください。[レイヤー図を拡張](../modeling/extend-layer-diagrams.md)します。 |                                                                                             レイヤー図上のコマンドを定義する。                                                                                              |


3. プロジェクトにクラス ファイルを追加し、その内容を次のコードに設定します。  

   > [!NOTE]
   >  名前空間、クラス名、および `Text` から返される値を必要に応じて変更してください。  
   >   
   >  複数のコマンドを定義する場合、それらのコマンドは、クラス名のアルファベット順でメニューに表示されます。  

   ```  
   using System.ComponentModel.Composition;     
   using System.Linq;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;  
   using Microsoft.VisualStudio.Uml.Classes;   
       // ADD other UML namespaces if required  

   namespace UMLmenu1 // CHANGE  
   {  
     // DELETE any of these attributes if the command  
     // should not appear in some types of diagram.  
     [ClassDesignerExtension]  
     [ActivityDesignerExtension]  
     [ComponentDesignerExtension]  
     [SequenceDesignerExtension]  
     [UseCaseDesignerExtension]   
     // [LayerDesignerExtension]  

     // All menu commands must export ICommandExtension:  
     [Export (typeof(ICommandExtension))]  
     // CHANGE class name – determines order of appearance on menu:  
     public class Menu1 : ICommandExtension  
     {  
       [Import]  
       public IDiagramContext DiagramContext { get; set; }  

       public void QueryStatus(IMenuCommand command)  
       { // Set command.Visible or command.Enabled to false  
         // to disable the menu command.  
         command.Visible = command.Enabled = true;  
       }  

       public string Text  
       {  
         get { return "MENU COMMAND LABEL"; }  
       }  

       public void Execute(IMenuCommand command)  
       {  
         // A selection of starting points:  
         IDiagram diagram = this.DiagramContext.CurrentDiagram;  
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
         { IElement element = shape.Element; }  
         IModelStore modelStore = diagram.ModelStore;  
         IModel model = modelStore.Root;  
         foreach (IElement element in modelStore.AllInstances<IClass>())   
         { }  
       }  
     }  
   }  
   ```  

    メソッドに記述する内容の詳細については、「 [メニュー コマンドの実装](#Implementing)」を参照してください。  

   VSIX プロジェクトにメニュー コマンドを追加する必要があります。VSIX プロジェクトは、コマンドをインストールするためのコンテナーとして機能します。 必要に応じて、同じ VSIX に他のコンポーネントを追加できます。  

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>VSIX プロジェクトにメニュー コマンドを追加するには  

1.  メニュー コマンドを独自の VSIX と共に作成した場合、この手順は必要ありません。  

2.  ソリューションに既存の VSIX プロジェクトが存在しない場合は、新しく作成します。  

    1.  **ソリューション エクスプローラー**で、ソリューションのショートカット メニューを開き、 **[追加]**、 **[新しいプロジェクト]** の順にクリックします。  

    2.  **[インストールされたテンプレート]** の **[Visual C#]** または **[Visual Basic]** を展開し、 **[機能拡張]** をクリックします。 中央の列で、 **[VSIX プロジェクト]** をクリックします。  

3.  ソリューション エクスプローラーで、VSIX プロジェクトのショートカット メニューを開き、 **[スタートアップ プロジェクトに設定]** をクリックします。  

4.  **source.extension.vsixmanifest**を開きます。  

    1.  **[メタデータ]** タブで、VSIX の名前を設定します。  

    2.  **[インストールの対象]** タブで、Visual Studio のバージョンを対象として設定します。  

    3.  **[アセット]** タブで、 **[新規作成]** をクリックし、ダイアログ ボックスで次のように設定します。  

         **[種類]** = **MEF コンポーネント**  

         **[ソース]** = **現在のソリューション内のプロジェクト**  

         **[プロジェクト]** = *クラス ライブラリ プロジェクト*  

##  <a name="Implementing"></a> メニュー コマンドの実装  
 メニュー コマンド クラスは、<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> に必要なメソッドを実装します。  

|||  
|-|-|  
|`string Text { get; }`|メニュー項目のラベルを返します。|  
|`void QueryStatus(IMenuCommand command);`|ユーザーが図上で右クリックすると呼び出されます。<br /><br /> このメソッドによってモデルが変更されることはありません。<br /><br /> `DiagramContext.CurrentDiagram.SelectedShapes` は、コマンドを表示して有効にするかどうかを指定するために使用します。<br /><br /> 設定できる値:<br /><br /> -   `command.Visible` `true`場合は、ダイアグラム内を右クリックしたときに、コマンドがメニューに表示する必要があります<br />-   `command.Enabled` `true`場合は、ユーザーがメニューのコマンドをクリックして<br />-   `command.Text` メニュー ラベルを動的に設定するには|  
|`void Execute (IMenuCommand command);`|ユーザーがメニュー項目をクリックすると呼び出されます (メニュー項目が表示され、有効な場合)。|  

### <a name="accessing-the-model-in-code"></a>コードのモデルにアクセスする  
 メニュー コマンド クラスに、次の宣言を含めます。  

```  
[Import] public IDiagramContext DiagramContext { get; set; }  
```  

 ...  

 `IDiagramContext` の宣言により、図、現在の選択項目、およびモデルにアクセスするメソッドにコードを記述することができます。  

```  
IDiagram diagram = this.DiagramContext.CurrentDiagram;  
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())  
{ IElement element = shape.Element; ... }  
IModelStore modelStore = diagram.ModelStore;  
IModel model = modelStore.Root;  
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}  
```  

### <a name="navigating-and-updating-the-model"></a>モデルをナビゲートおよび更新する  
 UML モデルの要素は、すべて API を通じて使用できます。 現在の選択項目から、またはモデルのルートから、その他すべての要素にアクセスすることができます。 詳細については、次を参照してください。 [UML モデル内を移動](../modeling/navigate-the-uml-model.md)と[UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)します。  

 シーケンス図を処理する場合も参照してください[UML API を使用して編集 UML シーケンス図](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)します。  

 この API を使用すると、要素のプロパティを変更し、要素と関係を削除し、新規要素および関係を生成することもできます。  

 既定では、Execute メソッドに対する変更は、別のトランザクションで実行されます。 ユーザーは、それぞれの変更を個別に元に戻すことができます。 グループの 1 つのトランザクションに変更する場合を使用して、 <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> 」の説明に従って[トランザクションを使用してリンク UML モデルの更新](../modeling/link-uml-model-updates-by-using-transactions.md)します。  

### <a name="use-the-ui-thread-for-updates"></a>更新の際の UI スレッドの使用  
 バックグラウンド スレッドからモデルの更新を行うと便利な場合があります。 たとえば、コマンドを使用して低速なリソースからデータを読み込む場合は、その処理をバックグラウンド スレッドで実行できます。これにより、ユーザーは実行中の変更を確認し、必要に応じて操作を取り消すことができます。  

 ただし、モデル ストアがスレッド セーフでないことに注意してください。 更新を行うには、必ずユーザー インターフェイス (UI) スレッドを使用する必要があります。可能な場合は、バックグラウンド操作の実行中にユーザーが編集を行えないようにしてください。 例については、次を参照してください。[バック グラウンド スレッドから UML モデルを更新](../modeling/update-a-uml-model-from-a-background-thread.md)します。  

##  <a name="Executing"></a> メニュー コマンドの実行  
 テストを行う場合は、コマンドをデバッグ モードで実行します。  

#### <a name="to-test-the-menu-command"></a>メニュー コマンドをテストするには  

1.  **F5**キーを押すか、 **[デバッグ]** メニューの **[デバッグ開始]** をクリックします。  

     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の実験用のインスタンスが開始します。  

     **トラブルシューティング**: 新しい [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] が起動しない場合:  

    -   複数のプロジェクトがある場合は、VSIX プロジェクトがソリューションのスタートアップ プロジェクトとして設定されていることを確認してください。  

    -   ソリューション エクスプローラーで、スタートアップまたはプロジェクトのみのショートカット メニューを開き、 **[プロパティ]** をクリックします。 プロジェクトのプロパティ エディターで、 **[デバッグ]** タブをクリックします。[外部プログラムの開始]** フィールドの文字列が [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]の完全なパス名であることを確認してください。通常は次のようになります。  

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`  

2.  実験用の [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]で、モデリング プロジェクトを開くか、または生成し、モデリング図を開くか、または生成します。 メニュー コマンド クラスの属性に表示されているいずれかの種類に含まれる図を使用してください。  

3.  図の任意の場所でショートカット メニューを開きます。 コマンドがメニューに表示されます。  

     **トラブルシューティング**: コマンドがメニューに表示されない場合は、次の点について確認してください。  

    -   メニュー コマンド プロジェクトは、VSIX プロジェクトの **source.extensions.manifest** の **[アセット]** タブに MEF コンポーネントとして表示される。  

    -   `Import` 属性と `Export` 属性のパラメーターが有効である。  

    -   `QueryStatus`メソッドが設定されていない、`command`します。`Enabled` または`Visible`フィールドを`false`します。  

    -   使用するモデル図の種類 (UML クラス、シーケンスなど) が、メニュー コマンド クラスの属性 ( `[ClassDesignerExtension]`、 `[SequenceDesignerExtension]` など) の 1 つとして表示される。  

##  <a name="Installing"></a> インストールして、拡張機能をアンインストールします。  
 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 拡張機能は、自分のコンピューターと他のコンピューターの両方にインストールできます。  

#### <a name="to-install-an-extension"></a>拡張機能をインストールするには  

1.  自分のコンピューターで、VSIX プロジェクトによってビルドされた **.vsix** ファイルを見つけます。  

    1.  **ソリューション エクスプローラー**で、VSIX プロジェクトのショートカット メニューを開き、 **[エクスプローラーでフォルダーを開く]** をクリックします。  

    2.  ファイルを見つけます**bin\\\*\\**_プロジェクト_**.vsix**  

2.  拡張機能をインストールする対象のコンピューターに **.vsix** ファイルをコピーします。 自分のコンピューターでも別のコンピューターでもかまいません。  

     ターゲット コンピューターには、各エディションのいずれかが必要[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]で指定した**source.extension.vsixmanifest**します。  

3.  ターゲット コンピューターで **.vsix** ファイルを開きます。たとえば、ダブルクリックして開きます。  

     **Visual Studio 拡張機能インストーラー** が起動され、拡張機能がインストールされます。  

4.  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]を起動または再起動します。  

#### <a name="to-uninstall-an-extension"></a>拡張機能をアンインストールするには  

1. **[ツール]** メニューの **[拡張機能と更新プログラム]** をクリックします。  

2. **[インストール済みの拡張機能]** を展開します。  

3. 拡張機能を選択し、 **[アンインストール]** をクリックします。  

   拡張機能の障害が原因で読み込みが失敗し、エラー ウィンドウにレポートが生成されることがまれにありますが、それは拡張機能マネージャーには表示されません。 その場合は、以下の場所からファイルを削除して、拡張機能を削除します。  

   *%Localappdata%* **\Local\Microsoft\VisualStudio\\[バージョン] \Extensions**  

##  <a name="MenuExample"></a> 「例」  
 クラス図の 2 つの要素の名前を入れ替えるメニュー コマンドのコードを次の例に示します。 このコードは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 拡張機能プロジェクト内でビルドし、前のセクションで説明した手順に従ってインストールする必要があります。  

```  
using System.Collections.Generic; // for IEnumerable  
using System.ComponentModel.Composition;  
  // for [Import], [Export]  
using System.Linq; // for IEnumerable extensions  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
  // for IDiagramContext  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
  // for designer extension attributes  
using Microsoft.VisualStudio.Modeling.Diagrams;  
  // for ShapeElement  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext  
using Microsoft.VisualStudio.Uml.Classes;  
  // for class diagrams, packages  

/// <summary>  
/// Extension to swap names of classes in a class diagram.  
/// </summary>  
namespace SwapClassNames  
{  
  // Declare the class as an MEF component:  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  // Add more ExportMetadata attributes to make  
  // the command appear on diagrams of other types.  
  public class NameSwapper : ICommandExtension  
  {  
  // MEF required interfaces:  
  [Import]  
  public IDiagramContext Context { get; set; }  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  

  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  /// <param name="command"></param>  
  public void Execute(IMenuCommand command)  
  {  
    // Get selected shapes that are IClassifiers -  
    // IClasses, IInterfaces, IEnumerators.  
    var selectedShapes = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  

    // Get model elements displayed by shapes.  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  

    // Do the swap in a transaction so that user  
    // cannot undo one change without the other.  
    using (ILinkedUndoTransaction transaction =  
    LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
    string firstName = firstElement.Name;  
    firstElement.Name = lastElement.Name;  
    lastElement.Name = firstName;  
    transaction.Commit();  
    }  
  }  

  /// <summary>  
  /// Called by Visual Studio to determine whether  
  /// menu item should be visible and enabled.  
  /// </summary>  
  public void QueryStatus(IMenuCommand command)  
  {   
    int selectedClassifiers = Context.CurrentDiagram  
     .GetSelectedShapes<IClassifier>().Count();  
    command.Visible = selectedClassifiers > 0;  
    command.Enabled = selectedClassifiers == 2;  
  }  

  /// <summary>  
  /// Name of the menu command.  
  /// </summary>  
  public string Text  
  {  
    get { return "Swap Names"; }  
  }  
  }  

}  
```  

## <a name="see-also"></a>関連項目  
 [定義およびモデリング拡張機能のインストール](../modeling/define-and-install-a-modeling-extension.md)   
 [UML モデルと図を拡張します。](../modeling/extend-uml-models-and-diagrams.md)   
 [モデリング図にジェスチャ ハンドラーを定義します。](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [定義のカスタム モデリング ツールボックス アイテム](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [UML モデルの検証制約を定義します。](../modeling/define-validation-constraints-for-uml-models.md)   
 [UML API を使用して UML シーケンス図を編集します。](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)   
 [UML API を使用したプログラミング](../modeling/programming-with-the-uml-api.md)   
 [UML 図で図形を整理するコマンドの例:](http://go.microsoft.com/fwlink/?LinkID=213809)



