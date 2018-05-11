---
title: ツール ウィンドウを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db06bebd700fa229685d6b79ffcfb014ef301994
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-tool-window"></a>ツール ウィンドウを追加します。
このチュートリアルでは、ツール ウィンドウを作成し、次のように Visual Studio に統合する方法を学習します。  
  
-   ツール ウィンドウにコントロールを追加します。  
  
-   ツール ウィンドウにツールバーを追加します。  
  
-   コマンドは、ツールバーを追加します。  
  
-   コマンドを実装します。  
  
-   ツール ウィンドウの既定の位置を設定します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-tool-window"></a>ツール ウィンドウを作成します。  
  
1.  という名前のプロジェクトを作成する**FirstToolWin** VSIX テンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートの追加**FirstToolWindow**です。  
  
    > [!NOTE]
    >  ツール ウィンドウで、拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能の作成](../extensibility/creating-an-extension-with-a-tool-window.md)です。  
  
## <a name="add-a-control-to-the-tool-window"></a>ツール ウィンドウにコントロールを追加します。  
  
1.  既定のコントロールを削除します。 FirstToolWindowControl.xaml を開き、削除、 **Click Me!** ボタンをクリックします。  
  
2.  **ツールボックス**、展開、**すべての WPF コントロール**セクションし、ドラッグ、**メディア要素**コントロールを**FirstToolWindowControl**フォーム。 コントロールを選択し、、**プロパティ**ウィンドウで、この要素の名前を付けます**mediaElement1**です。  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>ツール ウィンドウにツールバーを追加します。  
 ツールバーを追加すると、次のように、色、グラデーションが IDE の残りの部分と一貫性のあることを保証します。  
  
1.  **ソリューション エクスプ ローラー**FirstToolWindowPackage.vsct を開きます。 .Vsct ファイルでは、XML を使用して、ツール ウィンドウで、グラフィカル ユーザー インターフェイス (GUI) 要素を定義します。  
  
2.  `<Symbols>`セクションで、検索、`<GuidSymbol>`ノードが`name`属性は`guidFirstToolWindowPackageCmdSet`します。 次の 2 つの追加`<IDSymbol>`要素の一覧を`<IDSymbol>`ツールバーとツール バー グループを定義するには、このノード内の要素。  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  すぐ上、`<Buttons>`セクションで、作成、`<Menus>`これに似たセクション。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">  
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
            <Strings>  
                <ButtonText>Tool Window Toolbar</ButtonText>  
                <CommandName>Tool Window Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     メニューのさまざまな種類があります。 このメニューで定義されているツール ウィンドウのツールバーは、その`type`属性。 `guid`と`id`設定は、ツールバーの完全修飾 ID を構成します。 通常、`<Parent>`メニューは、含んでいるグループ。 ただし、ツールバーは、自身の親として定義されます。 このため、同じ識別子は、使用、`<Menu>`と`<Parent>`要素。 `priority`属性がだけ ' 0' です。  
  
4.  ツールバーには、さまざまな方法でメニューがようになります。 たとえば、メニュー コマンドのグループがある可能性がありますと同様、ツールバーではグループの一部こともできます。 (メニューのコマンド グループを指定する水平の線。 ツールバーのグループによって分離されていない visual 仕切り。)  
  
     追加、`<Groups>`を格納するセクション、`<Group>`要素。 宣言されている ID を持つグループの定義、`<Symbols>`セクションです。 追加、`<Groups>`直後セクション、`<Menus>`セクションです。  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     親の GUID と ID を GUID と、ツールバーの ID に設定して、ツールバーに、グループを追加します。  
  
## <a name="add-a-command-to-the-toolbar"></a>コマンド、ツールバーを追加します。  
 コマンドは、ボタンとして表示される、ツールバーを追加します。  
  
1.  `<Symbols>`セクションで、グループの宣言、ツールバーとツールバーの直後に、次の IDSymbol 要素を宣言します。  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  内のボタンの要素を追加、`<Buttons>`セクションです。 この要素は、検索 (虫眼鏡) アイコンの付いた、ツール ウィンドウのツールバーに表示されます。  
  
    ```xml  
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">  
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>  
        <Icon guid="guidImages" id="bmpPicSearch" />  
        <Strings>  
            <CommandName>cmdidWindowsMediaOpen</CommandName>  
            <ButtonText>Load File</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  FirstToolWindowCommand.cs を開き、クラス内の既存のフィールドの直後に次の行を追加します。  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     これにより、コマンドをコードで使用できます。  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Media Player プロパティ FirstToolWindowControl を追加します。  
 ツール バー コントロールのイベント ハンドラーからコードは、FirstToolWindowControl クラスの子である Media Player コントロールにアクセスできる必要があります。  
  
 **ソリューション エクスプ ローラー**FirstToolWindowControl.xaml を右クリックしをクリックして**コードの表示**、FirstToolWindowControl クラスに次のコードを追加します。  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>ツールバーとツール ウィンドウをインスタンス化します。  
 ツールバーとメニュー コマンドを呼び出す追加、**ファイルを開く**ダイアログと、選択したメディア ファイルを再生します。  
  
1.  FirstToolWindow.cs を開き、次の追加`using`ステートメントです。  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  FirstToolWindow クラス内には、FirstToolWindowControl コントロールへのパブリックの参照を追加します。  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  コンス トラクターの最後には、新しく作成されたコントロールにこのコントロール変数を設定します。  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  コンス トラクター内部ツールバーのインスタンスを作成します。  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  この時点で FirstToolWindow コンス トラクターは、次のようになります。  
  
    ```csharp  
    public FirstToolWindow() : base(null)  
    {  
        this.Caption = "FirstToolWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
        control = new FirstToolWindowControl();  
        base.Content = control;  
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
            FirstToolWindowCommand.ToolbarID);  
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    }  
    ```  
  
6.  ツールバーにメニュー コマンドを追加します。 次のコードを追加 FirstToolWindowCommand.cs クラスでステートメントを使用します。  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  FirstToolWindowCommand クラスでは、ShowToolWindow() メソッドの最後に、次のコードを追加します。 ButtonHandler コマンドは、次のセクションで実装されます。  
  
    ```csharp  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>ツール ウィンドウにメニュー コマンドを実装するには  
  
1.  FirstToolWindowCommand クラスでを呼び出す ButtonHandler メソッドを追加、**ファイルを開く**ダイアログ。 ファイルを選択すると、メディア ファイルを再生します。  
  
2.  FirstToolWindowCommand クラスでは、FindToolWindow() メソッドで作成される FirstToolWindow ウィンドウへのプライベートの参照を追加します。  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  ShowToolWindow() メソッド (ように ButtonHandler コマンド ハンドラーは、ウィンドウ コントロールにアクセスできます上で定義するウィンドウの設定を変更します。 ShowToolWindow() メソッド全体を次に示します。  
  
    ```csharp  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
                            throw new NotSupportedException("Cannot create tool window");  
        }  
  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
         var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),  
            FirstToolWindowCommand.cmdidWindowsMediaOpen);  
        var menuItem = new MenuCommand(new EventHandler(  
            ButtonHandler), toolbarbtnCmdID);  
        mcs.AddCommand(menuItem);  
    }  
    ```  
  
4.  ButtonHandler メソッドを追加します。 OpenFileDialog を再生するメディア ファイルを指定するユーザーが作成され、選択したファイルを再生します。  
  
    ```csharp  
    private void ButtonHandler(object sender, EventArgs arguments)  
    {  
        OpenFileDialog openFileDialog = new OpenFileDialog();  
        DialogResult result = openFileDialog.ShowDialog();  
        if (result == DialogResult.OK)  
        {  
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);  
        }  
    }  
    ```  
  
## <a name="set-the-default-position-for-the-tool-window"></a>ツール ウィンドウの既定の位置を設定します。  
 次に、ツール ウィンドウを IDE の既定の場所を指定します。 ツール ウィンドウの構成情報は、FirstToolWindowPackage.cs ファイルです。  
  
1.  FirstToolWindowPackage.cs、検索、<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>属性を`FirstToolWindowPackage`FirstToolWindow 型コンス トラクターに渡しても、クラスです。 既定の位置を指定するには、コンス トラクターは、次の例に以上のパラメーターを追加する必要があります。  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     最初の名前付きパラメーターは`Style`とその値は`Tabbed`、つまり、ウィンドウが、既存のウィンドウのタブになります。 ドッキング位置がで指定された、`Window`パラメーターでは、この場合は、n の GUID、**ソリューション エクスプ ローラー**です。  
  
    > [!NOTE]
    >  IDE のウィンドウの種類の詳細については、次を参照してください。<xref:EnvDTE.vsWindowType>です。  
  
## <a name="testing-the-tool-window"></a>ツール ウィンドウのテスト  
  
1.  Visual Studio の実験用の新しいインスタンスを開くに f5 キーを押してビルドします。  
  
2.  **ビュー**  メニューのをポイント**その他のウィンドウ** をクリックし、**最初のツール ウィンドウ**します。  
  
     同じ位置でメディア プレーヤーのツール ウィンドウを開いてください**ソリューション エクスプ ローラー**です。 前に、と同じ位置に表示されて、ウィンドウのレイアウトをリセット (**ウィンドウ/ウィンドウ レイアウトのリセット**)。  
  
3.  ツール ウィンドウには、(、検索アイコンが) ボタンをクリックします。 サポートされているサウンドやビデオ ファイルを選択 C:\windows\media\chimes.wav など、キーを押します**開く**です。  
  
     チャイム音を聞く必要があります。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)