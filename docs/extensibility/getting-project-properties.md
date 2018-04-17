---
title: プロジェクトのプロパティの取得 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d93e941c98293ca1d28f92bce1bc8c21f5ca2121
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getting-project-properties"></a>プロジェクトのプロパティの取得
このチュートリアルでは、ツール ウィンドウでプロジェクトのプロパティを表示する方法です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
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