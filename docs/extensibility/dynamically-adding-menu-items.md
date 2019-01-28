---
title: 動的メニュー項目の追加 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DYNAMICITEMSTART
- menu items, adding dynamically
- menus, adding dynamic items
ms.assetid: d281e9c9-b289-4d64-8d0a-094bac6c333c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee9f56af0d04daab20c14bf4fff7a8241dd9f01c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55022782"
---
# <a name="dynamically-add-menu-items"></a>メニュー項目を動的に追加します。
実行時に指定して、メニュー項目を追加することができます、`DynamicItemStart`コマンド フラグを Visual Studio コマンド テーブルのプレース ホルダー ボタンの定義 (*.vsct*) ファイル、し (コード) で表示するメニュー項目の数を定義してコマンドを処理します。 VSPackage が読み込まれるときに、プレース ホルダーは動的メニュー項目に置き換えられます。  
  
 Visual Studio での動的リストを使用して、**最近使用した**(MRU) の一覧は、最近開かれたドキュメントの名前を表示するには、および**Windows**一覧で、windows の名前を表示します現在開かれています。   `DynamicItemStart`コマンド定義のフラグは、コマンドは、VSPackage が開かれるまでのプレース ホルダーを指定します。 VSPackage が開かれたときに、プレース ホルダーは、0 または実行時に作成され、動的な一覧に追加されるその他のコマンドに置き換えられます。 VSPackage が開かれるまで、動的な一覧が表示されるメニューの位置を表示することはできません。  Visual Studio を動的リストを設定するには、最初の文字は、プレース ホルダーの ID と同じ ID を持つコマンドを検索する VSPackage を確認します。 Visual Studio には、一致するコマンドが検出されると、コマンドの名前を動的な一覧に追加します。 次に、ID をインクリメントし、以上ない動的なコマンドがあるまで、動的な一覧に追加するもう 1 つの一致するコマンドを探します。  
  
 このチュートリアルでコマンドを使用して Visual Studio ソリューションのスタートアップ プロジェクトを設定する方法を示しています、**ソリューション エクスプ ローラー**ツールバー。 アクティブなソリューションで、プロジェクトの動的なドロップダウン リストを持つメニュー コント ローラーを使用します。 ソリューションがない場合にこのコマンドを保持するが開いてまたはソリューションに複数のプロジェクトがある場合にのみ、開いているソリューションに 1 つしかプロジェクトがある場合、VSPackage が読み込まれます。  
  
 詳細については *.vsct*ファイルを参照してください[Visual Studio コマンド テーブル (.vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
## <a name="create-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して拡張機能を作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`DynamicMenuItems`します。  
  
2.  カスタム コマンドの項目テンプレートを追加し、名前、プロジェクトが開いたら、 **DynamicMenu**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="setting-up-the-elements-in-the-vsct-file"></a>内の要素の設定、 *.vsct*ファイル  
 ツールバーにある動的メニュー項目にメニュー コント ローラーを作成するには、次の要素を指定します。  
  
-   2 つのコマンド グループ、メニュー コント ローラーが含まれていると、ドロップダウン リストでのメニュー項目を含む別  
  
-   型の要素を 1 つのメニュー `MenuController`  
  
-   2 つのボタン、アイコンとツールバーのヒントを提供する別のメニュー項目のプレース ホルダーとして機能する 1 つ。  
  
1.  *DynamicMenuPackage.vsct*コマンドの Id を定義します。 Symbols セクションに移動し、IDSymbol 要素を交換して、 **guidDynamicMenuPackageCmdSet** GuidSymbol ブロックします。 2 つのグループ、メニュー コント ローラー、プレース ホルダーのコマンドおよびアンカー コマンドの IDSymbol 要素を定義する必要があります。  
  
    ```xml  
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
  
2.  Groups セクションで、既存のグループを削除し、定義した 2 つのグループを追加します。  
  
    ```xml  
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
  
     MenuController を追加します。 常に表示されていないため、DynamicVisibility コマンド フラグを設定します。 ButtonText は表示されません。  
  
    ```xml  
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
  
3.  MenuController の動的メニュー項目のプレース ホルダーとしてとアンカーとしての 2 つのボタンを追加します。  
  
     プレース ホルダーのボタンの親は、 **MyMenuControllerGroup**します。 DynamicItemStart、DynamicVisibility を追加し、プレース ホルダーのボタンに TextChanges コマンド フラグを設定します。 ButtonText は表示されません。  
  
     アンカーのボタンは、アイコン、およびツールヒントのテキストを保持します。 アンカーのボタンの親はまた、 **MyMenuControllerGroup**します。 ボタンがメニュー コント ローラーのドロップダウンで、実際に表示されないかどうかを確認する NoShowOnMenuController コマンド フラグと永続的なアンカーに FixMenuController コマンド フラグを追加するとします。  
  
    ```xml  
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
  
4.  アイコンをプロジェクトに追加 (で、*リソース*フォルダー) への参照を追加し、 *.vsct*ファイル。 このチュートリアルでは、プロジェクト テンプレートに含まれている矢印アイコンを使用します。  
  
5.  直前の Symbols セクションにコマンドのセクションの外部 VisibilityConstraints セクションを追加します。 (シンボルの後に追加する場合、警告を get に可能性があります。)このセクションでは、メニュー コント ローラーは、複数のプロジェクトを含むソリューションが読み込まれるときにのみが表示されることを確認します。  
  
    ```xml  
    <VisibilityConstraints>  
         <!--Make the MenuController show up only when there is a solution with more than one project loaded-->  
        <VisibilityItem guid="guidDynamicMenuPackageCmdSet" id="MyMenuController" context="UICONTEXT_SolutionHasMultipleProjects"/>  
    </VisibilityConstraints>  
    ```  
  
## <a name="implement-the-dynamic-menu-command"></a>動的メニュー コマンドを実装します。  
 継承する動的メニュー コマンド クラスを作成する<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>します。 この実装では、コンス トラクターは、コマンドの照合に使用する述語を指定します。 オーバーライドする必要があります、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>この述語を使用して設定するメソッド、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>プロパティで、呼び出されるコマンドを識別します。  
  
1.  新しい c# クラスという名前のファイルを作成する*DynamicItemMenuCommand.cs*、という名前のクラスを追加および**DynamicItemMenuCommand**から継承する<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>:  
  
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
  
3.  一致する述語を格納するプライベート フィールドを追加します。  
  
    ```csharp  
    private Predicate<int> matches;  
  
    ```  
  
4.  継承するコンス トラクターを追加、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand>コンス トラクターとコマンド ハンドラーを指定します、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>ハンドラー。 コマンドに一致するための述語を追加します。  
  
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
  
5.  上書き、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.DynamicItemMatch%2A>その it 述語とセットの一致では、メソッド、<xref:Microsoft.VisualStudio.Shell.OleMenuCommand.MatchedCommandId%2A>プロパティ。  
  
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
  
## <a name="add-the-command"></a>コマンドを追加します  
 DynamicMenu コンス トラクターは、動的メニューとメニュー項目を含むメニュー コマンドを設定します。  
  
1.  *DynamicMenuPackage.cs*、コマンド セットの GUID とコマンド ID を追加します。  
  
    ```csharp  
    public const string guidDynamicMenuPackageCmdSet = "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    public const uint cmdidMyCommand = 0x104;  
    ```  
  
2.  *DynamicMenu.cs*ファイルに追加し、次のステートメントを使用します。  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using System.ComponentModel.Design;  
    ```  
  
3.  `DynamicMenu`クラスにプライベート フィールドを追加**dte2**します。  
  
    ```csharp  
    private DTE2 dte2;  
    ```  
  
4.  プライベート rootItemId フィールドを追加します。  
  
    ```csharp  
    private int rootItemId = 0;  
    ```  
  
5.  DynamicMenu コンス トラクターでは、メニュー コマンドを追加します。 次のセクションでは、コマンド ハンドラーを定義します、`BeforeQueryStatus`イベント ハンドラー、および一致する述語。  
  
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
  
## <a name="implement-the-handlers"></a>ハンドラーを実装します。  
 メニュー コント ローラーで動的メニュー項目を実装するには、動的な項目がクリックされたときにコマンドを処理する必要があります。 メニュー項目の状態を設定するロジックを実装することも必要があります。 ハンドラーを追加、`DynamicMenu`クラス。  
  
1.  実装する、**スタートアップ プロジェクトに設定**コマンドを追加、 **OnInvokedDynamicItem**イベント ハンドラー。 呼び出されたでの絶対パスを設定して、スタートアップ プロジェクトとして設定するコマンドのテキストと同じ名前を持つプロジェクトを探し、<xref:EnvDTE.SolutionBuild.StartupProjects%2A>プロパティ。  
  
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
  
2.  追加、`OnBeforeQueryStatusDynamicItem`イベント ハンドラー。 これは、前に呼び出されるハンドラーを`QueryStatus`イベント。 メニュー項目には、プレース ホルダー項目ではなく、「実際の」項目があるかどうかを判断するかどうか、項目は既にチェックされている (つまり、プロジェクトがスタートアップ プロジェクトとしてを既に設定されている) とします。  
  
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
  
## <a name="implement-the-command-id-match-predicate"></a>コマンド ID の一致述部を実装します。  
  
これで、一致する述語を実装します。 2 つのことを確認する必要があります。 最初に、かどうか、コマンド ID が有効 (それが宣言されたコマンド ID 以上)、と 2 番目、かどうか (これは、ソリューション内のプロジェクトの数より小さい) 可能なプロジェクトを指定します。
  
    ```csharp  
    private bool IsValidDynamicItem(int commandId)  
    {  
        // The match is valid if the command ID is >= the id of our root dynamic start item   
        // and the command ID minus the ID of our root dynamic start item  
        // is less than or equal to the number of projects in the solution.  
        return (commandId >= (int)DynamicMenuPackageGuids.cmdidMyCommand) && ((commandId - (int)DynamicMenuPackageGuids.cmdidMyCommand) < dte2.Solution.Projects.Count);  
    }  
    ```  
  
## <a name="set-the-vspackage-to-load-only-when-a-solution-has-multiple-projects"></a>ソリューションに複数のプロジェクトがある場合にのみ読み込む VSPackage を設定します。  
 **スタートアップ プロジェクトに設定**コマンドは、アクティブなソリューションには、1 つ以上のプロジェクトが含まれていない場合、意味がないため、そのケースでのみ自動読み込みするように VSPackage を設定することができます。 使用する<xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute>UI コンテキストと共に<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids.SolutionHasMultipleProjects>します。 *DynamicMenuPackage.cs*ファイル DynamicMenuPackage クラスに次の属性を追加します。  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
[ProvideMenuResource("Menus.ctmenu", 1)]  
[ProvideAutoLoad(UIContextGuids.SolutionHasMultipleProjects)]  
[Guid(DynamicMenuPackage.PackageGuidString)]  
public sealed class DynamicMenuItemsPackage : Package  
{}  
```  
  
## <a name="test-the-set-startup-project-command"></a>テスト セットのスタートアップ プロジェクト コマンド  
 これで、コードをテストできます。  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  実験用インスタンスでは、1 つ以上のプロジェクトを含むソリューションを開きます。  
  
     矢印アイコンを表示する必要があります、**ソリューション エクスプ ローラー**ツールバー。 を展開すると、ソリューション内の別のプロジェクトを表すメニュー項目が表示されます。  
  
3.  プロジェクトのいずれかをチェックすると、スタートアップ プロジェクトになります。  
  
4.  ソリューションを閉じますか、または 1 つしかプロジェクトが含まれるソリューションを開くと、ツール バー アイコンが表示されなくなります。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Vspackage がユーザー インターフェイス要素を追加する方法](../extensibility/internals/how-vspackages-add-user-interface-elements.md)