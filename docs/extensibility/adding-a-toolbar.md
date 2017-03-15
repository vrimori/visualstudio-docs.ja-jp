---
title: "ツールバーの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 38
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
ms.openlocfilehash: e6b9b6a5ce384112464d0f768c35bf7b5c57a589
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-toolbar"></a>ツールバーを追加します。
このチュートリアルでは、Visual Studio IDE にツールバーを追加する方法を示します。  
  
 ツールバーは、水平または垂直方向のストリップで、コマンドにバインドされているボタンが含まれています。 実装によって IDE でツールバーの位置を変更、IDE のメイン ウィンドウの任意の辺にドッキングされておりしたり他のウィンドウの前にとどまって行われました。  
  
 ユーザーがさらに、コマンドをツールバーに追加するかを使用してそこから削除する、**カスタマイズ** ダイアログ ボックス。 通常、vspackages にあるツールバーは、ユーザーがカスタマイズできます。 IDE は、すべてのカスタマイズを処理し、VSPackage がコマンドに応答します。 VSPackage をコマンドが物理的にしておく必要はありません。  
  
 メニューの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-an-extension-with-a-toolbar"></a>ツールバーと拡張機能の作成  
 という名前の VSIX プロジェクトを作成する`IDEToolbar`です。 という名前のメニュー コマンド項目テンプレートを追加**ToolbarTestCommand**します。 これを行う方法については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="creating-a-toolbar-for-the-ide"></a>IDE のツールバーの作成  
  
1.  ToolbarTestCommandPackage.vsct、Symbols セクションを探します。 要素では、GuidSymbol guidToolbarTestCommandPackageCmdSet という名前は、次のように、ツールバーとツール バー グループの宣言を追加します。  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2.  コマンドのセクションの上部にあるメニュー」のセクションを作成します。 メニュー セクションでは、ツールバーの定義] メニューの [要素を追加します。  
  
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
  
     ツールバーは、サブメニューのような入れ子にすることはできません。 そのため、親グループを割り当てるにはありません。 さらに、されませんが、優先順位を設定するため、ユーザーがツールバーを移動できます。 通常、ツールバーの初期配置がプログラムを使用して、定義されているが、ユーザーがそれ以降の変更は保持します。  
  
3.  [グループ](../extensibility/groups-element.md) セクションで、既存のグループのエントリの後の定義、[グループ](../extensibility/group-element.md)ツールバーのコマンドを格納する要素。  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4.  ツールバーの表示ボタンを作成します。 [ボタン] セクションで、ツールバーのボタンで、親ブロックを置き換えます。 そのボタンのブロックは、次のようになります。  
  
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
  
7.  ファイル アイコンには、検索の右側にアイコンとしては、ツールバーが表示されます。 というメッセージ ボックスが表示のアイコンをクリックすると**ToolbarTestCommandPackage します。IDEToolbar.ToolbarTestCommand.MenuItemCallback() 内**します。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)
