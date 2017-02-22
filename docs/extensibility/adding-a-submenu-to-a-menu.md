---
title: "メニューのサブメニューの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンテキスト メニュー"
  - "サブメニューには、カスケード"
  - "カスケード サブメニュー"
  - "メニュー、カスケード サブメニューを作成します。"
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 43
caps.handback.revision: 43
ms.author: "gregvanl"
manager: "ghogen"
---
# メニューのサブメニューの追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルのデモに基づき [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) にサブメニューを追加する方法を表示することによって、 **TestMenu** メニュー。  
  
 サブメニューは、別のメニューに表示されるセカンダリ メニューです。 サブメニューは、その名の後の矢印で識別できます。 名前をクリックすると、サブメニュー、および表示するコマンドとします。  
  
 このチュートリアルでは、Visual Studio のメニュー バーのメニューのサブメニューを作成し、サブメニューで新しいコマンドを配置します。 このチュートリアルでは、新しいコマンドも実装します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## メニューのサブメニューの追加  
  
1.  手順に従います [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) プロジェクトとメニュー項目を作成します。 このチュートリアルの手順では、VSIX プロジェクトの名前があると仮定 `TopLevelMenu`します。  
  
2.  TestCommandPackage.vsct を開きます。`<Symbols>` セクションで、追加、 `<IDSymbol>` サブメニュー グループとすべてのコマンドのサブメニュー要素、 `<GuidSymbol>` "guidTopLevelMenuCmdSet"という名前のノード これは同じノードを含む、 `<IDSymbol>` \] メニューの最上位の要素。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  新しく作成されたサブメニューを追加、 `<Menus>` セクションです。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     親の GUID と ID のペアが生成されたメニュー グループを指定する [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), 、トップレベルのメニューの子であるとします。  
  
4.  手順 2 で定義されているメニュー グループを追加、 `<Groups>` セクションし、サブメニューの子を作成します。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  新しい `<Button>` 要素を `<Buttons>` サブメニューの項目として、手順 2. で作成するコマンドを定義するセクションです。  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6.  ソリューションをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
7.  クリックして **TestMenu** という名前の新規作成\] サブメニューを表示する **サブメニュー**します。 をクリックして **サブメニュー** サブメニューを開き、新しいコマンドを表示する **Test Sub コマンド**します。 クリックすることを確認 **Test Sub コマンド** 何も行われません。  
  
## コマンドの追加  
  
1.  TestCommand.cs を開き、既存のコマンド ID の後に次のコマンド ID を追加  
  
    ```c#  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  コマンドを追加します。 コマンドのコンス トラクターを検索します。 呼び出しの直後に次の行を追加、 `AddCommand` メソッドです。  
  
    ```c#  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` コマンド ハンドラーが後で定義されます。 コンス トラクターは、次のようになります。  
  
    ```c#  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3.  SubItemCallback\(\) を追加します。 これは、サブメニューで新しいコマンドがクリックされたときに呼び出されるメソッドです。  
  
    ```c#  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
5.  **TestMenu** \] メニューのをクリックして **サブメニュー** \] をクリックし、 **Test Sub コマンド**します。 メッセージ ボックスが表示され、"テスト コマンド内 TestCommand.SubItemCallback\(\)"のテキストを表示する必要があります。  
  
## 参照  
 [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)