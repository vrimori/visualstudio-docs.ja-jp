---
title: ユニバーサル Windows プロジェクトの管理 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06bfb109ce58ee822a32bc3a92d7e6e45578fb05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55005506"
---
# <a name="manage-universal-windows-projects"></a>ユニバーサル Windows プロジェクトを管理します。
ユニバーサル Windows アプリは、Windows 8.1 と Windows Phone 8.1、両方のプラットフォームでコードとその他のアセットを使用する開発者の両方を対象とするアプリです。 共有コードとリソースは、プラットフォーム固有のコードとリソースは個別のプロジェクト、その他の Windows Phone および Windows のいずれかの保持中に、共有プロジェクトに保持されます。 ユニバーサル Windows アプリの詳細については、次を参照してください。[ユニバーサル Windows アプリ](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx)します。 プロジェクトを管理する、visual Studio 拡張機能があります単一プラットフォームのアプリとは異なる構造をユニバーサル Windows アプリ プロジェクトがあることに注意してくださかった。 このチュートリアルでは、共有プロジェクトを移動し、共有のアイテムを管理する方法を示します。  

## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  

### <a name="navigate-the-shared-project"></a>共有プロジェクトを移動します。  

1.  という名前の c# VSIX プロジェクトを作成する**TestUniversalProject**します。 (**ファイル** > **新しい** > **プロジェクト**し**c#**  >  **機能拡張** > **Visual Studio パッケージ**)。 追加、**カスタム コマンド**プロジェクト項目テンプレート (上、**ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加** > **新しい項目**に移動し、**拡張**)。 ファイルに名前を**TestUniversalProject**します。  

2.  参照を追加*Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll*と*Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (で、 **拡張機能**セクション)。  

3.  開いている*TestUniversalProject.cs*し、以下の追加`using`ステートメント。  

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

4.  `TestUniversalProject`クラスがポイントするプライベート フィールドを追加、**出力**ウィンドウ。  

    ```csharp  
    public sealed class TestUniversalProject   
    {  
        IVsOutputWindowPane output;  
    . . .  
    }  
    ```  

5.  TestUniversalProject コンス トラクター内で出力ウィンドウへの参照を設定します。  

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

7.  このチュートリアルでは、複数のさまざまな目的に使用する DTE オブジェクトを取得します。 また、メニュー ボタンがクリックされたときに、ソリューションが読み込まれていることを確認してください。  

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

8.  共有プロジェクトを検索します。 共有プロジェクトは、純粋なコンテナーです。出力を生成またはビルドにしません。 次のメソッドを探すことによって、ソリューションの最初の共有プロジェクトを検索します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>共有プロジェクトの機能を持つオブジェクト。  

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

9. `ShowMessageBox`メソッド、キャプションの出力 (プロジェクト名に表示される、**ソリューション エクスプ ローラー**)、共有プロジェクトの。  

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

10. アクティブなプラットフォーム プロジェクトを取得します。 プラットフォームのプロジェクトとは、プラットフォーム固有のコードとリソースが含まれているプロジェクトです。 次のメソッドは、新しいフィールドを使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>アクティブ プラットフォーム プロジェクトを取得します。  

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

11. `ShowMessageBox`メソッドが、アクティブなプラットフォーム プロジェクトのキャプションを出力します。  

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

12. プラットフォームのプロジェクトを反復処理します。 次のメソッドは、共有プロジェクトからインポート (プラットフォーム) のすべてのプロジェクトを取得します。  

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
    >  ユーザーが実験用インスタンスで C++ ユニバーサル Windows アプリ プロジェクトを開き、上記のコードは例外をスローします。 これは既知の問題です。 例外を避けるためには、置換、`foreach`上、次のブロックします。  

    ```csharp  
    var importingProjects = sharedAssetsProject.EnumImportingProjects();  
    for (int i = 0; i < importingProjects.Count; ++i)  
    {  
        yield return importingProjects[i];  
    }   
    ```  

13. `ShowMessageBox`メソッドは、各プラットフォーム プロジェクトのキャプションを出力します。 アクティブなプラットフォーム プロジェクトのキャプションを出力する行の後に、次のコードを挿入します。 この一覧に読み込まれるプラットフォーム プロジェクトのみが表示されます。  

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

14. アクティブなプラットフォーム プロジェクトを変更します。 次のメソッドの設定を使用して、アクティブなプロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>します。  

    ```csharp  
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)  
    {  
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);  
    }  
    ```  

15. `ShowMessageBox`メソッドでは、アクティブなプラットフォーム プロジェクトを変更します。 このコードを挿入、`foreach`ブロックします。  

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

16. 試してみましょう。F5 キーを押して、実験用インスタンスを起動します。 実験用インスタンスでの c# ユニバーサル ハブ アプリ プロジェクトの作成 (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual c#** > **Windows**  >  **Windows 8** > **ユニバーサル** > **ハブ アプリ**)。 ソリューションが読み込まれた後に移動して、**ツール**メニューをクリックします**呼び出す TestUniversalProject**、およびチェックインし、テキスト、**出力**ウィンドウ。 次のように表示されます。  

    ```  
    Found shared project: HubApp.Shared  
    The active platform project: HubApp.Windows  
    Platform projects:  
     * HubApp.Windows  
     * HubApp.WindowsPhone  
    set active project: HubApp.WindowsPhone  
    ```  

### <a name="manage-the-shared-items-in-the-platform-project"></a>共有プラットフォーム プロジェクト アイテムを管理します。  

1.  プラットフォームのプロジェクト共有項目を検索します。 共有プロジェクト内の項目が、プラットフォーム プロジェクトに共有項目として表示されます。 表示することはできません、**ソリューション エクスプ ローラー**を検索して、プロジェクト階層を移動することができますが、します。 次のメソッドは、階層について説明し、共有のすべての項目を収集します。 必要に応じて、各項目のキャプションを出力します。 共有アイテムは、新しいプロパティで識別される<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7>します。  

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

2.  `ShowMessageBox`メソッドでは、次のコードをプラットフォームのプロジェクト階層アイテムの説明を追加します。 内で挿入、`foreach`ブロックします。  

    ```csharp  
    output.OutputStringThreadSafe("Walk the active platform project:\n");  
    var sharedItemIds = new List<uint>();  
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);  
    ```  

3.  共有項目を読み取ります。 共有項目が非表示のリンクされたファイルとして、プラットフォーム プロジェクトに表示され、通常のリンクされたファイルとしてのすべてのプロパティを読み取ることができます。 次のコードでは、共有の最初の項目の完全なパスを読み取ります。  

    ```csharp  
    var sharedItemId = sharedItemIds[0];  
    string fullPath;  
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));  
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));  
    ```  

4.  試してみましょう。キーを押して**F5**実験用インスタンスを起動します。 作成、C#実験用インスタンスで、ハブのユニバーサル アプリ プロジェクト (で、**新しいプロジェクト**ダイアログ ボックスで、 **Visual C#**   >  **Windows**  > **Windows 8** > **ユニバーサル** > **ハブ アプリ**) に移動して、**ツール**メニューをクリックします。**呼び出す TestUniversalProject**でテキストを確認し、**出力**ウィンドウ。 次のように表示されます。  

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>プラットフォームのプロジェクトと共有プロジェクトに変更を検出します。  

1. プラットフォームのプロジェクトの場合と同様、共有プロジェクトでの変更を検出するために階層し、プロジェクトのイベントを使用できます。 ただし、共有プロジェクト内のプロジェクト項目は表示されません、つまり、共有プロジェクトの項目が変更されたときに特定のイベントは起動されません。  

    プロジェクト内のファイルの名前が変更イベントの順序を考慮してください。  

   1. ディスクでは、ファイル名が変更されました。  

   2. ファイルの新しい名前を含めるには、プロジェクト ファイルが更新されます。  

      階層のイベント (たとえば、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) ように、UI に表示される変更の追跡を一般に、**ソリューション エクスプ ローラー**します。 階層のイベントは、ファイルの削除し、ファイルに追加で構成されるファイルの名前の変更操作を検討してください。 ただし、非表示の項目が変更されると、階層イベント システムが発生する<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>イベントがない、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベント。 そのため、プラットフォーム プロジェクト内のファイルの名前を変更する場合、取得両方<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>と<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>、取得のみ共有プロジェクト内のファイルの名前を変更する場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>します。  

      プロジェクト項目の変更を追跡するには、DTE プロジェクト項目のイベントを処理することができます (ものがある<xref:EnvDTE.ProjectItemsEventsClass>)。 ただし、多数のイベントを処理する場合でイベントの処理パフォーマンスの向上を入手できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>します。 このチュートリアルでは、DTE イベントと階層のイベントのみを説明します。 この手順では、共有プロジェクトとプラットフォーム プロジェクトにイベント リスナーを追加します。 次に、共有プロジェクトで 1 つのファイルとプラットフォーム プロジェクトに別のファイルの名前を変更するときに、各名前の変更操作に対して発生するイベントを確認できます。  

      この手順では、共有プロジェクトとプラットフォーム プロジェクトにイベント リスナーを追加します。 次に、共有プロジェクトで 1 つのファイルとプラットフォーム プロジェクトに別のファイルの名前を変更するときに、各名前の変更操作に対して発生するイベントを確認できます。  

2. イベント リスナーを追加します。 プロジェクトに新しいクラス ファイルを追加し、付けます*HierarchyEventListener.cs*します。  

3. 開く、 *HierarchyEventListener.cs*ファイルを開き、次を追加するステートメントを使用します。  

   ```csharp  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio;  
   using System.IO;  

   ```  

4. `HierarchyEventListener`クラス実装<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:  

   ```csharp  
   class HierarchyEventListener : IVsHierarchyEvents  
   { }  

   ```  

5. メンバーを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>次のコードのようにします。  

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

6. 同じクラスには、DTE イベントの別のイベント ハンドラーを追加<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>、プロジェクト項目の名前が変更されるたびに発生します。  

   ```csharp  
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)  
   {  
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",  
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));  
   }  
   ```  

7. 階層のイベントにサインアップします。 個別に追跡しているすべてのプロジェクトにサインアップする必要があります。 次のコードを追加`ShowMessageBox`、共有のプロジェクトでは、およびその他のプラットフォーム プロジェクトの 1 つのいずれか。  

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

8. DTE プロジェクト項目のイベントにサインアップ<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>します。 2 番目のリスナーをフックした後は、次のコードを追加します。  

   ```csharp  
   // hook up DTE events for project items  
   Events2 dteEvents = (Events2)dte.Events;  
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;  

   ```  

9. 共有対象アイテムを変更します。 プラットフォーム プロジェクトで共有項目を変更することはできません。代わりに、これらの項目の実際の所有者である共有プロジェクトでそれらを変更する必要があります。 共有のプロジェクトに対応する項目の ID を取得できます<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>、共有対象アイテムの完全なパスを指定します。 共有対象アイテムを変更します。 プラットフォームのプロジェクトに反映されます。  

    > [!IMPORTANT]
    >  プロジェクト項目が変更する前に共有項目がかどうかを確認する必要があります。  

     次のメソッドは、プロジェクト アイテム ファイルの名前を変更します。  

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

11. プロジェクトをビルドして実行します。 実験用インスタンスでの c# ユニバーサル hub アプリの作成に移動、**ツール**メニューをクリックします**呼び出す TestUniversalProject**、一般的な出力ペインのテキストを確認します。 共有プロジェクトの最初の項目の名前 (予定に、 *App.xaml*ファイル) 変更する必要がありますが表示されると、<xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>イベントが発生します。 名前を変更するためここでは、 *App.xaml*により*App.xaml.cs*名前を変更すると、4 つのイベント (プラットフォーム プロジェクトごとに 2 つ) を参照する必要があります。 (DTE イベントは、共有プロジェクト内の項目を追跡しないされません)。2 つのことがわかります<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>(プラットフォーム プロジェクトごとに 1 つ)、イベントが<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベント。  

12. プラットフォームのプロジェクト内のファイルの名前を変更してみましょうし、取得を発生させたイベントの違いを確認できます。 次のコードを追加`ShowMessageBox`への呼び出し後`ModifyFileName`します。  

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

13. プロジェクトをビルドして実行します。 実験用インスタンスで c# ユニバーサル プロジェクトを作成に移動、**ツール**メニューをクリックします**呼び出す TestUniversalProject**、一般的な出力ペインのテキストを確認します。 プラットフォーム プロジェクトにファイルの名前を変更した後、両方を表示する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>イベントおよび<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>イベント。 変更した後、ファイルの原因となったなし、変更するには、その他のファイルと、プラットフォーム プロジェクト内の項目への変更を任意の場所に反映取得はありません、ため 1 つしかない各これらのイベント。
