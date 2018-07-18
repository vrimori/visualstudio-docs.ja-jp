---
title: ユニバーサル Windows プロジェクトを管理する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d251818d9fba0c025b94fa17611a725daad3cec8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147595"
---
# <a name="managing-universal-windows-projects"></a>ユニバーサル Windows プロジェクトを管理します。
ユニバーサル Windows アプリとは、Windows 8.1 と Windows Phone 8.1、両方のプラットフォームでコードやその他のアセットを使用する開発者の両方を対象とするアプリです。 共有コードおよびリソースは、プラットフォーム固有のコードおよびリソースが個別のプロジェクト、Windows と Windows Phone 用に保持されるときに、共有プロジェクトに保持されます。 ユニバーサル Windows アプリの詳細については、次を参照してください。[ユニバーサル Windows アプリ](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)です。 プロジェクトを管理する、visual Studio 拡張機能は、ユニバーサル Windows アプリ プロジェクトが 1 つのプラットフォームのアプリとは異なる構造を持つことに注意してください。 このチュートリアルでは、共有プロジェクトを移動し、共有項目を管理する方法を示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
### <a name="navigate-the-shared-project"></a>共有プロジェクトを移動します。  
  
1.  という名前の C# の場合は、VSIX プロジェクトを作成する**TestUniversalProject**です。 (**ファイル、新規]、[プロジェクト**し**C# の場合、拡張性、Visual Studio パッケージ**)。 追加、**にカスタム コマンド**プロジェクト項目テンプレート (ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし **追加/新しい項目の**に移動し、 **Extensibility**)。 ファイルの名前を付けます**TestUniversalProject**です。  
  
2.  Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll および Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll への参照を追加 (で、**拡張**セクション)。  
  
3.  TestUniversalProject.cs を開き、次の追加`using`ステートメント。  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  TestUniversalProject クラスでポイントするプライベート フィールドを追加、**出力**ウィンドウです。  
  
    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  TestUniversalProject コンス トラクター内の出力ペインへの参照を設定します。  
  
    ```csharp  
    private TestUniversalProject(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
        // get a reference to the Output window  
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));  
    }  
    ```  
  
6.  既存のコードからの削除、`ShowMessageBox`メソッド。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  このチュートリアルでいくつかの異なる目的で使用する DTE オブジェクトを取得します。 また、メニュー ボタンがクリックされたときに、ソリューションが読み込まれていることを確認してください。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {   
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));  
        if (dte.Solution != null)   
        {  
            . . .  
        }  
        else   
        {  
            MessageBox.Show("No solution is open");  
            return;   
        }  
    }  
    ```  
  
8.  共有プロジェクトを検索します。 共有プロジェクトは、純粋なコンテナーです。出力が生成またはビルドにしません。 次のメソッドをソリューション内の最初の共有プロジェクトを検索を探して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>共有プロジェクト機能を持つオブジェクト。  
  
    ```csharp  
    private IVsHierarchy FindSharedProject()  
    {  
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));  
        Guid empty = Guid.Empty;  
        IEnumHierarchies enumHiers;  
  
        //get all the projects in the solution  
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));  
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))  
        {  
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))  
            {  
                return hier;  
            }  
        }  
        return null;  
    }  
    ```  
  
9. `ShowMessageBox`メソッド、出力キャプション (含まれているプロジェクト名、**ソリューション エクスプ ローラー**) 共有プロジェクトのです。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
                }  
        else  
        {  
            MessageBox.Show("No solution is open");  
            return;  
        }  
    }  
    ```  
  
10. アクティブなプラットフォームのプロジェクトを取得します。 プラットフォームのプロジェクトとは、プラットフォーム固有のコードおよびリソースを含むプロジェクトです。 次のメソッドは、新しいフィールドを使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>active プラットフォームのプロジェクトを取得します。  
  
    ```csharp  
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)  
    {  
        IVsHierarchy activeProjectContext;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))  
        {  
            return activeProjectContext;  
        }  
        else  
        {  
            return null;  
        }  
    }  
    ```  
  
11. `ShowMessageBox`メソッドがアクティブなプラットフォームのプロジェクトのキャプションを出力します。  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
  
        if (dte.Solution != null)  
        {  
            var sharedHier = this.FindSharedProject();  
            if (sharedHier != null)  
            {  
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,  
                     (int)__VSHPROPID.VSHPROPID_Caption);  
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));  
  
                var activePlatformHier = this.GetActiveProjectContext(sharedHier);  
                if (activePlatformHier != null)  
                {  
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,  
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);  
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));  
                }  
                else  
                {  
                MessageBox.Show("Shared project has no active platform project");  
                }  
            }  
            else  
            {  
                MessageBox.Show("Solution has no shared project");  
                return;  
            }  
        }  
        else  
            {  
                MessageBox.Show("No solution is open");  
                return;  
            }  
        }  
  
    ```  
  
12. プラットフォームのプロジェクトを反復処理します。 次のメソッドは、共有プロジェクトからすべてのインポート (platform) プロジェクトを取得します。  
  
    ```csharp  
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)  
    {  
        IVsSharedAssetsProject sharedAssetsProject;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)  
            && sharedAssetsProject != null)  
        {  
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())  
            {  
                yield return importingProject;  
            }  
        }  
    }  
    ```  
  
    > [!IMPORTANT]
    >  ユーザーに、実験用インスタンスで C++ ユニバーサル Windows アプリ プロジェクトが開かれている場合、上記のコードは例外をスローします。 これは既知の問題です。 例外を回避するのには、置換、`foreach`上に次のブロックします。  
  
    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. `ShowMessageBox`メソッドは、各プラットフォームのプロジェクトのキャプションを出力します。 アクティブなプラットフォームのプロジェクトのキャプションを出力する行の後に、次のコードを挿入します。 この一覧に読み込まれるプラットフォーム プロジェクトのみが表示されます。  
  
    ```csharp  
    output.OutputStringThreadSafe("Platform projects:\n");  
  
    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);  
  
    bool isActiveProjectSet = false;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
            (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
    }  
    ```  
  
14. アクティブなプラットフォームのプロジェクトを変更します。 次のメソッドの設定を使用して、アクティブなプロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>です。  
  
    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. `ShowMessageBox`メソッド、アクティブなプラットフォーム プロジェクトを変更します。 このコードを挿入、`foreach`ブロックします。  
  
    ```csharp  
    bool isActiveProjectSet = false;  
    string platformCaption = null;  
    foreach (IVsHierarchy platformHier in projects)  
    {  
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,  
             (int)__VSHPROPID.VSHPROPID_Caption);  
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));  
  
        // if this project is neither the shared project nor the current active platform project,   
        // set it to be the active project  
        if (!isActiveProjectSet && platformHier != activePlatformHier)  
        {  
            this.SetActiveProjectContext(sharedHier, platformHier);  
            activePlatformHier = platformHier;  
            isActiveProjectSet = true;  
        }  
    }  
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');  
    ```  
  
16. 試してみましょう。F5 キーを押して、実験用インスタンスを起動します。 実験用インスタンスで c# ユニバーサル ハブ アプリケーション プロジェクトを作成 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/Windows/Windows 8/ユニバーサル/ハブ アプリ**)。 ソリューションが読み込まれた後に移動、**ツール**メニューをクリック**呼び出す TestUniversalProject**テキストを確認し、**出力**ウィンドウです。 次のようなものが表示されます。  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### <a name="manage-the-shared-items-in-the-platform-project"></a>プラットフォームのプロジェクトで共有のアイテムを管理します。  
  
1.  プラットフォームのプロジェクトでの共有項目を検索します。 共有プロジェクト内の項目は、プラットフォームのプロジェクトで共有項目として表示されます。 表示することはできません、**ソリューション エクスプ ローラー**、それらを探してプロジェクトの階層を行うことができますが、します。 次のメソッドは、階層について説明し、すべての共有アイテムを収集します。 必要に応じて、各項目のキャプションを出力します。 共有アイテムは、新しいプロパティで識別される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>です。  
  
    ```csharp  
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)  
    {  
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);  
        if (printItems)  
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));  
  
        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items  
        bool isSharedItem;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)  
            && (isSharedItem == getSharedItems))  
        {  
            itemIds.Add(itemid);  
        }  
  
        uint child;  
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)  
            && child != (uint)VSConstants.VSITEMID.Nil)  
        {  
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
  
            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)  
                && child != (uint)VSConstants.VSITEMID.Nil)  
            {  
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);  
            }  
                    }  
    }  
    ```  
  
2.  `ShowMessageBox`メソッド、プラットフォームのプロジェクト階層アイテムのすべての要素の次のコードを追加します。 内で挿入、`foreach`ブロックします。  
  
    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  共有項目を読み取る。 共有アイテムが非表示のリンクされたファイルとしてプラットフォーム プロジェクトで表示され、として通常のリンクされたファイルのすべてのプロパティを読み取ることができます。 次のコードでは、共有の最初の項目の完全なパスを読み取ります。  
  
    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  試してみましょう。F5 キーを押して、実験用インスタンスを起動します。 実験用インスタンスで c# ユニバーサル ハブ アプリケーション プロジェクトを作成 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#/Windows/Windows 8/ユニバーサル/ハブ アプリ**) に移動して、**ツール**メニューをクリック**呼び出す TestUniversalProject**テキストを確認し、**出力**ウィンドウです。 次のようなものが表示されます。  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    Walk the active platform project:  
        HubApp.WindowsPhone  
            <HubApp.Shared>  
                App.xaml  
                    App.xaml.cs  
                Assets  
                    DarkGray.png  
                    LightGray.png  
                    MediumGray.png  
                Common  
                    NavigationHelper.cs  
                    ObservableDictionary.cs  
                    RelayCommand.cs  
                    SuspensionManager.cs  
                DataModel  
                    SampleData.json  
                    SampleDataSource.cs  
                HubApp.Shared.projitems  
                Strings  
                    en-US  
                        Resources.resw  
            Assets  
                HubBackground.theme-dark.png  
                HubBackground.theme-light.png  
                Logo.scale-240.png  
                SmallLogo.scale-240.png  
                SplashScreen.scale-240.png  
                Square71x71Logo.scale-240.png  
                StoreLogo.scale-240.png  
                WideLogo.scale-240.png  
            HubPage.xaml  
                HubPage.xaml.cs  
            ItemPage.xaml  
                ItemPage.xaml.cs  
            Package.appxmanifest  
            Properties  
                AssemblyInfo.cs  
            References  
                .NET for Windows Store apps  
                HubApp.Shared  
                Windows Phone 8.1  
            SectionPage.xaml  
                SectionPage.xaml.cs  
    ```  
  
### <a name="detecting-changes-in-platform-projects-and-shared-projects"></a>プラットフォームのプロジェクトと共有プロジェクトの変更の検出  
  
1.  プロジェクトでは共有、変更を検出するために階層とプロジェクトのイベントを使用するには、プロジェクトのプラットフォームと同様です。 ただし、共有プロジェクトにプロジェクト項目は表示されません、つまり、共有プロジェクト項目が変更されたときに特定のイベントは起動されません。  
  
     プロジェクト内のファイルの名前が変更されるイベントの順序を考慮してください。  
  
    1.  ファイル名をディスクに変更します。  
  
    2.  ファイルの新しい名前を含めるには、プロジェクト ファイルが更新されます。  
  
     階層のイベント (たとえば、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) 通常ように、UI に表示される変更の追跡、**ソリューション エクスプ ローラー**です。 階層のイベントは、ファイルの削除し、ファイルの追加で構成するファイルの名前の変更操作を検討してください。 ただし、非表示の項目が変更されると、階層イベント システムが起動した。、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>イベントがない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベント。 そのため、プラットフォームのプロジェクト内のファイルの名前を変更する場合、取得両方<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>、共有プロジェクトのファイルの名前を変更すると、表示のみが、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>です。  
  
     プロジェクト項目の変更を追跡するためには、DTE プロジェクト項目のイベントを処理することができます (のものが見つかった<xref:EnvDTE.ProjectItemsEventsClass>)。 ただし、多数のイベントを処理している場合は、イベントの処理パフォーマンスを向上させるを入手できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>です。 このチュートリアルでは、階層イベントのみおよび DTE イベントについて説明します。 この手順では、共有プロジェクトと、プラットフォームのプロジェクトに、イベント リスナーを追加します。 次に、共有プロジェクトで 1 つのファイルと、プラットフォームのプロジェクトで別のファイルの名前を変更するときに、名前の変更操作ごとに発生するイベントを表示できます。  
  
     この手順では、共有プロジェクトと、プラットフォームのプロジェクトに、イベント リスナーを追加します。 次に、共有プロジェクトで 1 つのファイルと、プラットフォームのプロジェクトで別のファイルの名前を変更するときに、名前の変更操作ごとに発生するイベントを表示できます。  
  
2.  イベント リスナーを追加します。 新しいクラス ファイルをプロジェクトに追加し、HierarchyEventListener.cs 付けます。  
  
3.  HierarchyEventListener.cs ファイルを開き、次の追加のステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  `HierarchyEventListener`クラス実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  メンバーを実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>次のコードのように、します。  
  
    ```csharp  
    class HierarchyEventListener : IVsHierarchyEvents  
    {  
        private IVsHierarchy hierarchy;  
        IVsOutputWindowPane output;   
  
        internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {  
             this.hierarchy = hierarchy;  
             this.output = outputWindow;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemDeleted(uint itemID) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");  
            return VSConstants.S_OK;  
        }  
  
        int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {  
            output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");  
            return VSConstants.S_OK;  
        }  
    }  
  
    ```  
  
6.  同じクラスで DTE イベントの別のイベント ハンドラーを追加<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>、プロジェクト項目の名前が変更されるたびに発生します。  
  
    ```csharp  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  階層のイベントにサインアップします。 個別に追跡しているすべてのプロジェクトにサインアップする必要があります。 次のコードを追加`ShowMessageBox`、共有プロジェクト、および他のプラットフォームのプロジェクトのいずれかのいずれか。  
  
    ```csharp  
    // hook up the event listener for hierarchy events on the shared project  
    HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);  
    uint cookie1;  
    sharedHier.AdviseHierarchyEvents(listener1, out cookie1);  
  
    // hook up the event listener for hierarchy events on the   
    active project  
    HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);  
    uint cookie2;  
    activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);  
    ```  
  
8.  DTE プロジェクト項目のイベントにサインアップする<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>です。 2 つ目のリスナーをフックする後は、次のコードを追加します。  
  
    ```csharp  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. 共有項目を変更します。 プラットフォームのプロジェクトの共有項目を変更することはできません。代わりに、これらのアイテムの実際の所有者である共有プロジェクトに変更する必要があります。 共有プロジェクトに、対応する項目の ID を取得できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>、共有アイテムの完全なパスを指定します。 共有項目を変更します。 変更は、プラットフォームのプロジェクトに反映されます。  
  
    > [!IMPORTANT]
    >  プロジェクト項目が変更する前に、共有項目がかどうかを調べる必要があります。  
  
     次のメソッドでは、プロジェクト項目ファイルの名前を変更します。  
  
    ```csharp  
    private void ModifyFileNameInProject(IVsHierarchy project, string path)  
    {    
        int found;  
        uint projectItemID;  
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];  
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))  
            && found != 0)  
        {  
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);  
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);  
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));  
        }  
    }  
    ```  
  
10. すべての他のコードでこのメソッドを呼び出す`ShowMessageBox`ファイルの共有プロジェクト内の項目の名前を変更します。 共有プロジェクト内のアイテムの完全なパスを取得するコードの後に、これを挿入します。  
  
    ```csharp  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. プロジェクトをビルドして実行します。 C# ユニバーサル ハブ アプリケーションを作成する、実験用インスタンスでは、「、**ツール**メニューをクリック**呼び出す TestUniversalProject**、一般出力ウィンドウ内テキストを確認します。 共有の最初の項目の名前 (お本来は、App.xaml ファイルである) プロジェクトを変更する必要がありますと表示されます、<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>イベントが発生します。 この例では、App.xaml の名前を変更するも名前を変更する App.xaml.cs、ので (プラットフォーム プロジェクトごとに 2 つ) 4 つのイベントが表示されます。 (DTE イベントは、共有プロジェクトに項目を追跡しないしません)。2 つが表示されます<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>(プラットフォームのプロジェクトごとに 1 つ)、イベントがない<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベント。  
  
12. プラットフォームのプロジェクト内のファイルの名前を変更してみましょうおよび取得される発生するイベントの違いを確認することができます。 次のコードを追加`ShowMessageBox`への呼び出し後`ModifyFileName`です。  
  
    ```csharp  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. プロジェクトをビルドして実行します。 実験用インスタンスで c# ユニバーサル プロジェクトの作成は、「、**ツール**メニューをクリック**呼び出す TestUniversalProject**、一般出力ウィンドウ内テキストを確認します。 プラットフォームのプロジェクト内のファイルの名前を変更した後、両方を表示する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベントおよび<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>イベント。 変更した後、ファイルの原因となったなし、変更するには、その他のファイル、任意の場所、プラットフォームのプロジェクト内の項目への変更は反映しない、ための 1 つだけ各これらのイベント。