---
title: "プロジェクトのプロパティの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 931c4c6495d13418ed94f0507a00351e82a92564
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="getting-project-properties"></a>プロジェクトのプロパティの取得
このチュートリアルでは、ツール ウィンドウでプロジェクトのプロパティを表示する方法です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX プロジェクトを作成し、ツール ウィンドウを追加するには  
  
1.  すべての Visual Studio 拡張機能は、資産を拡張機能を含んでいる VSIX 配置プロジェクトを開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`ProjectPropertiesExtension`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**です。  
  
2.  という名前のカスタムのツール ウィンドウの項目テンプレートを追加することで、ツール ウィンドウを追加`ProjectPropertiesToolWindow`です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加 ダイアログ**には、 **Visual c# アイテム/機能拡張**選択**カスタムのツール ウィンドウ**します。 **名前**ダイアログの下部にあるフィールドに、ファイル名に変更`ProjectPropertiesToolWindow.cs`です。 カスタムのツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
3.  ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>ツール ウィンドウにプロジェクトのプロパティを表示するには  
  
1.  ProjectPropertiesToolWindowCommand.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  ProjectPropertiesToolWindowControl.xaml、既存のボタンを削除し、[ツールボックス] からの TreeView を追加します。 ProjectPropertiesToolWindowControl.xaml.cs ファイルからクリック イベント ハンドラーを削除することもできます。  
  
3.  ProjectPropertiesToolWindowCommand.cs、ShowToolWindow() メソッドを使用して、プロジェクトを開き、そのプロパティを読み取る TreeView にプロパティを追加します。 ShowToolWindow のコードは、次のようになります。  
  
    ```csharp  
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
  
6.  **ビュー/その他のウィンドウ**クリックして**ProjectPropertiesToolWindow**です。  
  
     最初のプロジェクトとそのすべてのプロジェクトのプロパティの名前と共に、ツール ウィンドウのツリー コントロールが表示されます。