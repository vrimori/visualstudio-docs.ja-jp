---
title: プロジェクト プロパティの取得 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b99e86c4b955471ee10e0eb63cb5ca81fa675263
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561596"
---
# <a name="getting-project-properties"></a>プロジェクト プロパティの取得
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルではツール ウィンドウでプロジェクトのプロパティを表示する方法。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX プロジェクトを作成し、ツール ウィンドウを追加するには  
  
1.  すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]という名前の VSIX プロジェクト`ProjectPropertiesExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#/機能拡張**します。  
  
2.  ツール ウィンドウを追加するには、という名前のカスタム ツール ウィンドウの項目テンプレートを追加`ProjectPropertiesToolWindow`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加 ダイアログ**に移動して、 **Visual c# アイテム/機能拡張**選択と**カスタム ツール ウィンドウ**します。 **名前**ダイアログの下部にあるフィールドに、ファイル名を変更して`ProjectPropertiesToolWindow.cs`します。 カスタム ツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
3.  ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>ツール ウィンドウにプロジェクトのプロパティを表示するには  
  
1.  ProjectPropertiesToolWindowCommand.cs ファイルで、次を追加ステートメントを使用します。  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  ProjectPropertiesToolWindowControl.xaml、既存のボタンを削除し、ツールボックスから、TreeView を追加します。 ProjectPropertiesToolWindowControl.xaml.cs ファイルから、クリック イベント ハンドラーを削除することもできます。  
  
3.  ProjectPropertiesToolWindowCommand.cs、ShowToolWindow() メソッドを使用して、プロジェクトを開き、そのプロパティを読み取るし、ツリー ビューにプロパティを追加します。 ShowToolWindow のコードは次のようになります。  
  
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
  
5.  実験用インスタンスでプロジェクトを開きます。  
  
6.  **ビュー/その他の Windows**クリックして**ProjectPropertiesToolWindow**します。  
  
     最初のプロジェクトのすべてのプロジェクト プロパティの名前と共にツール ウィンドウのツリー コントロールが表示されます。

