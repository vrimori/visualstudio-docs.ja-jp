---
title: プロジェクト プロパティの取得 |Microsoft Docs
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
ms.openlocfilehash: 58967c87b86eff8ab00e343ee872637e18ee57ed
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497756"
---
# <a name="get-project-properties"></a>プロジェクトのプロパティを取得します。
このチュートリアルではツール ウィンドウでプロジェクトのプロパティを表示する方法。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)します。  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>VSIX プロジェクトを作成し、ツール ウィンドウを追加するには  
  
1.  すべての Visual Studio 拡張機能は、拡張機能資産が含まれる VSIX 配置プロジェクトで開始します。 作成、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]という名前の VSIX プロジェクト`ProjectPropertiesExtension`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** > **Extensibility**します。  
  
2.  ツール ウィンドウを追加するには、という名前のカスタム ツール ウィンドウの項目テンプレートを追加`ProjectPropertiesToolWindow`します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目の**します。 **新しい項目の追加 ダイアログ**に移動して、 **Visual c# アイテム** > **拡張**選択**カスタム ツール ウィンドウ**。 **名前**ダイアログの下部にあるフィールドに、ファイル名を変更して`ProjectPropertiesToolWindow.cs`します。 カスタム ツール ウィンドウを作成する方法の詳細については、次を参照してください。[ツール ウィンドウで拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
3.  ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>ツール ウィンドウにプロジェクトのプロパティを表示するには  
  
1.  ProjectPropertiesToolWindowCommand.cs ファイルで、次を追加ステートメントを使用します。  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  *ProjectPropertiesToolWindowControl.xaml*TreeView をツールボックスから追加、既存のボタンを削除します。 Click イベント ハンドラーを削除することも、 *ProjectPropertiesToolWindowControl.xaml.cs*ファイル。  
  
3.  *ProjectPropertiesToolWindowCommand.cs*を使用して、`ShowToolWindow()`メソッドをプロジェクトを開き、そのプロパティの読み取りがしプロパティをツリー ビューに追加します。 ShowToolWindow のコードは次のようになります。  
  
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
  
6.  **ビュー** > **その他の Windows**クリックして**ProjectPropertiesToolWindow**します。  
  
     最初のプロジェクトのすべてのプロジェクト プロパティの名前と共にツール ウィンドウのツリー コントロールが表示されます。