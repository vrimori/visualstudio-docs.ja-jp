---
title: "メニューにサブメニューを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: "43"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 150252dceaff2d194af8f59d92fdaf39cdae259c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="adding-a-submenu-to-a-menu"></a>メニューにサブメニューを追加
上でデモについては、このチュートリアルをビルド[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)にサブメニューを追加する方法を表示することによって、 **TestMenu**メニュー。  
  
 サブメニューは、別のメニューに表示されるセカンダリ メニューです。 サブメニューは、その名前に依存して、矢印によって識別できます。 名前をクリックすると、サブメニュー、表示するには、そのコマンド。  
  
 このチュートリアルでは、Visual Studio のメニュー バーのメニューにサブメニューを作成し、サブメニューに新しいコマンドを格納します。 このチュートリアルでは、新しいコマンドも実装します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="adding-a-submenu-to-a-menu"></a>メニューにサブメニューを追加  
  
1.  手順に従います[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)プロジェクトとメニュー項目を作成します。 このチュートリアルの手順では、VSIX プロジェクトの名前があると仮定`TopLevelMenu`です。  
  
2.  TestCommandPackage.vsct を開きます。 `<Symbols>`セクションを追加、`<IDSymbol>`サブメニュー グループと、コマンド内のすべてのサブメニューの要素、 `<GuidSymbol>` "guidTopLevelMenuCmdSet"という名前のノード。 これは、同じノードを含む、 `<IDSymbol>`  メニューの最上位の要素。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  新しく作成したサブメニューを追加、`<Menus>`セクションです。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     親の GUID と ID のペアが生成されたメニュー グループを指定する[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)、トップレベルのメニューの子であるとします。  
  
4.  手順 2 で定義されているメニュー グループを追加、`<Groups>`セクションし、サブメニューの子に設定します。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  新しい`<Button>`要素を`<Buttons>`サブメニューの項目として、手順 2 で作成されたコマンドを定義するセクション。  
  
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
  
7.  をクリックして**TestMenu**という名前の新規作成 サブメニューを表示する**サブメニュー**です。 をクリックして**サブメニュー**をサブメニューを開き、新しいコマンドを確認して**テスト Sub コマンド**です。 クリックすることを確認**テスト Sub コマンド**何も行われません。  
  
## <a name="adding-a-command"></a>コマンドの追加  
  
1.  TestCommand.cs を開き、既存のコマンド ID の後に、次のコマンド ID を追加  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  サブ コマンドを追加します。 コマンドのコンス トラクターを検索します。 呼び出しの直後に次の行を追加、`AddCommand`メソッドです。  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`コマンド ハンドラーを後で定義されます。 コンス トラクターは、次のようになります。  
  
    ```csharp  
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
  
3.  SubItemCallback() を追加します。 これはサブメニューに新しいコマンドがクリックされたときに呼び出されるメソッドです。  
  
    ```csharp  
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
  
5.  **TestMenu**  メニューのをクリックして**サブメニュー**  をクリックし、**テスト Sub コマンド**です。 メッセージ ボックスは表示され、"テスト コマンド内 TestCommand.SubItemCallback()"のテキストを表示する必要があります。  
  
## <a name="see-also"></a>参照  
 [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)