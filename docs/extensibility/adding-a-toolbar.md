---
title: ツールバーの追加 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 6fa301a146dec9e7ee9b2f7edcaa6480e6bf5fef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934743"
---
# <a name="add-a-toolbar"></a>ツールバーを追加します。
このチュートリアルでは、Visual Studio IDE にツールバーを追加する方法を示します。  
  
 ツールバーは、水平方向または垂直方向のストリップで、コマンドにバインドされているボタンが含まれています。 実装によって IDE でツールバーの位置を変更、IDE のメイン ウィンドウの任意の辺にドッキングしたり他のウィンドウの前に常に加えられました。  
  
 ユーザーがさらに、ツールバーにコマンドを追加またはを使用してから、削除、**カスタマイズ** ダイアログ ボックス。 通常、Vspackage では、ツールバーは、ユーザーがカスタマイズできます。 IDE がカスタマイズをすべてを処理し、VSPackage がコマンドに応答します。 VSPackage は、コマンドが物理的に配置されている場所を認識する必要はありません。  
  
 メニューの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-an-extension-with-a-toolbar"></a>ツールバーと拡張機能を作成します。  
 という名前の VSIX プロジェクトを作成する`IDEToolbar`します。 という名前のメニュー コマンド項目テンプレートを追加**ToolbarTestCommand**します。 これを行う方法については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="create-a-toolbar-for-the-ide"></a>IDE のツールバーを作成します。  
  
1.  *ToolbarTestCommandPackage.vsct*、Symbols セクションを探します。 GuidToolbarTestCommandPackageCmdSet をという名前の GuidSymbol 要素では、次のようにツールバーとツールバー、グループの宣言を追加します。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  コマンドのセクションの上部にあるメニューのセクションを作成します。 メニュー セクションで、ツールバーを定義するには、メニュー要素を追加します。  
  
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
  
     ツールバーは、サブメニューのような入れ子にすることはできません。 そのため、親グループを割り当てるにはありません。 またがありません、優先順位を設定するため、ユーザーがツールバーを移動できます。 通常、ツールバーの初期配置がプログラムで定義されているが、ユーザーがそれ以降の変更が保存されます。  
  
3.  [グループ](../extensibility/groups-element.md)セクションでは、既存のグループ エントリの後に定義、[グループ](../extensibility/group-element.md)ツールバーのコマンドを格納する要素。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  ツールバーの表示 ボタンを作成します。 [ボタン] セクションで、ツールバーにボタンの親ブロックに置き換えます。 結果として得られるボタン ブロックは、このようになります。  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     既定では、ツールバーにコマンドが存在しない場合に表示されません。  
  
5.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
6.  ツールバーの一覧を取得する Visual Studio のメニュー バーを右クリックします。 選択**テスト ツールバー**します。  
  
7.  ファイル アイコンには、検索の右側にアイコンとして、ツールバーがわかります。 示すメッセージ ボックスが表示アイコンをクリックすると**ToolbarTestCommandPackage します。IDEToolbar.ToolbarTestCommand.MenuItemCallback() 内**します。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)