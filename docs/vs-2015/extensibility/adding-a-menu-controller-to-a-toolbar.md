---
title: ツールバーにメニュー コント ローラーの追加 |Microsoft Docs
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
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 39
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f6d124b1dc6bcd16b0f4d62c47df521ba25b07b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545641"
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>メニュー コントローラーのツールバーへの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ツールバーにメニュー コント ローラーの追加](https://docs.microsoft.com/visualstudio/extensibility/adding-a-menu-controller-to-a-toolbar)します。  
  
このチュートリアルの[ツール ウィンドウにツールバーを追加する](../extensibility/adding-a-toolbar-to-a-tool-window.md)チュートリアルとツール ウィンドウのツールバーにメニュー コント ローラーを追加する方法について説明します。 以下に示す手順も適用できますで作成したツールバーに、[ツールバーの追加](../extensibility/adding-a-toolbar.md)チュートリアル。  
  
 メニュー コント ローラーは、分割コントロールです。 メニュー コント ローラーの左側にあるは、最後に使用されたコマンドを示しをクリックして実行できます。 メニュー コント ローラーの右側にある矢印をクリックすると、その他のコマンドの一覧を開きます。 コマンドの実行の一覧でコマンドをクリックして、メニュー コント ローラーの左側にあるコマンドに置き換えられます。 これで、メニュー コント ローラーは、一覧から最後に使用されたコマンドは常に表示されるコマンド ボタンのように動作します。  
  
 メニューにメニュー コント ローラーを表示できますが、ツールバーに最もよく使われます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-menu-controller"></a>メニュー コント ローラーの作成  
  
#### <a name="to-create-a-menu-controller"></a>メニュー コント ローラーを作成するには  
  
1.  説明されている手順に従って[ツール ウィンドウにツールバーを追加する](../extensibility/adding-a-toolbar-to-a-tool-window.md)ツールバーのあるツール ウィンドウを作成します。  
  
2.  TWTestCommandPackage.vsct、Symbols セクションに移動します。 という名前の GuidSymbol 要素で**guidTWTestCommandPackageCmdSet**、メニュー コント ローラー、メニュー コント ローラーのグループ、および 3 つのメニュー項目を宣言します。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  メニューのセクションで、最後のメニュー エントリの後に、メニューとしてメニュー コント ローラーを定義します。  
  
    ```xml  
    <Menu guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" priority="0x0100" type="MenuController">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <CommandFlag>TextChanges</CommandFlag>  
        <CommandFlag>TextIsAnchorCommand</CommandFlag>  
        <Strings>  
            <ButtonText>Test Menu Controller</ButtonText>  
            <CommandName>Test Menu Controller</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     `TextChanges`と`TextIsAnchorCommand`フラグは、選択した最後のコマンドを反映するためにメニュー コント ローラーを含める必要があります。  
  
4.  グループのセクションで、最後のグループのエントリの後にメニュー コント ローラーのグループを追加します。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     メニュー コント ローラーを親として設定することにより、このグループに配置されたすべてのコマンドは、メニュー コント ローラーに表示されます。 `priority`属性を省略すると、0 の場合の既定値に設定する唯一のグループにメニュー コント ローラーとなります。  
  
5.  ボタンのセクションで、最後のボタンのエントリ後、メニュー項目の各ボタン要素を追加します。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem1" priority="0x0000" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 1</ButtonText>  
            <CommandName>MC Item 1</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem2" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 2</ButtonText>  
            <CommandName>MC Item 2</CommandName>  
        </Strings>  
    </Button>  
    <Button guid="guidTWTestCommandPackageCmdSet" id="cmdidMCItem3" priority="0x0200" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" />  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <CommandFlag>IconAndText</CommandFlag>  
        <Strings>  
            <ButtonText>MC Item 3</ButtonText>  
            <CommandName>MC Item 3</CommandName>  
        </Strings>  
    </Button>  
    ```  
  
6.  この時点では、メニュー コント ローラーで確認できます。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
    1.  **ビュー/その他の Windows** ] メニューの [open**テスト ToolWindow**します。  
  
    2.  ツール ウィンドウのツールバーにメニュー コント ローラーが表示されます。  
  
    3.  次の 3 つの可能なコマンドを表示するメニュー コント ローラーの右側にある矢印をクリックします。  
  
     コマンドをクリックしたときにそのコマンドを表示するメニュー コント ローラーのタイトルが変更に注意してください。 次のセクションでは、これらのコマンドをアクティブ化するコードを追加します。  
  
## <a name="implementing-the-menu-controller-commands"></a>コント ローラーのメニュー コマンドを実装します。  
  
1.  TWTestCommandPackageGuids.cs では、既存のコマンド Id の後に、次の 3 つのメニュー項目のコマンド Id を追加します。  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  TWTestCommand.cs では、TWTestCommand クラスの上部にある次のコードを追加します。  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand コンス トラクターの最後の呼び出しの後で、`AddCommand`メソッドでは、コマンドごとに同じハンドラーを使用してイベントをルーティングするコードを追加します。  
  
    ```csharp  
    for (int i = TWTestCommandPackageGuids.cmdidMCItem1; i <=  
        TWTestCommandPackageGuids.cmdidMCItem3; i++)  
    {  
        CommandID cmdID = new  
        CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), i);  
        OleMenuCommand mc = new OleMenuCommand(new  
          EventHandler(OnMCItemClicked), cmdID);  
        mc.BeforeQueryStatus += new EventHandler(OnMCItemQueryStatus);  
        commandService.AddCommand(mc);  
        // The first item is, by default, checked.   
        if (TWTestCommandPackageGuids.cmdidMCItem1 == i)  
        {  
            mc.Checked = true;  
            this.currentMCCommand = i;  
        }  
    }  
    ```  
  
4.  チェックされているように選択したコマンドをマークする TWTestCommand クラスにイベント ハンドラーを追加します。  
  
    ```csharp  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  メニュー コント ローラー上のコマンドを選択すると、メッセージ ボックスを表示するイベント ハンドラーを追加します。  
  
    ```csharp  
    private void OnMCItemClicked(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            string selection;  
            switch (mc.CommandID.ID)  
            {  
                case c.cmdidMCItem1:  
                    selection = "Menu controller Item 1";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem2:  
                    selection = "Menu controller Item 2";  
                    break;  
  
                case TWTestCommandPackageGuids.cmdidMCItem3:  
                    selection = "Menu controller Item 3";  
                    break;  
  
                default:  
                    selection = "Unknown command";  
                    break;  
            }  
            this.currentMCCommand = mc.CommandID.ID;  
  
            IVsUIShell uiShell =  
              (IVsUIShell) ServiceProvider.GetService(typeof(SVsUIShell));  
            Guid clsid = Guid.Empty;  
            int result;  
            uiShell.ShowMessageBox(  
                       0,  
                       ref clsid,  
                       "Test Tool Window Toolbar Package",  
                       string.Format(CultureInfo.CurrentCulture,  
                                     "You selected {0}", selection),  
                       string.Empty,  
                       0,  
                       OLEMSGBUTTON.OLEMSGBUTTON_OK,  
                       OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
                       OLEMSGICON.OLEMSGICON_INFO,  
                       0,  
                       out result);  
        }  
    }  
    ```  
  
## <a name="testing-the-menu-controller"></a>メニュー コント ローラーのテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  開く、**テスト ToolWindow**上、**ビュー/その他の Windows**メニュー。  
  
     メニュー コント ローラーがツール ウィンドウのツールバーに表示され**MC アイテム 1**します。  
  
3.  矢印の左側にあるメニュー コント ローラー ボタンをクリックします。  
  
     選択されており、そのアイコンの周囲に強調表示ボックスの 3 つの項目が表示されます。 クリックして**MC 項目 3**します。  
  
     ダイアログ ボックスが、メッセージが表示されます**コント ローラーのメニュー項目 3 を選択した**します。 メッセージは、メニュー コント ローラーのボタンのテキストに対応することを確認します。 メニュー コント ローラー ボタンを表示するようになりました**MC 項目 3**します。  
  
## <a name="see-also"></a>関連項目  
 [ツール ウィンドウにツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [ツール バーの追加](../extensibility/adding-a-toolbar.md)

