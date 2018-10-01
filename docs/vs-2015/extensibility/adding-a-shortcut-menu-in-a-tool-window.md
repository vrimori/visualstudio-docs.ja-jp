---
title: ツール ウィンドウのショートカット メニューを追加する |Microsoft Docs
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
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
caps.latest.revision: 38
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3a09e288771702ec6c5abde1838d8139e151504d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537440"
---
# <a name="adding-a-shortcut-menu-in-a-tool-window"></a>ツール ウィンドウへのショートカット メニューの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ツール ウィンドウのショートカット メニューを追加する](https://docs.microsoft.com/visualstudio/extensibility/adding-a-shortcut-menu-in-a-tool-window)します。  
  
このチュートリアルでは、ツール ウィンドウのショートカット メニューを配置します。 ショートカット メニューは、ユーザーは、ボタン、テキスト ボックスに、またはウィンドウの背景を右クリックしたときに表示されるメニューです。 ショートカット メニューのコマンドは、その他のメニューまたはツールバーでコマンドと同じ動作します。 ショートカット メニューをサポートするために .vsct ファイルで指定して、マウスの右クリックに応答に表示します。  
  
 ツール ウィンドウから継承するカスタム ツール ウィンドウのクラスでの WPF ユーザー コントロールから成る<xref:Microsoft.VisualStudio.Shell.ToolWindowPane>します。  
  
 このチュートリアルでは、Visual Studio のメニューとして、.vsct ファイルでのメニュー項目を宣言し、ツール ウィンドウを定義するクラスで実装する Managed Package Framework を使用してショートカット メニューを作成する方法を示します。 このアプローチには、Visual Studio コマンド、UI 要素、およびオートメーション オブジェクト モデルへのアクセスが容易になります。  
  
 また場合、ショートカット メニューでは、Visual Studio の機能はアクセスできませんが、使用できます、<xref:System.Windows.FrameworkElement.ContextMenu%2A>ユーザー コントロール内の XAML 要素のプロパティ。 詳細については、次を参照してください。 [ContextMenu](http://msdn.microsoft.com/library/2f40b2bb-b702-4706-9fc4-10bcfd7cc35d)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-the-tool-window-shortcut-menu-package"></a>ツール ウィンドウのショートカット メニューのパッケージを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`TWShortcutMenu`というツール ウィンドウのテンプレートを追加および**ショートカット メニュー**にします。 ツール ウィンドウの作成の詳細については、次を参照してください。[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。  
  
## <a name="specifying-the-shortcut-menu"></a>ショートカット メニューを指定します。  
 このチュートリアルで示すように、ユーザーができるようになどのショートカット メニューは、ツール ウィンドウの背景の塗りつぶしに使用される色の一覧から選択します。  
  
1.  ShortcutMenuPackage.vsct では、という名前の guidShortcutMenuPackageCmdSet、GuidSymbol 要素を検索し、ショートカット メニューのショートカット メニューのグループ、およびメニュー オプションを宣言します。 GuidSymbol 要素は、次のようになります。  
  
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
  
5.  ShortcutMenuPackageGuids.cs、コマンドの定義セットの GUID、ショートカット メニューのメニュー項目を追加します。  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     これらは、ShortcutMenuPackage.vsct ファイルの Symbols セクションで定義されている同じコマンド Id です。 コンテキストのグループは含まれません、.vsct ファイルでのみ必要であるためです。  
  
## <a name="implementing-the-shortcut-menu"></a>ショートカット メニューを実装します。  
 このセクションでは、ショートカット メニューのおよびコマンドを実装します。  
  
1.  ShortcutMenu.cs、ツール ウィンドウ、メニュー コマンド サービスを取得できますが、コントロールが含まれていることはできません。 次の手順では、メニュー コマンド サービスをユーザー コントロールを使用できるようにする方法を示します。  
  
2.  ShortcutMenu.cs で、次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  メニュー コマンド サービスを取得し、メニュー コマンド サービスをコンス トラクターに渡して、コントロールを追加するツール ウィンドウの Initialize() メソッドをオーバーライドします。  
  
    ```csharp  
    protected override void Initialize()  
    {  
        commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
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
  
5.  ShortcutMenuControl.xaml.cs、メニュー コマンド サービスのプライベート フィールドを追加し、メニュー コマンド サービスを実行するコントロールのコンス トラクターを変更します。 メニュー コマンド サービスを使用し、コンテキスト メニューのコマンドを追加できます。 ShortcutMenuControl コンス トラクターは、次のコードのようになります。 コマンド ハンドラーは、後で定義されます。  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuPackageGuids.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuPackageGuids.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuPackageGuids.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  ShortcutMenuControl.xaml で追加、<xref:System.Windows.UIElement.MouseRightButtonDown>最上位レベルのイベント<xref:System.Windows.Controls.UserControl>要素。 XAML ファイルは、次のようになります。  
  
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
  
7.  ShortcutMenuControl.xaml.cs では、イベント ハンドラーのスタブを追加します。  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
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
                new Guid(ShortcutMenuPackageGuids.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuPackageGuids.ColorMenu);  
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
            case ShortcutMenuPackageGuids.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuPackageGuids.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuPackageGuids.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     1 つのメソッドが識別することでメニュー項目のすべてのイベントを処理するこの例では、<xref:System.ComponentModel.Design.CommandID>と背景色を適宜設定します。 メニュー項目には、関連のないコマンドが含まれていた、作成した場合はコマンドごとに個別のイベント ハンドラー。  
  
## <a name="testing-the-tool-window-features"></a>ツール ウィンドウの機能をテストします。  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
2.  実験用インスタンスでは、次のようにクリックします。**ビュー/その他の Windows**、 をクリックし、**ショートカット メニュー**します。 これを行うと、ツール ウィンドウが表示されます。  
  
3.  ツール ウィンドウの本文で右クリックします。 色のリストを持つショートカット メニューを表示する必要があります。  
  
4.  ショートカット メニューの 色をクリックします。 ツール ウィンドウの背景色は、選択した色を変更しないでください。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)   
 [サービスの使用と提供](../extensibility/using-and-providing-services.md)

