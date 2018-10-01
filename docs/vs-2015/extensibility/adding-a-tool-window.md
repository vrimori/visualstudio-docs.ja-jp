---
title: ツール ウィンドウの追加 |Microsoft Docs
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
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 53
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3d484dc6c7d66284034d29162b19ab45a16fd23f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539767"
---
# <a name="adding-a-tool-window"></a>ツール ウィンドウの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ツール ウィンドウの追加](https://docs.microsoft.com/visualstudio/extensibility/adding-a-tool-window)します。  
  
このチュートリアルでは、ツール ウィンドウを作成し、次の方法で Visual Studio に統合する方法について説明します。  
  
-   ツール ウィンドウにコントロールを追加します。  
  
-   ツール ウィンドウにツールバーを追加します。  
  
-   ツールバーにコマンドを追加します。  
  
-   コマンドを実装します。  
  
-   ツール ウィンドウの既定の位置を設定します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-tool-window"></a>ツール ウィンドウの作成  
  
1.  という名前のプロジェクトを作成する**FirstToolWin** VSIX のテンプレートを使用して、という名前のカスタム ツール ウィンドウの項目テンプレートを追加**FirstToolWindow**します。  
  
    > [!NOTE]
    >  ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## <a name="add-a-control-to-the-tool-window"></a>ツール ウィンドウにコントロールを追加します。  
  
1.  既定のコントロールを削除します。 FirstToolWindowControl.xaml を開き、削除、 **Click Me!** を追加します。  
  
2.  **ツールボックス**、展開、**すべての WPF コントロール**セクションし、ドラッグ、**メディア要素**への制御、 **FirstToolWindowControl**フォーム。 コントロールを選択し、**プロパティ**ウィンドウで、この要素の名前を付けます**mediaElement1**します。  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>ツール ウィンドウにツールバーを追加します。  
 次のようにツールバーを追加すると、色、グラデーションが IDE の残りの部分と一貫性のあることを保証します。  
  
1.  **ソリューション エクスプ ローラー**FirstToolWindowPackage.vsct を開きます。 .Vsct ファイルでは、XML を使用して、ツール ウィンドウで、グラフィカル ユーザー インターフェイス (GUI) の要素を定義します。  
  
2.  `<Symbols>`セクションで、検索、`<GuidSymbol>`ノードが`name`属性が`guidFirstToolWindowPackageCmdSet`します。 次の 2 つの追加`<IDSymbol>`要素の一覧に`<IDSymbol>`ツールバーとツールバーのグループを定義するには、このノード内の要素。  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  すぐ上、`<Buttons>`セクションで、作成、`<Menus>`のようなセクション。  
  
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
  
     メニューのさまざまな種類があります。 このメニューで定義されているツール ウィンドウ、ツールバーは、その`type`属性。 `guid`と`id`設定は、ツールバーの完全修飾 ID を構成します。 通常、`<Parent>`メニューが含まれるグループ。 ただし、ツールバーは、それ自身の親として定義されます。 そのため、同じ識別子がの使用、`<Menu>`と`<Parent>`要素。 `priority`属性がだけ ' 0' です。  
  
4.  ツールバーには、さまざまな方法でのメニューに似ています。 たとえば、メニュー コマンドのグループがある可能性があります、同じようでも、ツールバーのグループ場合もあります。 (メニューのコマンド グループを指定する本の水平線アイコン。 ツールバーのグループによって分離されていないビジュアルの区分線です。)  
  
     追加、`<Groups>`を含むセクションを`<Group>`要素。 これで宣言されている ID を持つグループを定義、`<Symbols>`セクション。 追加、`<Groups>`セクション直後、`<Menus>`セクション。  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     GUID と ID の GUID と、ツールバーの ID を親を設定、ツールバーに、グループを追加します。  
  
## <a name="add-a-command-to-the-toolbar"></a>コマンド、ツールバーを追加します。  
 ボタンとして表示されると、ツールバーにコマンドを追加します。  
  
1.  `<Symbols>`セクションで、グループの宣言と、ツールバーとツールバーの直後に、次の IDSymbol 要素を宣言します。  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  内のボタン要素を追加、`<Buttons>`セクション。 この要素は、[ツール] ウィンドウで検索 (虫眼鏡) アイコンがツールバーに表示されます。  
  
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
  
3.  FirstToolWindowCommand.cs を開き、既存のフィールドの直後後、クラスで、次の行を追加します。  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     これにより、コマンドがコードで使用できます。  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>MediaPlayer プロパティ FirstToolWindowControl を追加します。  
 ツール バー コントロールのイベント ハンドラーからには、コードは FirstToolWindowControl クラスの子である Media Player コントロールにアクセスできる必要があります。  
  
 **ソリューション エクスプ ローラー**FirstToolWindowControl.xaml を右クリックしてをクリックし、**コードの表示**、FirstToolWindowControl クラスに次のコードを追加します。  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>ツール ウィンドウとツールバーをインスタンス化します。  
 ツールバーとメニュー コマンドを呼び出す追加、**ファイルを開く**ダイアログとは、選択したメディア ファイルを再生します。  
  
1.  FirstToolWindow.cs を開き、次の追加`using`ステートメント。  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  FirstToolWindow クラス内には、FirstToolWindowControl コントロールへのパブリックの参照を追加します。  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  コンス トラクターの末尾には、新しく作成されたコントロールにこのコントロールの変数を設定します。  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  コンス トラクター内でツールバーをインスタンス化します。  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  この時点で FirstToolWindow コンス トラクターは次のようになります。  
  
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
  
6.  ツールバーにメニュー コマンドを追加します。 次のコードを追加、FirstToolWindowCommand.cs クラスでステートメントを使用します。  
  
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
  
2.  FirstToolWindowCommand クラスでは、FindToolWindow() メソッドで作成される FirstToolWindow ウィンドウへの参照をプライベートを追加します。  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  (その ButtonHandler コマンド ハンドラーは、ウィンドウ コントロールにアクセスできます上記で定義した期間を設定する ShowToolWindow() メソッドを変更します。 完全な ShowToolWindow() メソッドを次に示します。  
  
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
  
4.  ButtonHandler メソッドを追加します。 OpenFileDialog を再生するメディア ファイルを指定するユーザーを作成し、選択したファイルが再生されます。  
  
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
 次に、ツール ウィンドウの IDE で、既定の場所を指定します。 ツール ウィンドウの構成情報は、FirstToolWindowPackage.cs ファイルです。  
  
1.  FirstToolWindowPackage.cs で見つけ、<xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>属性を`FirstToolWindowPackage`クラスで、FirstToolWindow 型をコンス トラクターに渡します。 既定の位置を指定するには、コンス トラクターの例を次に以上のパラメーターを追加する必要があります。  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     最初の名前付きパラメーターは`Style`、値は`Tabbed`ウィンドウは、既存のウィンドウ タブにあることを意味します。 ドッキング位置がで指定された、`Window`パラメーターでは、この場合は、n の GUID、**ソリューション エクスプ ローラー**します。  
  
    > [!NOTE]
    >  IDE のウィンドウの種類の詳細については、次を参照してください。<xref:EnvDTE.vsWindowType>します。  
  
## <a name="testing-the-tool-window"></a>ツール ウィンドウのテスト  
  
1.  F5 キーを押して Visual Studio の実験用の新しいインスタンスを開いてビルドします。  
  
2.  **ビュー**メニューで、**その他の Windows**  をクリックし、**最初のツール ウィンドウ**します。  
  
     同じ位置でメディア プレーヤーのツール ウィンドウを開く必要があります**ソリューション エクスプ ローラー**します。 前に、と同じ位置に引き続き表示される場合、ウィンドウ レイアウトのリセット (**ウィンドウ/ウィンドウ レイアウトのリセット**)。  
  
3.  ツール ウィンドウで、(検索アイコンがある) ボタンをクリックします。 サポートされているサウンドまたはビデオ ファイルを選択 C:\windows\media\chimes.wav など、キーを押します**オープン**します。  
  
     チャイム音を聞く必要があります。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)

