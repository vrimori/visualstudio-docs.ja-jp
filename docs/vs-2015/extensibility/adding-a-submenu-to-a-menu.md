---
title: サブメニューのメニューへの追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 93d34c0402eeb963cfb49ab3a890a97e77b625a9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548828"
---
# <a name="adding-a-submenu-to-a-menu"></a>サブメニューのメニューへの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[サブメニューのメニューに追加](https://docs.microsoft.com/visualstudio/extensibility/adding-a-submenu-to-a-menu)します。  
  
このチュートリアルのデモ」に基づいて[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)にサブメニューを追加する方法を表示することによって、 **TestMenu**メニュー。  
  
 サブメニューは、別のメニューに表示されるセカンダリ メニューです。 サブメニューは、その名の後の矢印で識別できます。 名前をクリックすると、サブメニューで開くと表示するには、そのコマンド。  
  
 このチュートリアルでは、Visual Studio のメニュー バーのメニューにサブメニューを作成し、サブメニューで、新しいコマンドを配置します。 このチュートリアルでは、新しいコマンドも実装します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="adding-a-submenu-to-a-menu"></a>サブメニューのメニューへの追加  
  
1.  手順に従って[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)プロジェクトとメニュー項目を作成します。 このチュートリアルの手順では、VSIX プロジェクトの名前があると仮定`TopLevelMenu`します。  
  
2.  TestCommandPackage.vsct を開きます。 `<Symbols>`セクションで、追加、 `<IDSymbol>` 、サブメニューで開くグループとすべてのコマンドは、サブメニューの要素、 `<GuidSymbol>` "guidTopLevelMenuCmdSet"という名前のノード。 これは、同じノードを含む、 `<IDSymbol>`  メニューの最上位の要素。  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  新しく作成したサブメニューを追加、`<Menus>`セクション。  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     親の GUID と ID のペアが生成されたメニュー グループを指定します[Visual Studio のメニュー バーにメニューを追加する](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)、トップレベルのメニューの子であるとします。  
  
4.  手順 2 で定義されているメニュー グループの追加、`<Groups>`セクションし、サブメニューの子になります。  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  新しい追加`<Button>`要素を`<Buttons>`サブメニューの項目として手順 2 で作成したコマンドを定義するセクション。  
  
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
  
7.  クリックして**TestMenu**という名前の新しいサブメニューを表示する**サブメニュー**します。 クリックして**サブメニュー**をサブメニューを開き、新しいコマンドを参照してください**テスト サブ コマンド**します。 クリックをする**テスト サブ コマンド**何も行われません。  
  
## <a name="adding-a-command"></a>コマンドの追加  
  
1.  TestCommand.cs を開いて、既存のコマンド ID の後に、次のコマンド ID を追加  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  サブ コマンドを追加します。 コマンドのコンス トラクターを検索します。 呼び出し直後に次の行を追加、`AddCommand`メソッド。  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`コマンド ハンドラーは後で定義されます。 コンス トラクターは、次のようになります。  
  
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
  
3.  SubItemCallback() を追加します。 これは、サブメニューで新しいコマンドがクリックされたときに呼び出されるメソッドです。  
  
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
  
5.  **TestMenu**  メニューのをクリックして**サブメニュー**順にクリックします**テスト サブ コマンド**します。 メッセージ ボックスが表示され、"テスト コマンド内で TestCommand.SubItemCallback()"のテキストを表示する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のメニュー バーにメニューを追加します。](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)

