---
title: ツール ウィンドウにツールバーの追加 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2dfb26dd77a3117f40f82fdb80669a2e849e6c94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755167"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>ツール ウィンドウへのツールバーの追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、ツール ウィンドウにツールバーを追加する方法を示します。  
  
 ツールバーは、水平方向または垂直方向のストリップで、コマンドにバインドされているボタンが含まれています。 ツール ウィンドウのツールバーの長さは、常に幅または、ツールバーのドッキング先に応じて、ツール ウィンドウの高さと同じです。  
  
 IDE でツールバーとは異なりでツール ウィンドウのツールバーをする必要がありますドッキング、移動またはできませんカスタマイズ。 Umanaged コードで、VSPackage が書き込まれた場合、ツールバーがいずれかの端にドッキングできます。  
  
 ツールバーを追加する方法の詳細については、次を参照してください。[ツールバーの追加](../extensibility/adding-a-toolbar.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>ツール ウィンドウのツールバーの作成  
  
1.  という名前の VSIX プロジェクトを作成する`TWToolbar`という名前の両方をメニュー コマンドを持つ**TWTestCommand**というツール ウィンドウと**TestToolWindow**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)と[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)します。 ツール ウィンドウのテンプレートを追加する前に、コマンドの項目テンプレートを追加する必要があります。  
  
2.  TWTestCommandPackage.vsct の Symbols セクションを探します。 GuidTWTestCommandPackageCmdSet をという名前の GuidSymbol ノードで次のようにツールバーとツールバーのグループを宣言します。  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  上部にある、`Commands`セクションで、作成、`Menus`セクション。 追加、`Menu`ツールバーを定義する要素。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     ツールバーは、サブメニューのような入れ子にすることはできません。 そのため、親を割り当てるにはありません。 またがありません、優先順位を設定するため、ユーザーがツールバーを移動できます。 通常、ツールバーの初期配置がプログラムで定義されているが、ユーザーがそれ以降の変更が保存されます。  
  
4.  Groups セクションでは、ツールバーのコマンドを格納するグループを定義します。  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  ボタンのセクションでは既存のボタン要素の親をツールバーのグループに変更して、ツールバーが表示されますようにします。  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     既定では、ツールバーにコマンドが存在しない場合に表示されません。  
  
     新しいツールバーはツール ウィンドウに自動的に追加されませんが、ため、ツールバーを明示的に追加する必要があります。 これについては、次のセクションで説明します。  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>ツール ウィンドウにツールバーを追加します。  
  
1.  TWTestCommandPackageGuids.cs では、次の行を追加します。  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  TestToolWindow.cs で次のコードを追加ステートメントを使用します。  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3.  TestToolWindow コンス トラクターでは、次の行を追加します。  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>ツール ウィンドウで、ツールバーのテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
2.  **ビュー/その他の Windows**  メニューのをクリックして**テスト ToolWindow**ツール ウィンドウを表示します。  
  
     上部のツールバーのような既定のアイコン) がツール ウィンドウのタイトルのすぐ下の左に表示されます。  
  
3.  ツールバーで、メッセージを表示するアイコンをクリックします。 **TWTestCommandPackage 内 TWToolbar.TWTestCommand.MenuItemCallback()** します。  
  
## <a name="see-also"></a>関連項目  
 [ツール バーの追加](../extensibility/adding-a-toolbar.md)

