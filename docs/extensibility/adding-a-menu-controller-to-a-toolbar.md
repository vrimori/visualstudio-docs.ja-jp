---
title: "ツールバー] メニューの [コント ローラーの追加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ツールバー [Visual Studio] メニューのコント ローラーの追加"
  - "メニュー、ツールバーを] メニューの [コント ローラーの追加"
  - "ツールバーへの追加] メニューの [コント ローラー"
ms.assetid: 6af9b0b4-037f-404c-bb40-aaa1970768ea
caps.latest.revision: 38
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 38
---
# ツールバー] メニューの [コント ローラーの追加
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルに基づき、 [ツール ウィンドウに、ツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md) チュートリアルにツール ウィンドウのツールバー\] メニューの \[コント ローラーを追加する方法を示しています。 以下に示す手順もに適用できるで作成されたツールバー、 [ツールバーを追加します。](../extensibility/adding-a-toolbar.md) チュートリアルです。  
  
 メニューの \[コント ローラーは、分割コントロールです。 メニューの \[コント ローラーの左側にあるは最後に使用されたコマンドを示しをクリックして実行できます。 メニューの \[コント ローラーの右側にある矢印はをクリックすると、その他のコマンドの一覧を表示します。 リストで、コマンドの実行\] をクリックして、メニュー コント ローラーの左側にあるコマンドが置き換えられます。 この方法では\] メニューの \[コント ローラーは、一覧から最後に使用されたコマンドが常に表示されるコマンド ボタンのように動作します。  
  
 コント ローラーのメニューがメニューに表示できますが、ツールバーに最もよく使用されます。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## メニューの \[コント ローラーの作成  
  
#### メニューの \[コント ローラーを作成するには  
  
1.  説明する手順に従います [ツール ウィンドウに、ツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md) ツールバーのあるツール ウィンドウを作成します。  
  
2.  TWTestCommandPackage.vsct、Symbols セクションに移動します。 指定された GuidSymbol 要素で **guidTWTestCommandPackageCmdSet**, 、\] メニューの \[コント ローラー、\] メニューの \[コント ローラーのグループ、および 3 つのメニュー項目を宣言します。  
  
    ```xml  
    <IDSymbol name="TestMenuController" value="0x1300" /><IDSymbol name="TestMenuControllerGroup" value="0x1060" /><IDSymbol name="cmdidMCItem1" value="0x0130" /><IDSymbol name="cmdidMCItem2" value="0x0131" /><IDSymbol name="cmdidMCItem3" value="0x0132" />  
    ```  
  
3.  メニュー」のセクションで、最後のメニュー エントリの後に、メニューとして\] メニューの \[コント ローラーを定義します。  
  
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
  
     `TextChanges` と `TextIsAnchorCommand` フラグは、選択した最後のコマンドを反映するように、メニュー コント ローラーを有効に含める必要があります。  
  
4.  グループの最後のグループのエントリの後のセクション\] メニューの \[コント ローラーのグループを追加します。  
  
    ```xml  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TestMenuControllerGroup" priority="0x000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TestMenuController" />  
    </Group>  
    ```  
  
     メニューの \[コント ローラーを親として設定することにより、このグループに配置されたすべてのコマンドは、メニュー コント ローラーに表示されます。`priority` 属性を省略すると、既定値は 0 に設定する\] メニューの \[コント ローラーのみのグループとなります。  
  
5.  \[ボタン\] セクションで、最後のボタンのエントリの後に、メニュー項目の各 Button 要素を追加します。  
  
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
  
6.  この時点では、\] メニューの \[コント ローラーで確認することができます。 プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
    1.  **ビュー\/その他のウィンドウ** \] メニューの \[開く **テスト ツール ウィンドウ**します。  
  
    2.  \[ツール\] ウィンドウ ツールバー\] メニューの \[コント ローラーが表示されます。  
  
    3.  次の 3 つの可能なコマンドを参照してください\] メニューの \[コント ローラーの右側にある矢印をクリックします。  
  
     コマンドをクリックすると、そのコマンドを表示する\] メニューの \[コント ローラーのタイトルが変更に注意してください。 次のセクションでは、これらのコマンドをアクティブ化するコードを追加します。  
  
## コント ローラーのメニュー コマンドを実装します。  
  
1.  TWTestCommandPackageGuids.cs では、既存のコマンド Id の後に 3 つのメニュー項目のコマンド Id を追加します。  
  
    ```c#  
    public const int cmdidMCItem1 = 0x130;  
    public const int cmdidMCItem2 = 0x131;  
    public const int cmdidMCItem3 = 0x132;  
    ```  
  
2.  TWTestCommand.cs では、TWTestCommand クラスの上部にある次のコードを追加します。  
  
    ```c#  
    private int currentMCCommand; // The currently selected menu controller command  
    ```  
  
3.  TWTestCommand コンス トラクターの最後の呼び出しの後で、 `AddCommand` メソッドでは、同じ処理を使ったコマンドごとにイベントをルーティングするためのコードを追加します。  
  
    ```c#  
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
  
4.  Checked のように選択したコマンドをマークする TWTestCommand クラスにイベント ハンドラーを追加します。  
  
    ```c#  
    private void OnMCItemQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand mc = sender as OleMenuCommand;  
        if (null != mc)  
        {  
            mc.Checked = (mc.CommandID.ID == this.currentMCCommand);  
        }  
    }  
    ```  
  
5.  ユーザーが\] メニューの \[コント ローラーでコマンドを選択したときに、メッセージ ボックスを表示するイベント ハンドラーを追加します。  
  
    ```c#  
    private void OnMCItemClicked(object sender, EventArgs e)  
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
  
## メニューの \[コント ローラーのテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  開いている、 **テスト ツール ウィンドウ** 上、 **ビュー\/その他のウィンドウ** メニュー。  
  
     メニューの \[コント ローラーがツール ウィンドウのツールバーに表示され **MC アイテム 1**します。  
  
3.  矢印の左側にあるメニュー コント ローラー ボタンをクリックします。  
  
     まずが選択されており、そのアイコンを囲む強調表示の 3 つの項目が表示されます。 クリックして **MC 項目 3**します。  
  
     ダイアログ ボックスが、メッセージが表示されます **コント ローラーのメニュー項目 3 を選択した**します。 コント ローラーのメニュー ボタンのテキストにメッセージが対応していることを確認します。 コント ローラーのメニュー ボタンが表示されます **MC 項目 3**します。  
  
## 参照  
 [ツール ウィンドウに、ツールバーを追加します。](../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [ツールバーを追加します。](../extensibility/adding-a-toolbar.md)