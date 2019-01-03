---
title: ツール ウィンドウのショートカット メニューを追加する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa350ff37a5073a5def0140db694b53c9fdf5067
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909802"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>ツール ウィンドウのショートカット メニューを追加します。
このチュートリアルでは、ツール ウィンドウのショートカット メニューを配置します。 ショートカット メニューは、ユーザーは、ボタン、テキスト ボックスに、またはウィンドウの背景を右クリックしたときに表示されるメニューです。 ショートカット メニューのコマンドは、その他のメニューまたはツールバーでコマンドと同じ動作します。 ショートカット メニューをサポートするために指定で、 *.vsct*ファイルを開き、マウスの右クリックに応答に表示します。  
  
 ツール ウィンドウから継承するカスタム ツール ウィンドウのクラスでの WPF ユーザー コントロールから成る<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>します。  
  
 このチュートリアルでのメニュー項目を宣言することで Visual Studio のメニューにショートカット メニューを作成する方法を示しています、 *.vsct*ファイルを開き、ツール ウィンドウを定義するクラスで実装する Managed Package Framework を使用します。 このアプローチには、Visual Studio コマンド、UI 要素、およびオートメーション オブジェクト モデルへのアクセスが容易になります。  
  
 また場合、ショートカット メニューでは、Visual Studio の機能はアクセスできませんが、使用できます、<xref:System.Windows.FrameworkElement.ContextMenu%2A>ユーザー コントロール内の XAML 要素のプロパティ。 詳細については、次を参照してください。 [ContextMenu](/dotnet/framework/wpf/controls/contextmenu)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="create-the-tool-window-shortcut-menu-package"></a>ツール ウィンドウのショートカット メニューのパッケージを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`TWShortcutMenu`というツール ウィンドウのテンプレートを追加および**ショートカット メニュー**にします。 ツール ウィンドウの作成の詳細については、次を参照してください。[ツール ウィンドウで拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## <a name="specifying-the-shortcut-menu"></a>ショートカット メニューを指定します。  
 このチュートリアルで示すように、ユーザーができるようになどのショートカット メニューは、ツール ウィンドウの背景の塗りつぶしに使用される色の一覧から選択します。  
  
1.  *ShortcutMenuPackage.vsct*guidShortcutMenuPackageCmdSet をという名前の GuidSymbol 要素内の検索、および、ショートカット メニューのショートカット メニューのグループ、およびメニュー オプションを宣言します。 GuidSymbol 要素は、次のようになります。  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  ボタンの要素の直前にメニュー要素を作成し、これで、ショートカット メニューを定義します。  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     ショートカット メニューには、親はありません メニューまたはツールバーの一部ではないためです。  
  
3.  ショートカット メニュー項目を格納するグループの要素を持つグループ要素を作成し、ショートカット メニューの グループに関連付けます。  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  ボタンの要素では、ショートカット メニューに表示される個々 のコマンドを定義します。 このようボタン要素になります。  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  *ShortcutMenuCommand.cs*、コマンド セットの GUID、ショートカット メニューのメニュー項目の定義を追加します。  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     これらは、同じコマンド Id の Symbols セクションで定義されている、 *ShortcutMenuPackage.vsct*ファイル。 コンテキストのグループは含まれませんでのみ必要であるため、 *.vsct*ファイル。  
  
## <a name="implementing-the-shortcut-menu"></a>ショートカット メニューを実装します。  
 このセクションでは、ショートカット メニューのおよびコマンドを実装します。  
  
1.  *ShortcutMenu.cs*、ツール ウィンドウ、メニュー コマンド サービスを取得できますが、コントロールが含まれていることはできません。 次の手順では、メニュー コマンド サービスをユーザー コントロールを使用できるようにする方法を示します。  
  
2.  *ShortcutMenu.cs*次を追加するステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  メニュー コマンド サービスを取得し、メニュー コマンド サービスをコンス トラクターに渡す、コントロールを追加するツール ウィンドウの Initialize() メソッドをオーバーライドします。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  ショートカット メニューのツール ウィンドウ コンス トラクターでは、コントロールを追加する行を削除します。 コンス トラクターは、次のようになります。  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  *ShortcutMenuControl.xaml.cs*、メニュー コマンド サービスのプライベート フィールドを追加し、メニュー コマンド サービスを実行するコントロールのコンス トラクターを変更します。 メニュー コマンド サービスを使用し、コンテキスト メニューのコマンドを追加できます。 ShortcutMenuControl コンス トラクターは、次のコードのようになります。 コマンド ハンドラーは、後で定義されます。  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  *ShortcutMenuControl.xaml*、追加、<xref:System.Windows.UIElement.MouseRightButtonDown>最上位レベルのイベント<xref:System.Windows.Controls.UserControl>要素。 XAML ファイルは、次のようになります。  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  *ShortcutMenuControl.xaml.cs*、イベント ハンドラーのスタブを追加します。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  次の追加、同じファイルにステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. 実装、`MyToolWindowMouseRightButtonDown`イベントとして次のとおりです。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuCommand.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     これを作成、<xref:System.ComponentModel.Design.CommandID>オブジェクトのショートカット メニューの マウスのクリックの場所を識別およびを使用して、その場所でショートカット メニューを開きます、<xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A>メソッド。  
  
10. コマンド ハンドラーを実装します。  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuCommand.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuCommand.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuCommand.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     1 つのメソッドが識別することでメニュー項目のすべてのイベントを処理するこの例では、<xref:System.ComponentModel.Design.CommandID>と背景色を適宜設定します。 メニュー項目には、関連のないコマンドが含まれていた、作成した場合はコマンドごとに個別のイベント ハンドラー。  
  
## <a name="test-the-tool-window-features"></a>ツール ウィンドウの機能をテストします。  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  実験用インスタンスでは、次のようにクリックします。**ビュー/その他の Windows**、 をクリックし、**ショートカット メニュー**します。 これを行うと、ツール ウィンドウが表示されます。  
  
3.  ツール ウィンドウの本文で右クリックします。 色のリストを持つショートカット メニューを表示する必要があります。  
  
4.  ショートカット メニューの 色をクリックします。 ツール ウィンドウの背景色は、選択した色を変更しないでください。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)