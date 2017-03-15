---
title: "メニュー項目を動的に追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DYNAMICITEMSTART"
  - "メニュー項目を動的に追加します。"
  - "動的な項目の追加メニュー"
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
caps.latest.revision: 37
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 37
---
# メニュー項目を動的に追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

指定して実行時にメニュー項目を追加することができます、 `DynamicItemStart` コマンドでは、コマンドの処理と表示項目\] メニューの数を \(コード\) で定義しを Visual Studio コマンド テーブル \(.vsct\) ファイル内のプレース ホルダー ボタン定義に対するフラグです。 VSPackage が読み込まれるときに、プレース ホルダーが動的メニュー項目に置き換えられます。  
  
 Visual Studio での動的リストを使用、 **最近使用した** \(MRU\) の一覧は、最近開かれているドキュメントの名前を表示するには、および **Windows** 一覧で、現在開いているウィンドウの名前を表示します。`DynamicItemStart` コマンドは、VSPackage が開かれるまでプレース ホルダーをコマンド定義にフラグを指定します。 VSPackage を開いたときに、プレース ホルダーは、0 または実行時に作成および動的な一覧に追加される他のコマンドに置き換えられます。 VSPackage が開かれるまで、動的な一覧が表示されるメニューの位置を表示することはできません。 Visual Studio を動的な一覧を設定するには、コマンドの最初の文字は、プレース ホルダーの ID と同じ ID で検索する VSPackage を確認します。 Visual Studio には、対応するコマンドが検出されると、コマンドの名前を動的な一覧に追加します。 ID をインクリメントし、動的な一覧に追加して、それ以上ない動的コマンドに一致する別のコマンドを探します。  
  
 このチュートリアルでは、コマンドを使用して Visual Studio ソリューションのスタートアップ プロジェクトに設定する方法、 **ソリューション エクスプ ローラー** ツールバーです。 アクティブなソリューションで、プロジェクトの動的なドロップダウン リストを持つメニュー コント ローラーを使用します。 このコマンドがソリューションがないときに表示されることを防止するが開いているか、ソリューションに複数のプロジェクトがある場合にのみ VSPackage が読み込まれる、開いているソリューションに 1 つしかプロジェクトがある場合。  
  
 .Vsct ファイルの詳細については、次を参照してください。 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
## メニュー コマンドを使用して拡張機能の作成  
  
1.  という名前の VSIX プロジェクトを作成する `DynamicMenuItems`です。  
  
2.  カスタム コマンド項目テンプレートを追加し、名前のプロジェクトを開いたら、 **DynamicMenu**します。 詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
## .Vsct ファイル内の要素の設定  
 ツールバーにある動的メニュー項目を含む\] メニューの \[コント ローラーを作成するには、次の要素を指定します。  
  
-   2 つのコマンドのグループ\] メニューの \[コント ローラーを含む 1 つをドロップダウン リストでのメニュー項目が含まれています  
  
-   型の 1 つの menu 要素 `MenuController`  
  
-   2 つのボタン、アイコンおよびツールバーのツール ヒントを提供するメニュー項目と別のプレース ホルダーとして機能する 1 つです。  
  
1.  DynamicMenuPackage.vsct では、コマンド Id を定義します。 Symbols セクションに移動し、IDSymbol の要素を置き換える、 **guidDynamicMenuPackageCmdSet** GuidSymbol ブロックします。 2 つのグループや\] メニューの \[コント ローラー、プレース ホルダー コマンド アンカー コマンド IDSymbol 要素を定義する必要があります。  
  
    ```c#  
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
  
2.  Groups\] セクションでは、既存のグループを削除し、定義した 2 つのグループを追加します。  
  
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
  
     MenuController を追加します。 常に表示されていないため、DynamicVisibility コマンド フラグを設定します。 アドインは表示されません。  
  
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
  
3.  MenuController の動的メニュー項目のプレース ホルダーとして、アンカーとしての 2 つのボタンを追加します。  
  
     プレース ホルダーのボタンの親は、 **MyMenuControllerGroup**します。 プレース ホルダーのボタンに DynamicItemStart、DynamicVisibility、および \[テキスト コマンドのフラグを追加します。 アドインは表示されません。  
  
     アンカー ボタンは、アイコンとツールヒントのテキストを保持します。 アンカー ボタンの親でも、 **MyMenuControllerGroup**します。 メニュー コント ローラーのドロップダウン ボタンが表示されない実際に確認する NoShowOnMenuController コマンド フラグと永続的なアンカーに FixMenuController コマンド フラグを追加します。  
  
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
  
4.  \(フォルダーにあるリソース\)、プロジェクトにアイコンを追加し、.vsct ファイルへの参照を追加します。 このチュートリアルでは、プロジェクト テンプレートに含まれている矢印アイコンを使用します。  
  
5.  Symbols セクションの直前のコマンド セクションの外側で VisibilityConstraints セクションを追加します。 \(シンボルの後に追加する場合、警告を表示に可能性があります。\) このセクションでは\] メニューの \[コント ローラーが複数のプロジェクトを含むソリューションが読み込まれるときにのみ表示されていることを確認します。  
  
    ```  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## 動的メニュー コマンドの実装  
 動的メニュー コマンド クラスから継承を作成する <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>です。 この実装では、コンス トラクターは、コマンドの照合に使用する述語を指定します。 オーバーライドする必要があります、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> この述語を使用して設定する方法、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> プロパティで、呼び出されるコマンドを指定します。  
  
1.  新しい c\# クラスという名前のファイル、DynamicItemMenuCommand.cs を作成し、という名前のクラスを追加 **DynamicItemMenuCommand** から継承する <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
    ```c#  
    class DynamicItemMenuCommand : OleMenuCommand  
    {  
  
    }  
  
    ```  
  
2.  次の追加のステートメントを使用します。  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using System.ComponentModel.Design;  
    ```  
  
3.  一致する述語を格納するプライベート フィールドを追加します。  
  
    ```c#  
    private Predicate<int> matches;  
  
    ```  
  
4.  継承されたコンス トラクターを追加、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> コンス トラクター コマンド ハンドラーを指定し、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> ハンドラー。 コマンドに一致する述語を追加します。  
  
    ```c#  
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
  
5.  オーバーライド、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A> メソッド it が述語とセットの一致項目を呼び出して、 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A> プロパティ。  
  
    ```c#  
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
  
## コマンドを追加します。  
 DynamicMenu コンス トラクターは、メニュー コマンド、動的メニューおよびメニュー項目を設定する場所です。  
  
1.  DynamicMenuPackageGuids.cs、コマンド セットの GUID とコマンド ID を追加します。  
  
    ```c#  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  DynamicMenu.cs ファイルに次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  DynamicMenu クラスでプライベート フィールドを追加 **dte2**します。  
  
    ```c#  
    private DTE2 dte2;  
    ```  
  
4.  プライベート rootItemId フィールドを追加します。  
  
    ```c#  
    private int rootItemId = 0;  
    ```  
  
5.  DynamicMenu コンス トラクターでは、メニュー コマンドを追加します。 次のセクションでは、コマンド ハンドラーを定義しましょう、 `BeforeQueryStatus` イベント ハンドラー、および一致する述語。  
  
    ```c#  
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
  
## ハンドラーを実装します。  
 メニューの \[コント ローラーで動的メニュー項目を実装するには、動的アイテムがクリックされたときにコマンドを行う必要があります。 また、メニュー項目の状態を設定するロジックを実装する必要があります。 DynamicMenu クラスに対応するハンドラーを追加します。  
  
1.  実装する、 **スタートアップ プロジェクトとして設定** コマンドを追加、 **OnInvokedDynamicItem** イベント ハンドラーです。 これが呼び出されてでその絶対パスを設定してスタートアップ プロジェクトとして設定するコマンドのテキストと同じ名前のプロジェクトの検索、 <xref:EnvDTE.SolutionBuild.StartupProjects%2A> プロパティです。  
  
    ```c#  
    private void OnInvokedDynamicItem(object sender, EventArgs args)  
    {  
        DynamicItemMenuCommand invokedCommand = (DynamicItemMenuCommand)sender;  
        // If the command is already checked, we don’t need to do anything  
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
  
2.  追加、 `OnBeforeQueryStatusDynamicItem` イベント ハンドラーです。 これは、前に呼び出されるハンドラー、 `QueryStatus` イベントです。 メニュー項目が、「実際」の項目は、プレース ホルダー アイテムではなくであるかどうかを決定するかどうか、項目が既にチェック \(つまり、プロジェクトがスタートアップ プロジェクトとして設定されて既にこと\) とします。  
  
    ```c#  
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
  
## コマンド ID の一致する述語を実装します。  
  
1.  これで、一致する述語を実装します。 2 つのことを確認する必要があります。 まず、かどうか、コマンド ID が有効 \(それが宣言されたコマンド ID 以上\)、と 2 つ目は、\(これは、ソリューションにプロジェクトの数よりも少ない\) 可能なプロジェクトを指定するかどうか。  
  
    ```c#  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## ソリューションに複数のプロジェクトがある場合にのみを読み込む VSPackage を設定します。  
 **スタートアップ プロジェクトとして設定** コマンドは、アクティブなソリューションに複数のプロジェクトが含まれていない、意味がないため、自動読み込みする場合にのみ、VSPackage を設定することができます。 使用する <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> UI コンテキストと共に <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>します。 DynamicMenuPackage.cs ファイルでは、DynamicMenuPackage クラスに次の属性を追加します。  
  
```c#  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackageGuids.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## \[スタートアップ プロジェクトに設定\] コマンドをテストします。  
 これで、コードをテストできます。  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  実験用インスタンスでは、複数のプロジェクトが含まれるソリューションを開きます。  
  
     矢印のアイコンが表示、 **ソリューション エクスプ ローラー** ツールバーです。 を展開すると、ソリューション内の別のプロジェクトを表すメニュー項目が表示されます。  
  
3.  プロジェクトのいずれかをチェックすると、スタートアップ プロジェクトになります。  
  
4.  ソリューションを閉じますか 1 つしかプロジェクトが含まれるソリューションを開くときにツール バー アイコンは表示されなくなります。  
  
## 参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)