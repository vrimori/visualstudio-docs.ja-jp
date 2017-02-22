---
title: "ツール ウィンドウを追加します。 | Microsoft Docs"
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
  - "チュートリアル"
  - "ツール ウィンドウ"
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
caps.latest.revision: 52
caps.handback.revision: 52
ms.author: "gregvanl"
manager: "ghogen"
---
# ツール ウィンドウを追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、ツール ウィンドウを作成し、次の方法で Visual Studio に統合する方法を学習します。  
  
-   ツール ウィンドウに、コントロールを追加します。  
  
-   ツール ウィンドウには、ツールバーを追加します。  
  
-   ツールバーにコマンドを追加します。  
  
-   コマンドを実装します。  
  
-   ツール ウィンドウの既定の位置を設定します。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## ツール ウィンドウを作成します。  
  
1.  という名前のプロジェクトを作成する **FirstToolWin** VSIX のテンプレートを使用し、という名前のカスタム ツール ウィンドウの項目テンプレートを追加 **FirstToolWindow**します。  
  
    > [!NOTE]
    >  ツール ウィンドウで拡張機能の作成の詳細については、次を参照してください。 [ツール ウィンドウで、拡張機能を作成します。](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## ツール ウィンドウにコントロールを追加します。  
  
1.  既定のコントロールを削除します。 FirstToolWindowControl.xaml を開き、削除、 **Click Me\!** \] ボタンをクリックします。  
  
2.  **ツールボックス**, 、展開、 **すべての WPF コントロール** セクションし、ドラッグ、 **メディア要素** への制御、 **FirstToolWindowControl** フォームです。 コントロールを選択し、\[、 **プロパティ** ウィンドウで、この要素名を指定 **mediaElement1**します。  
  
## ツール ウィンドウにツールバーを追加します。  
 ツールバーを追加すると次のように、そのグラデーションと色が IDE の残りの部分と一致するを保証します。  
  
1.  **ソリューション エクスプ ローラー**, 、FirstToolWindowPackage.vsct を開きます。 .Vsct ファイルは、XML を使用して、ツール ウィンドウで、グラフィカル ユーザー インターフェイス \(GUI\) の要素を定義します。  
  
2.  `<Symbols>` セクションで、検索、 `<GuidSymbol>` ノードが `name` 属性は `guidFirstToolWindowPackageCmdSet`です。 次の 2 つの追加 `<IDSymbol>` のリストに対して要素 `<IDSymbol>` ツールバーとツールバーのグループを定義するには、このノード内の要素。  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  すぐ上、 `<Buttons>` セクションで、作成、 `<Menus>` セクションを次のようにします。  
  
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
  
     メニューのいくつかの異なる種類があります。 このメニューで定義されているツール ウィンドウのツールバーは、その `type` 属性です。`guid` と  `id` 設定は、ツールバーの完全修飾 ID を構成します。 通常、 `<Parent>` メニューが含まれるグループです。 ただし、ツールバーは、自身の親として定義されます。 したがってに同じ識別子を使用、 `<Menu>` と `<Parent>` 要素。`priority` 属性は、同じ ' 0' です。  
  
4.  ツールバーには、さまざまな方法でメニューに似ています。 たとえば、メニュー コマンドのグループがある場合がありますと同様、ツールバーではグループの一部こともできます。 \(メニューのコマンド グループを指定する水平の線。 ツールバーのグループで区切られていない visual 区分線です。\)  
  
     追加、 `<Groups>` を格納するセクション、 `<Group>` 要素。 これにより、グループ定義で宣言されている ID を持つ、 `<Symbols>` セクションです。 追加、 `<Groups>` セクションの直後に、 `<Menus>` セクションです。  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     親の GUID と ID を GUID と、ツールバーの ID に設定\] ツールバーに、グループを追加します。  
  
## ツールバーにコマンドを追加します。  
 ボタンとして表示されるツールバーにコマンドを追加します。  
  
1.  `<Symbols>` セクションで、グループの宣言と、ツールバーとツールバーの直後に次の IDSymbol 要素を宣言します。  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  内のボタン要素を追加、 `<Buttons>` セクションです。 この要素は、\[ツール\] ウィンドウの検索 \(虫眼鏡\) アイコンがツールバーに表示されます。  
  
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
  
3.  FirstToolWindowCommand.cs を開き、既存のフィールドの直後に、クラスで、次の行を追加します。  
  
    ```c#  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     これとは、コマンドがコードで使用可能にします。  
  
## FirstToolWindowControl に MediaPlayer プロパティを追加します。  
 コードは、ツール バー コントロールのイベント ハンドラーから FirstToolWindowControl クラスの子である Media Player コントロールにアクセスできる必要があります。  
  
 **ソリューション エクスプ ローラー**, を FirstToolWindowControl.xaml を右クリックして、 **コードの表示**, 、FirstToolWindowControl クラスに次のコードを追加します。  
  
```c#  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## ツール ウィンドウとツールバーを作成します。  
 追加のツールバーとメニュー コマンドを呼び出す、 **ファイルを開く** ダイアログし、選択したメディア ファイルを再生します。  
  
1.  FirstToolWindow.cs を開き、次の追加 `using` ステートメントです。  
  
    ```c#  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  FirstToolWindow クラス内には、FirstToolWindowControl コントロールへのパブリックの参照を追加します。  
  
    ```c#  
    public FirstToolWindowControl control;  
    ```  
  
3.  コンス トラクターの末尾には、このコントロール変数を新しく作成されたコントロールに設定します。  
  
    ```c#  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  コンス トラクター内のツールバーのインスタンスを作成します。  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  この時点で FirstToolWindow コンス トラクターは、次のようになります。  
  
    ```c#  
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
  
6.  メニュー コマンド、ツールバーに追加します。 次のコードを追加 FirstToolWindowCommand.cs クラスでステートメントを使用します。  
  
    ```c#  
    using System.Windows.Forms;  
    ```  
  
7.  FirstToolWindowCommand クラスでは、ShowToolWindow\(\) メソッドの最後に、次のコードを追加します。 ButtonHandler コマンドは、次のセクションで実装されます。  
  
    ```c#  
    // Create the handles for the toolbar command.   
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),  
        FirstToolWindowCommand.cmdidWindowsMediaOpen);  
    var menuItem = new MenuCommand(new EventHandler(  
        ButtonHandler), toolbarbtnCmdID);  
    mcs.AddCommand(menuItem);  
    ```  
  
#### ツール ウィンドウにメニュー コマンドを実装するには  
  
1.  FirstToolWindowCommand クラスを呼び出す ButtonHandler メソッドを追加、 **ファイルを開く** ダイアログ。 ファイルを選択すると、メディア ファイルを再生します。  
  
2.  FirstToolWindowCommand クラスでは、FindToolWindow\(\) メソッドで作成される FirstToolWindow ウィンドウへのプライベート参照を追加します。  
  
    ```c#  
    private FirstToolWindow window;  
    ```  
  
3.  \(そう ButtonHandler コマンド ハンドラーは、ウィンドウのコントロールにアクセスできます上記で定義したウィンドウを設定する ShowToolWindow\(\) 方法を変更します。 完全な ShowToolWindow\(\) メソッドを次に示します。  
  
    ```c#  
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
  
4.  ButtonHandler メソッドを追加します。 ユーザーを再生するメディア ファイルを指定するため、OpenFileDialog が作成され、選択したファイルを再生します。  
  
    ```c#  
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
  
## ツール ウィンドウの既定の位置を設定します。  
 次に、ツール ウィンドウの IDE で、既定の場所を指定します。 ツール ウィンドウの構成情報は、FirstToolWindowPackage.cs ファイルです。  
  
1.  FirstToolWindowPackage.cs を検索、 <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> 属性を `FirstToolWindowPackage` FirstToolWindow 型コンス トラクターに渡しても、クラスです。 既定の位置を指定するには、コンス トラクターの使用例を次に多くのパラメーターを追加する必要があります。  
  
    ```c#  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     最初の名前付きパラメーターは `Style` 、値は `Tabbed`, 、ウィンドウは、既存のウィンドウのタブにあることを意味します。 固定位置が指定された、 `Window` パラメーターには、この場合は、n の GUID、 **ソリューション エクスプ ローラー**します。  
  
    > [!NOTE]
    >  IDE でのウィンドウの種類の詳細については、次を参照してください。 <xref:EnvDTE.vsWindowType>します。  
  
## テスト ツール ウィンドウ  
  
1.  F5 キーを押して Visual Studio の実験用の新しいインスタンスを開くを構築します。  
  
2.  **ビュー** \] メニューをポイント **その他のウィンドウ** \] をクリックし、 **最初のツール ウィンドウ**します。  
  
     同じ位置でメディア プレーヤーのツール ウィンドウを開く必要があります **ソリューション エクスプ ローラー**します。 まだ前に、と同じ位置にある場合は、ウィンドウ レイアウトをリセット \(**ウィンドウ\/ウィンドウ レイアウトのリセット**\)。  
  
3.  \[ツール\] ウィンドウには、\(検索アイコンを持つ\) ボタンをクリックします。 選択、サポートされているサウンドやビデオ ファイルなどの C:\\windows\\media\\chimes.wav キーを押します **開く**します。  
  
     チャイム音を聞く必要があります。  
  
## 参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)