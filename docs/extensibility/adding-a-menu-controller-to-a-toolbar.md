---
title: "ツールバーにメニュー コント ローラーの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding menu controllers
- menus, adding menu controllers to toolbars
- menu controllers, adding to toolbars
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: "38"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 786d7c8841f680d5af5c539e30723289df4db0f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="adding-a-menu-controller-to-a-toolbar"></a>ツールバーにメニュー コント ローラーを追加します。
このチュートリアルの[ツール ウィンドウにツールバーを追加する](../extensibility/adding-a-toolbar-to-a-tool-window.md)チュートリアルし、ツール ウィンドウのツールバーにメニュー コント ローラーを追加する方法を示しています。 次に示す手順もに適用できますで作成される、ツールバー、[ツールバーを追加する](../extensibility/adding-a-toolbar.md)チュートリアルです。  
  
 メニュー コント ローラーは、分割コントロールです。 メニュー コント ローラーの左側にあるは、最後に使用されたコマンドを示しをクリックして実行できます。 メニュー コント ローラーの右側にある矢印はをクリックすると、その他のコマンドの一覧が表示されます。 一覧で、コマンドの実行コマンドをクリックして、メニュー コント ローラーの左側にあるコマンドに置き換えます。 この方法では、メニュー コント ローラーは、一覧から、最後に使用されたコマンドが常に表示されるコマンド ボタンのように動作します。  
  
 メニュー コント ローラーがメニューに表示できますが、ツールバーによく使用されます。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降で、ダウンロード センターから、Visual Studio SDK をインストールするはできません。 Visual Studio のセットアップのオプション機能として含まれます。 後でまた VS SDK をインストールすることができます。 詳細については、次を参照してください。 [、Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-menu-controller"></a>メニュー コント ローラーの作成  
  
#### <a name="to-create-a-menu-controller"></a>メニュー コント ローラーを作成するには  
  
1.  記載された手順に従って[ツール ウィンドウにツールバーを追加する](../extensibility/adding-a-toolbar-to-a-tool-window.md)ツールバーのあるツール ウィンドウを作成します。  
  
2.  TWTestCommandPackage.vsct、シンボル セクションに移動します。 指定された GuidSymbol 要素で**guidTWTestCommandPackageCmdSet**、メニュー コント ローラー、メニュー コント ローラーのグループ、および 3 つのメニュー項目を宣言します。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  セクションでは、メニュー、最後のメニュー エントリ後でメニューとメニュー コント ローラーを定義します。  
  
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
  
     `TextChanges`と`TextIsAnchorCommand`フラグは、選択した最後のコマンドを反映するように、メニュー コント ローラーを有効に含める必要があります。  
  
4.  グループのセクションで、最後のグループのエントリの後にメニュー コント ローラーのグループを追加します。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     メニュー コント ローラーを親として設定することにより、このグループに配置されたすべてのコマンドは、メニュー コント ローラーに表示されます。 `priority`属性を省略すると、0、既定値に設定するために、メニュー コント ローラーのみのグループです。  
  
5.  セクションでは、ボタン、最後のボタン エントリ後に、メニュー項目の各ボタンの要素を追加します。  
  
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
  
6.  この時点では、メニュー コント ローラーで確認することができます。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
    1.  **ビュー/その他のウィンドウ**] メニューの [開いている**テスト ToolWindow**です。  
  
    2.  ツール ウィンドウのツールバーにメニュー コント ローラーが表示されます。  
  
    3.  次の 3 つの可能なコマンドを表示するメニュー コント ローラーの右側にある矢印をクリックします。  
  
     コマンドをクリックすると、メニュー コント ローラーのタイトルに変更されているそのコマンドを表示することを確認します。 次のセクションでは、これらのコマンドをアクティブ化するコードを追加します。  
  
## <a name="implementing-the-menu-controller-commands"></a>コント ローラーのメニュー コマンドを実装します。  
  
1.  TWTestCommandPackageGuids.cs では、既存のコマンド Id の後に、3 つのメニュー項目のコマンド Id を追加します。  
  
    ```csharp  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  TWTestCommand.cs では、TWTestCommand クラスの上部にある次のコードを追加します。  
  
    ```csharp  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand コンス トラクターの最後の呼び出しの後で、`AddCommand`メソッド、コマンドごとに、同じ処理を使ったイベントにルーティングするコードを追加します。  
  
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
  
4.  Checked として選択したコマンドをマークする TWTestCommand クラスにイベント ハンドラーを追加します。  
  
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
  
5.  ユーザーがメニュー コント ローラーでコマンドを選択したときに、メッセージ ボックスを表示するイベント ハンドラーを追加します。  
  
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
  
2.  開く、**テスト ToolWindow**上、**ビュー/その他のウィンドウ**メニュー。  
  
     メニュー コント ローラーがツール ウィンドウのツールバーに表示され**MC 項目 1**です。  
  
3.  矢印の左側にメニュー コント ローラーのボタンをクリックします。  
  
     最初が選択されており、そのアイコンを囲む強調表示ボックスの 3 つの項目が表示されます。 をクリックして**MC 項目 3**です。  
  
     ダイアログ ボックスが、メッセージが表示されます**メニュー コント ローラーのアイテム 3 を選択した**です。 メニュー コント ローラー ボタンのテキストにメッセージが対応していることを確認します。 メニュー コント ローラー ボタンを表示するようになりました**MC 項目 3**です。  
  
## <a name="see-also"></a>関連項目  
 [ツール ウィンドウにツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [ツール バーの追加](../extensibility/adding-a-toolbar.md)