---
title: "ユニバーサル Windows プロジェクトの管理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# ユニバーサル Windows プロジェクトの管理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ユニバーサル Windows アプリは、Windows 8.1 と Windows Phone 8.1、両方のプラットフォームでのコードやその他のアセットを使用する開発者の両方を対象とするアプリです。 共有コードとリソースは、プラットフォーム固有のコードおよびリソースが個別のプロジェクト、Windows Phone 用および Windows のいずれかの保持中に、共有プロジェクトに保持されます。 ユニバーサル Windows アプリについての詳細については、次を参照してください。 [ユニバーサル Windows アプリ](http://msdn.microsoft.com/library/windows/apps/dn609832.aspx)します。 プロジェクトを管理する、visual Studio 拡張機能は、ユニバーサル Windows アプリ プロジェクトが単一プラットフォームのアプリとは異なる構造を持っていることに注意する必要があります。 このチュートリアルでは、共有プロジェクトを移動し、共有アイテムを管理する方法を示します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
### 共有プロジェクトを移動します。  
  
1.  という名前の C\# の場合は、VSIX プロジェクトを作成する **TestUniversalProject**します。 \(**ファイル\]、\[新規\]、\[プロジェクト** し **C\# の場合、拡張性、Visual Studio パッケージ**\)。 追加、 **にカスタム コマンド** プロジェクト項目テンプレート \(ソリューション エクスプ ローラーで、プロジェクト ノードを右クリックし \[ **追加\/\[新しい項目の**, に移動し、 **拡張**\)。 ファイルに名前を **TestUniversalProject**します。  
  
2.  Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll および Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll への参照の追加 \(で、 **拡張** セクション\)。  
  
3.  TestUniversalProject.cs を開き、次の追加 `using` ステートメント。  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.Internal.VisualStudio.PlatformUI;   
    using System.Collections.Generic;   
    using System.IO;  
    using System.Windows.Forms;  
    ```  
  
4.  TestUniversalProject クラスでポイントするプライベート フィールドを追加、 **出力** ウィンドウです。  
  
    ```c#  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  
  
5.  TestUniversalProject コンス トラクター内にある出力ウィンドウへの参照を設定します。  
  
    ```c#  
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
  
6.  既存のコードからの削除、 `ShowMessageBox` メソッド。  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)   
    {  
    }  
    ```  
  
7.  このチュートリアルではいくつかの異なる目的で使用する DTE オブジェクトを取得します。 また、メニュー ボタンがクリックされたときに、ソリューションが読み込まれていることを確認してください。  
  
    ```c#  
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
  
8.  共有プロジェクトを検索します。 共有プロジェクトは、純粋なコンテナーです。ビルドや出力を生成できません。 次のメソッドなソリューション内の最初の共有プロジェクトの検出を探して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 共有プロジェクトの機能を持つオブジェクト。  
  
    ```c#  
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
  
9. `ShowMessageBox` メソッドを出力キャプション \(に表示されるプロジェクトの名前、 **ソリューション エクスプ ローラー**\)、共有プロジェクトのです。  
  
    ```c#  
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
  
10. アクティブなプラットフォーム プロジェクトを取得します。 プラットフォームのプロジェクトとは、プラットフォーム固有のコードとリソースを含むプロジェクトです。 次のメソッドは、新しいフィールドを使用して <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7> をアクティブなプラットフォーム プロジェクトを取得します。  
  
    ```c#  
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
  
11. `ShowMessageBox` メソッドがアクティブなプラットフォーム プロジェクトのキャプションを出力します。  
  
    ```c#  
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
  
12. プラットフォームのプロジェクトを反復処理します。 次のメソッドは、共有プロジェクトからインポートするすべての \(プラットフォーム\) プロジェクトを取得します。  
  
    ```c#  
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
    >  ユーザーには、実験用インスタンスで C\+\+ ユニバーサル Windows アプリ プロジェクトが開き、上記のコードは例外をスローします。 これは、既知の問題です。 例外を避けるためには、置換、 `foreach` の上に次のブロックします。  
  
    ```c#  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  
  
13. `ShowMessageBox` メソッドは、各プラットフォーム プロジェクトのキャプションを出力します。 アクティブなプラットフォーム プロジェクトのキャプションを出力する行の後に次のコードを挿入します。 この一覧に読み込まれているプラットフォーム プロジェクトのみが表示されます。  
  
    ```c#  
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
  
14. アクティブなプラットフォーム プロジェクトを変更します。 次の設定を使用して、アクティブなプロジェクト <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>します。  
  
    ```c#  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  
  
15. `ShowMessageBox` メソッドでは、アクティブなプラットフォームのプロジェクトを変更します。 内でこのコードを挿入、 `foreach` ブロックします。  
  
    ```c#  
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
  
16. 試してみましょう。 F5 キーを押して、実験用インスタンスを起動します。 実験用インスタンスで c\# ハブのユニバーサル アプリ プロジェクトの作成 \(で、 **新しいプロジェクト** ダイアログ ボックスで、 **Visual c\#\/Windows\/Windows 8 ユニバーサル\/\/ハブ アプリケーション**\)。 ソリューションが読み込まれた後に、 **ツール** メニューをクリック **呼び出す TestUniversalProject**, テキストを確認し、 **出力** ウィンドウです。 次のような結果を表示する必要があります。  
  
    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  
  
### プラットフォームのプロジェクトで共有項目を管理します。  
  
1.  プラットフォーム プロジェクトの共有の項目を検索します。 共有プロジェクト内の項目が、プラットフォーム プロジェクトに共有項目として表示されます。 表示されない、 **ソリューション エクスプ ローラー**, を探せば、プロジェクト階層を移動することができますが、します。 次のメソッドは、階層について説明し、すべての共有アイテムを収集します。 必要に応じて、各項目のキャプションを出力します。 共有項目が、新しいプロパティで識別される <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>します。  
  
    ```c#  
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
  
2.  `ShowMessageBox` メソッドをプラットフォーム プロジェクトの階層構造の項目を順番に次のコードを追加します。 内での挿入、 `foreach` ブロックします。  
  
    ```c#  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  
  
3.  共有アイテムを読み取る。 共有の項目が非表示のリンクされたファイルとしてプラットフォーム プロジェクトが表示され、通常のリンクされたファイルとしてのすべてのプロパティを読み取ることができます。 次のコードでは、共有の最初の項目の完全なパスを読み取ります。  
  
    ```c#  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  
  
4.  試してみましょう。 F5 キーを押して、実験用インスタンスを起動します。 実験用インスタンスで c\# ハブのユニバーサル アプリ プロジェクトの作成 \(で、 **新しいプロジェクト** ダイアログ ボックスで、 **Visual C\# の場合\/Windows\/Windows 8 ユニバーサル\/\/ハブ アプリケーション**\) に移動、 **ツール** メニューをクリック **呼び出す TestUniversalProject**, テキストを確認し、 **出力** ウィンドウです。 次のような結果を表示する必要があります。  
  
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
  
### プラットフォーム プロジェクトおよび共有プロジェクトの変更の検出  
  
1.  プラットフォーム プロジェクトと同様、共有プロジェクトでの変更を検出するために階層とプロジェクトのイベントを使用できます。 ただし、共有プロジェクトでプロジェクト項目は表示されません、つまり、共有プロジェクト項目が変更されたときに特定のイベントは起動されません。  
  
     プロジェクトのファイルの名前が変更されるイベントの順序を考慮してください。  
  
    1.  ファイルの名前は、ディスクに変更されます。  
  
    2.  ファイルの新しい名前を含めるには、プロジェクト ファイルが更新されます。  
  
     階層のイベント \(たとえば、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>\)、通常のように、UI に表示される変更を追跡、 **ソリューション エクスプ ローラー**します。 階層のイベントは、ファイルの削除と、ファイルの追加で構成するファイルの名前の変更操作を検討してください。 ただし、非表示の項目を変更すると、階層イベント システムが発生する <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> イベントではなく、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> イベントです。 そのため、プラットフォーム プロジェクトのファイルの名前を変更する場合、取得両方 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, が、共有プロジェクト内のファイルの名前を変更する場合のみ <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>します。  
  
     プロジェクト項目の変更を追跡するには、DTE プロジェクト項目のイベントを処理 \(記載されている <xref:EnvDTE.ProjectItemsEventsClass>\)。 ただし、多数のイベントを処理する場合は、イベントの処理パフォーマンスを向上させるを入手できます <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>します。 このチュートリアルでは、DTE イベントと階層のイベントのみを紹介します。 この手順では、共有のプロジェクトおよびプラットフォーム プロジェクトにイベント リスナーを追加します。 次に、プラットフォームのプロジェクトで別のファイルおよび共有プロジェクトの 1 つのファイルの名前を変更するときに、名前の変更操作ごとに発生するイベントを確認できます。  
  
     この手順では、共有のプロジェクトおよびプラットフォーム プロジェクトにイベント リスナーを追加します。 次に、プラットフォームのプロジェクトで別のファイルおよび共有プロジェクトの 1 つのファイルの名前を変更するときに、名前の変更操作ごとに発生するイベントを確認できます。  
  
2.  イベント リスナーを追加します。 新しいクラス ファイルをプロジェクトに追加し、HierarchyEventListener.cs 付けます。  
  
3.  HierarchyEventListener.cs ファイルを開き、次の追加のステートメントを使用します。  
  
    ```c#  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using System.IO;  
  
    ```  
  
4.  `HierarchyEventListener` クラス実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  
  
    ```c#  
    class HierarchyEventListener : IVsHierarchyEvents  
    { }  
  
    ```  
  
5.  メンバーを実装 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, 次のコードでは、次のようにします。  
  
    ```c#  
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
  
6.  同じクラスで DTE イベントの別のイベント ハンドラーを追加 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, 、プロジェクト項目の名前が変更されるたびに発生します。  
  
    ```c#  
    public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
    {  
        output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
             oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
    }  
    ```  
  
7.  階層のイベントにサインアップします。 個別に追跡しているすべてのプロジェクトにサインアップする必要があります。 次のコードを追加 `ShowMessageBox`, 、共有プロジェクトと他のプラットフォーム プロジェクトのいずれかのいずれかです。  
  
    ```c#  
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
  
8.  DTE プロジェクト項目のイベントにサインアップ <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>します。 2 つ目のリスナーをフックした後は、次のコードを追加します。  
  
    ```c#  
    // hook up DTE events for project items  
    Events2 dteEvents = (Events2)dte.Events;  
    dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  
  
    ```  
  
9. 共有項目を変更します。 プラットフォーム プロジェクトの共有項目を変更することはできません。代わりに、これらのアイテムの実際の所有者である共有プロジェクトでそれらを変更する必要があります。 共有プロジェクトに対応する項目の ID を取得できます <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, 、共有アイテムの完全なパスを付けます。 共有項目を変更します。 プラットフォーム プロジェクトには、変更が反映されます。  
  
    > [!IMPORTANT]
    >  プロジェクト項目が共有項目を変更する前にかどうかを探します。  
  
     次のメソッドでは、プロジェクト項目ファイルの名前を変更します。  
  
    ```c#  
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
  
10. 結局のところに他のコードでこのメソッドを呼び出す `ShowMessageBox` ファイルの共有プロジェクト内の項目の名前を変更します。 共有プロジェクト内のアイテムの完全パスを取得するコードの後に、これを挿入します。  
  
    ```c#  
    // change the file name of an item in a shared project  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));   
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));  
    this.ModifyFileNameInProject(sharedHier, fullPath);  
    ```  
  
11. プロジェクトをビルドして実行します。 移動して、実験用インスタンスで、c\# のユニバーサル ハブ アプリを作成、 **ツール** メニューをクリック **呼び出す TestUniversalProject**, 、全般的な出力ペイン内のテキストを確認します。 共有の最初の項目の名前 \(思います App.xaml ファイルである\) プロジェクトを変更する必要がありますとを確認する必要があります、 <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> イベントが発生します。 この場合は、App.xaml 名前の変更によって App.xaml.cs も名前を変更するのには後、は、4 つのイベント \(各プラットフォーム プロジェクトの 2 つ\) が表示されます。 \(DTE イベントは、共有プロジェクト内の項目を追跡しないしません\)。 2 つが表示されます <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> \(プラットフォーム プロジェクトごとに 1 つ\)、イベントがない <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> イベントです。  
  
12. プラットフォーム プロジェクトのファイル名を変更してみましょうし、取得が発生するイベントの違いを確認することができます。 次のコードを追加 `ShowMessageBox` への呼び出し後 `ModifyFileName`します。  
  
    ```c#  
    // change the file name of an item in a platform project  
    var unsharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);  
  
    var unsharedItemId = unsharedItemIds[0];  
    string unsharedPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));  
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));  
  
    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);  
    ```  
  
13. プロジェクトをビルドして実行します。 実験用インスタンスで、c\# のユニバーサル プロジェクトを作成する」に進んでください、 **ツール** メニューをクリック **呼び出す TestUniversalProject**, 、全般的な出力ペイン内のテキストを確認します。 プラットフォームのプロジェクトで、ファイルの名前を変更した後、両方を表示する必要があります、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> イベントと <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> イベントです。 変更した後、ファイルの原因となったないその他のファイルを変更して、任意の場所、プラットフォーム プロジェクト内の項目の変更は反映されないのでのみについて 1 つある各これらのイベントです。