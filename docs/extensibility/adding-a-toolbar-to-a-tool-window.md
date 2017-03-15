---
title: "ツール ウィンドウに、ツールバーを追加する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 48
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 80f8d2e3d689b05680c5d43a0d4b26f17d9a88ce
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar-to-a-tool-window"></a>ツール ウィンドウに、ツールバーを追加します。
このチュートリアルでは、ツール ウィンドウにツールバーを追加する方法を示します。  
  
 ツールバーは、水平または垂直方向のストリップで、コマンドにバインドされているボタンが含まれています。 ツール ウィンドウのツールバーの長さは、常に、ツールバーのドッキング位置によって、ツール ウィンドウの高さまたは幅と同じです。  
  
 IDE で、ツールバーとは異なりツール ウィンドウのツールバー必要がありますドッキングありことはできません、移動やカスタマイズします。 VSPackage が umanaged コードで記述されている場合は、いずれかの端にツールバーをドッキングできます。  
  
 ツールバーを追加する方法の詳細については、次を参照してください。[ツールバーを追加する](../extensibility/adding-a-toolbar.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>ツール ウィンドウのツールバーの作成  
  
1.  という名前の VSIX プロジェクトを作成する`TWToolbar`という名前の両方のメニュー コマンドを含む**TWTestCommand**という名前のツール ウィンドウと**TestToolWindow**します。 詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)と[ツール ウィンドウで、拡張機能を作成する](../extensibility/creating-an-extension-with-a-tool-window.md)です。 ツール ウィンドウのテンプレートを追加する前に、コマンドの項目テンプレートを追加する必要があります。  
  
2.  TWTestCommandPackage.vsct、Symbols セクションを探します。 GuidTWTestCommandPackageCmdSet をという名前の GuidSymbol ノードで次のようにツールバーとツールバーのグループを宣言します。  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3.  上部にある、`Commands`セクションで、作成、`Menus`セクションです。 追加、`Menu`要素で、ツールバーを定義します。  
  
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
  
     ツールバーは、サブメニューのような入れ子にすることはできません。 そのため、親を割り当てるにはありません。 さらに、されませんが、優先順位を設定するため、ユーザーがツールバーを移動できます。 通常、ツールバーの初期配置がプログラムを使用して、定義されているが、ユーザーがそれ以降の変更は保持します。  
  
4.  Groups セクションでは、ツールバーのコマンドが所属するグループを定義します。  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5.  ボタン セクションでは、ツールバーを表示するためにツールバー グループに既存の Button 要素の親を変更します。  
  
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
  
     新しいツールバーがツール ウィンドウに自動的に追加されていないため、ツールバーを明示的に追加する必要があります。 これについては、次のセクションで説明します。  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>ツール ウィンドウに、ツールバーを追加します。  
  
1.  TWTestCommandPackageGuids.cs では、次の行を追加します。  
  
    ```c#  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2.  TestToolWindow.cs で次のコードを追加ステートメントを使用します。  
  
    ```c#  
    using System.ComponentModel.Design;  
    ```  
  
3.  TestToolWindow コンス トラクターでは、次の行を追加します。  
  
    ```c#  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>ツール ウィンドウで、ツールバーのテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 Visual Studio の実験用インスタンスが表示されます。  
  
2.  **ビュー/その他のウィンドウ** メニューのをクリックして**テスト ツール ウィンドウ**ツール ウィンドウを表示します。  
  
     タイトルのすぐ下のツール ウィンドウの上部のツールバー (次のように既定のアイコン) の左に表示されます。  
  
3.  ツールバーで、メッセージを表示するアイコンをクリックして**TWTestCommandPackage 内 TWToolbar.TWTestCommand.MenuItemCallback()**します。  
  
## <a name="see-also"></a>関連項目  
 [ツールバーを追加します。](../extensibility/adding-a-toolbar.md)
