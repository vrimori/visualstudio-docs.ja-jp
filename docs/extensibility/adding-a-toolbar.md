---
title: ツールバーを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4a9a28ef3fced7cc2dab1f14b2854f2ca27d362
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-toolbar"></a>ツールバーを追加します。
このチュートリアルでは、Visual Studio IDE にツールバーを追加する方法を示します。  
  
 ツールバーは、水平または垂直方向のストリップをコマンドにバインドされているボタンを含むです。 実装によって IDE でツールバーは、位置、IDE のメイン ウィンドウの任意の辺にドッキングされてまたは他のウィンドウの前に常に加えられました。  
  
 さらに、ユーザーがコマンド、ツールバーを追加したりを使用してそこから削除することができます、**カスタマイズ** ダイアログ ボックス。 通常、Vspackage のツールバーは、ユーザーがカスタマイズできます。 IDE は、すべてのカスタマイズを処理し、VSPackage がコマンドに応答します。 VSPackage はコマンドが物理的に配置されている次のトピックにはありません。  
  
 メニューの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>ツールバーと拡張機能の作成  
 という名前の VSIX プロジェクトを作成する`IDEToolbar`です。 という名前のメニュー コマンド項目テンプレートを追加**ToolbarTestCommand**です。 これを行う方法については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>IDE のツールバーの作成  
  
1.  ToolbarTestCommandPackage.vsct で、[シンボル] セクションを探します。 要素に、GuidSymbol guidToolbarTestCommandPackageCmdSet をという名前、追加のツールバーとツールバーのグループでは、宣言には、次のようにします。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  コマンドのセクションの上部にある、メニュー」のセクションを作成します。 ツールバーを定義するメニュー セクションには、メニュー要素を追加します。  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     ツールバーは、サブメニューのような入れ子にすることはできません。 そのため、親グループを割り当てるにはありません。 またがありません、優先順位を設定するため、ユーザーがツールバーを移動できます。 通常、ツールバーの初期配置が、プログラムで定義されているが、ユーザーが後続の変更は保持します。  
  
3.  [グループ](../extensibility/groups-element.md) セクションで、既存のグループのエントリを定義、[グループ](../extensibility/group-element.md)ツールバーのコマンドを格納する要素。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  ツールバーの表示ボタンを作成します。 [ボタン] セクションで、ボタンをツールバーで、親ブロックを置き換えます。 結果として得られるボタン ブロックは、次のようになります。  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     既定では、ツールバーには、コマンドが存在しない場合に表示されません。  
  
5.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6.  ツールバーの一覧を取得する Visual Studio のメニュー バーを右クリックします。 選択**テスト ツールバー**です。  
  
7.  ファイル アイコンには、検索の右側にアイコンとしては、ツールバーが表示されます。 示すメッセージ ボックスが表示されます、アイコンをクリックすると**ToolbarTestCommandPackage です。IDEToolbar.ToolbarTestCommand.MenuItemCallback() 内**です。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)