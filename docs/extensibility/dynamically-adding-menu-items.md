---
title: "動的メニュー項目の追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1eaa8cc41e7b27d509e68d6785c34a9ae214ffd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dynamically-adding-menu-items"></a>メニュー項目を動的に追加します。
指定して実行時にメニュー項目を追加することができます、`DynamicItemStart`コマンドを処理および表示するアイテムには (コード) メニューの数を定義し、Visual Studio コマンド テーブル (.vsct) ファイルでプレース ホルダー ボタンの定義をフラグをコマンドします。 VSPackage が読み込まれるときに、プレース ホルダーは、動的メニュー項目に置き換えられます。  
  
 Visual Studio での動的なリストを使用して、**最近使用した**(MRU) の一覧は、最後に開かれたドキュメントの名前を表示するには、および**Windows**一覧で、windows の名前を表示現在開いています。   `DynamicItemStart`コマンド定義にフラグは、VSPackage が開かれるまでは、セルのコマンドは、プレース ホルダーを指定します。 VSPackage が開かれたときに、プレース ホルダーは、0 またはが実行時に作成され、動的な一覧に追加できるコマンドの詳細に置き換えられます。 ことができますに VSPackage が開かれるまで、動的な一覧が表示されるメニューの位置を参照しないでください。  動的な一覧を表示するには、Visual Studio は、VSPackage が最初の文字は、プレース ホルダーの ID と同じ ID を使用してコマンドを確認するように依頼します。 Visual Studio には、対応するコマンドが検出されると、ときに、動的な一覧にコマンドの名前を追加します。 ID をインクリメントし、なくなる動的コマンドまで、動的な一覧に追加するもう 1 つの一致するコマンドを検索します。  
  
 このチュートリアルで、コマンドを使用して Visual Studio ソリューションのスタートアップ プロジェクトを設定する方法を示しています、**ソリューション エクスプ ローラー**ツールバー。 アクティブなソリューションにプロジェクトの動的なドロップダウン リストを持つメニュー コント ローラーを使用します。 このコマンドがソリューションがない場合に表示されることを防止するが開いているか、ソリューションに複数のプロジェクトがある場合にのみ、VSPackage が読み込まれる、開いているソリューションに 1 つしかプロジェクトがある場合。  
  
 .Vsct ファイルの詳細については、次を参照してください。 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)です。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して、拡張機能の作成  
  
1.  という名前の VSIX プロジェクトを作成する`DynamicMenuItems`です。  
  
2.  プロジェクトを開いたら、カスタム コマンド項目テンプレートを追加し、名前を付けます**DynamicMenu**です。 詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>.Vsct ファイル内の要素の設定  
 ツールバーにある動的メニュー項目にメニュー コント ローラーを作成するには、次の要素を指定します。  
  
-   グループ メニュー コント ローラーを含んでいると、ドロップダウン リストでメニュー項目を含む 2 つをコマンドします。  
  
-   型の要素を 1 つのメニュー`MenuController`  
  
-   2 つのボタン、アイコン、ツールバーのツール ヒントを提供するメニュー項目と別のプレース ホルダーとして機能する 1 つです。  
  
1.  DynamicMenuPackage.vsct では、コマンド Id を定義します。 シンボル セクションに移動して、IDSymbol の要素を交換して、 **guidDynamicMenuPackageCmdSet** GuidSymbol ブロックします。 2 つのグループ、メニュー コント ローラー、プレース ホルダー コマンドおよびアンカー コマンドの IDSymbol 要素を定義する必要があります。  
  
    ```csharp  
    <GuidSymbol name="guidDynamicMenuPackageCmdSet" value="{ your GUID here }">  
        <IDSymbol name="MyToolbarItemGroup" value="0x1020" />  
        <IDSymbol name="MyMenuControllerGroup" value="0x1025" />  
        <IDSymbol name="MyMenuController" value ="0x1030"/>  
        <IDSymbol name="cmdidMyAnchorCommand" value="0x0103" />  
        <!-- NOTE: The following command expands at run time to some number of ids.  
         Try not to place command ids after it (e.g. 0x0105, 0x0106).  
         If you must add a command id after it, make the gap very large (e.g. 0x200) -->  
        <IDSymbol name="cmdidMyDynamicStartCommand" value="0x0104" />  
    </GuidSymbol>    
    ```  
  
2.  グループ セクションで、既存のグループを削除し、定義した 2 つのグループを追加します。  
  
    ```  
    <Groups>  
        <!-- The group that adds the MenuController on the Solution Explorer toolbar.   
             The 0x4000 priority adds this group after the group that contains the  
             Preview Selected Items button, which is normally at the far right of the toolbar. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" priority="0x4000" >  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN" />  
        </Group>  
        <!-- The group for the items on the MenuController drop-down. It is added to the MenuController submenu. -->  
        <Group guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" priority="0x4000" >  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" />  
        </Group>  
    </Groups>  
    ```  
  
     MenuController を追加します。 常に表示されていないために、DynamicVisibility コマンド フラグを設定します。 ButtonText は表示されません。  
  
    ```  
    <Menus>  
        <!-- The MenuController to display on the Solution Explorer toolbar.  
             Place it in the ToolbarItemGroup.-->  
        <Menu guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" priority="0x1000" type="MenuController">  
            <Parent guid="guidDynamicMenuPackageCmdSet" id="MyToolbarItemGroup" />  
            <CommandFlag>DynamicVisibility</CommandFlag>  
            <Strings>  
               <ButtonText></ButtonText>  
           </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
3.  MenuController の動的メニュー項目のプレース ホルダーとして 1 つ使用し、もう一方のアンカーを使用する、2 つのボタンを追加します。  
  
     プレース ホルダーのボタンの親は、 **MyMenuControllerGroup**です。 DynamicItemStart、DynamicVisibility を追加し、プレース ホルダー ボタンに TextChanges コマンド フラグを設定します。 ButtonText は表示されません。  
  
     アンカー ボタンは、アイコンとツールヒントのテキストを保持します。 アンカー ボタンの親はまた、 **MyMenuControllerGroup**です。 メニュー コント ローラーのドロップダウンで、ボタンが表示されない実際にかどうかを確認する NoShowOnMenuController コマンド フラグおよび永続的なアンカーを FixMenuController コマンド フラグを追加します。  
  
    ```  
    <!-- The placeholder for the dynamic items that expand to N items at runtime. -->  
    <Buttons>  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyDynamicStartCommand" priority="0x1000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <CommandFlag>DynamicItemStart</CommandFlag>  
          <CommandFlag>DynamicVisibility</CommandFlag>  
          <CommandFlag>TextChanges</CommandFlag>  
          <!-- This text does not appear. -->  
          <Strings>  
            <ButtonText>Project</ButtonText>  
          </Strings>  
        </Button>  
  
        <!-- The anchor item to supply the icon/tooltip for the MenuController -->  
        <Button guid="guidDynamicMenuPackageCmdSet" id="cmdidMyAnchorCommand" priority="0x0000" >  
          <Parent guid="guidDynamicMenuPackageCmdSet" id="MyMenuControllerGroup" />  
          <!-- This is the icon that appears on the Solution Explorer toolbar. -->  
          <Icon guid="guidImages" id="bmpPicArrows"/>  
          <!-- Do not show on the menu controller's drop down list-->  
          <CommandFlag>NoShowOnMenuController</CommandFlag>  
          <!-- Become the permanent anchor item for the menu controller -->  
          <CommandFlag>FixMenuController</CommandFlag>  
          <!-- The text that appears in the tooltip.-->  
          <Strings>  
            <ButtonText>Set Startup Project</ButtonText>  
          </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
4.  (フォルダーにあるリソース)、プロジェクトにアイコンを追加し、.vsct ファイルでへの参照を追加します。 このチュートリアルでは、プロジェクト テンプレートに含まれている矢印アイコンを使用します。  
  
5.  Commands セクションで、シンボルのセクションの直前に外部 VisibilityConstraints セクションを追加します。 (シンボルの後に追加する場合、警告を get に可能性があります。)このセクションでは、メニュー コント ローラーが複数のプロジェクトを含むソリューションが読み込まれるときにのみが表示されることを確認します。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implementing-the-dynamic-menu-command"></a>動的メニュー コマンドの実装  
 継承する動的メニュー コマンド クラスを作成する<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>です。 この実装では、コンス トラクターは、コマンドの照合に使用する述語を指定します。 オーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>設定にこの述語を使用する方法、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>プロパティで、呼び出されるコマンドを識別します。  
  
1.  新しい c# クラス ファイル DynamicItemMenuCommand.cs、という名前を作成し、という名前のクラスを追加**DynamicItemMenuCommand**から継承する<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```csharp  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  次の追加ステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  一致する述語を格納するためのプライベート フィールドを追加します。  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  継承するコンス トラクターを追加、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>コンス トラクター、コマンド ハンドラーを指定し、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>ハンドラー。 コマンドに一致するための述語を追加します。  
  
    ```csharp  
    public DynamicItemMenuCommand(CommandID rootId, Predicate<int> matches, EventHandler invokeHandler, EventHandler beforeQueryStatusHandler)  
        : base(invokeHandler, null /*changeHandler*/, beforeQueryStatusHandler, rootId)  
    {  
        if (matches == null)  
        {  
            throw new ArgumentNullException("matches");  
        }  
  
        this.matches = matches;  
    }  
    ```  
  
5.  上書き、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>述語とセット一致呼び出すためのメソッド、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>プロパティ。  
  
    ```csharp  
    public override bool DynamicItemMatch(int cmdId)  
    {  
        // Call the supplied predicate to test whether the given cmdId is a match.  
        // If it is, store the command id in MatchedCommandid   
        // for use by any BeforeQueryStatus handlers, and then return that it is a match.  
        // Otherwise clear any previously stored matched cmdId and return that it is not a match.  
        if (this.matches(cmdId))  
        {  
            this.MatchedCommandId = cmdId;  
            return true;  
        }  
  
        this.MatchedCommandId = 0;  
        return false;  
    }  
    ```  
  
## <a name="adding-the-command"></a>コマンドを追加します。  
 DynamicMenu コンス トラクターは、動的メニューおよびメニュー項目を含む、メニュー コマンドを設定するためです。  
  
1.  DynamicMenuPackageGuids.cs、コマンド セットの GUID とコマンド ID を追加します。  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  次のコードを追加、DynamicMenu.cs ファイルでステートメントを使用します。  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  DynamicMenu クラスでは、プライベート フィールドを追加する**dte2**です。  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  プライベート rootItemId フィールドを追加します。  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  DynamicMenu コンス トラクターでは、メニュー コマンドを追加します。 次のセクションでは、コマンド ハンドラーを定義してあります、 `BeforeQueryStatus` 、イベント ハンドラーと一致する述語。  
  
    ```csharp  
    private DynamicMenu(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            // Add the DynamicItemMenuCommand for the expansion of the root item into N items at run time.   
            CommandID dynamicItemRootId = new CommandID(new Guid(DynamicMenuPackageGuids.guidDynamicMenuPackageCmdSet), (int)DynamicMenuPackageGuids.cmdidMyCommand);  
            DynamicItemMenuCommand dynamicMenuCommand = new DynamicItemMenuCommand(dynamicItemRootId,  
                IsValidDynamicItem,  
                OnInvokedDynamicItem,  
                OnBeforeQueryStatusDynamicItem);  
                commandService.AddCommand(dynamicMenuCommand);  
                }  
  
        dte2 = (DTE2)this.ServiceProvider.GetService(typeof(DTE));  
    }  
    ```  
  
## <a name="implementing-the-handlers"></a>ハンドラーを実装します。  
 メニュー コント ローラーで動的メニュー項目を実装するには、動的アイテムがクリックされたときにコマンドを処理する必要があります。 メニュー項目の状態を設定するロジックを実装することも必要があります。 DynamicMenu クラスにハンドラーを追加します。  
  
1.  実装する、**スタートアップ プロジェクトとして設定**コマンドを追加、 **OnInvokedDynamicItem**イベント ハンドラー。 呼び出されてとでその絶対パスを設定して、スタートアップ プロジェクトとして設定されたコマンドのテキストと同じ名前のプロジェクトの検索、<xref:EnvDTE.SolutionBuild.StartupProjects%2A>プロパティです。  
  
    ```csharp  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don't need to do anything  
        if (invokedCommand.Checked)  
            return;  
  
        // Find the project that corresponds to the command text and set it as the startup project  
        var projects = dte2.Solution.Projects;  
        foreach (Project proj in projects)  
        {  
            if (invokedCommand.Text.Equals(proj.Name))  
            {  
                dte2.Solution.SolutionBuild.StartupProjects = proj.FullName;  
                return;  
            }  
        }  
    }  
    ```  
  
2.  追加、`OnBeforeQueryStatusDynamicItem`イベント ハンドラー。 これは、前に呼び出されるハンドラー、`QueryStatus`イベント。 メニュー項目を「現実の」アイテム、つまり、プレース ホルダー アイテムではなくであるかどうかを判定するかどうか、項目は既にチェックされて (つまり、プロジェクトがスタートアップ プロジェクトとしてを既に設定されている) とします。  
  
    ```csharp  
    private void OnBeforeQueryStatusDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand matchedCommand = (DynamicItemMenuCommand)sender;  
        matchedCommand.Enabled = true;  
        matchedCommand.Visible = true;  
  
        // Find out whether the command ID is 0, which is the ID of the root item.  
        // If it is the root item, it matches the constructed DynamicItemMenuCommand,  
         // and IsValidDynamicItem won't be called.  
        bool isRootItem = (matchedCommand.MatchedCommandId == 0);  
  
        // The index is set to 1 rather than 0 because the Solution.Projects collection is 1-based.  
        int indexForDisplay = (isRootItem ? 1 : (matchedCommand.MatchedCommandId - (int) DynamicMenuPackageGuids.cmdidMyCommand) + 1);  
  
        matchedCommand.Text = dte2.Solution.Projects.Item(indexForDisplay).Name;  
  
        Array startupProjects = (Array)dte2.Solution.SolutionBuild.StartupProjects;  
        string startupProject = System.IO.Path.GetFileNameWithoutExtension((string)startupProjects.GetValue(0));  
  
        // Check the command if it isn't checked already selected  
        matchedCommand.Checked = (matchedCommand.Text == startupProject);  
  
        // Clear the ID because we are done with this item.  
        matchedCommand.MatchedCommandId = 0;  
    }  
    ```  
  
## <a name="implementing-the-command-id-match-predicate"></a>コマンド ID の一致する述語を実装します。  
  
1.  一致する述語を実装するようになりました。 2 つのことを確認する必要があります: 最初に、かどうかのコマンド ID が有効では (より大きいか、宣言されたコマンド ID に等しい) であると、2 番目 (これは、ソリューション内のプロジェクトの数より小さい) 可能なプロジェクトを指定するかどうか。  
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="setting-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>ソリューションに複数のプロジェクトがある場合にのみをロードする VSPackage の設定  
 **スタートアップ プロジェクトとして設定**コマンドは、アクティブなソリューションには、複数のプロジェクトが含まれていない限り、意味がないため、そのケースでのみの自動読み込みを VSPackage に設定することができます。 使用する<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI コンテキストと共に<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>です。 DynamicMenuPackage.cs ファイルでは、DynamicMenuPackage クラスに次の属性を追加します。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="testing-the-set-startup-project-command"></a>スタートアップ プロジェクトとして設定コマンドのテスト  
 これで、コードをテストできます。  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  実験用インスタンスの複数のプロジェクトが含まれるソリューションを開きます。  
  
     ある矢印アイコンが表示されます、**ソリューション エクスプ ローラー**ツールバー。 を展開すると、ソリューション内の別のプロジェクトを表すメニュー項目が表示されます。  
  
3.  プロジェクトのいずれかをチェックするときに、スタートアップ プロジェクトになります。  
  
4.  ソリューションを閉じますか、または 1 つしかプロジェクトが含まれるソリューションを開くと、ツールバーのアイコンが表示されなくなります。  
  
## <a name="see-also"></a>参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [VSPackage でユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)