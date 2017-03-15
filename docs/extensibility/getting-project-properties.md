---
title: "プロジェクトのプロパティを取得する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 09a811a3bb42f5de9406ec85038579b5545619ae
ms.lasthandoff: 02/22/2017

---
# <a name="getting-project-properties"></a>プロジェクトのプロパティを取得します。
このチュートリアルではツール ウィンドウでプロジェクトのプロパティを表示する方法です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX プロジェクトを作成し、ツール ウィンドウを追加するには  
  
1.  すべての Visual Studio 拡張機能は、拡張機能の資産を格納する VSIX 配置プロジェクトから開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`ProjectPropertiesExtension`します。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  ツール ウィンドウを追加するには、という名前のカスタム ツール ウィンドウの項目テンプレートを追加`ProjectPropertiesToolWindow`します。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックして、選択**追加/新しい項目の**です。 **新しい項目の追加 ダイアログ ボックス**には、 **Visual c# アイテム/機能拡張**選択**カスタム ツール ウィンドウ**です。 **名**ダイアログの下部にあるフィールドに、ファイルの名前を変更する`ProjectPropertiesToolWindow.cs`です。 カスタム ツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
3.  ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>ツール ウィンドウにプロジェクトのプロパティを表示するには  
  
1.  ProjectPropertiesToolWindowCommand.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  ProjectPropertiesToolWindowControl.xaml、既存のボタンを削除し、ツールボックスから、TreeView を追加します。 ProjectPropertiesToolWindowControl.xaml.cs ファイルから、クリック イベント ハンドラーを削除することもできます。  
  
3.  ProjectPropertiesToolWindowCommand.cs、ShowToolWindow() メソッドを使用して、プロジェクトを開き、そのプロパティの読み取りをし、ツリー ビューにプロパティを追加します。 ShowToolWindow のコードは、次のようになります。  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  実験用インスタンスでは、プロジェクトを開きます。  
  
6.  **ビュー/その他のウィンドウ**クリックして**ProjectPropertiesToolWindow**します。  
  
     最初のプロジェクトおよびそのすべてのプロジェクトのプロパティの名前とツール ウィンドウのツリー コントロールが表示されます。
