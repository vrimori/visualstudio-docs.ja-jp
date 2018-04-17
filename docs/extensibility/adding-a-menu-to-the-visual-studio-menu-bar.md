---
title: Visual Studio のメニュー バーにメニューを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3a391da85c38176d79a1c77ce8836ce510e8d27e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バーにメニューを追加します。
このチュートリアルでは、Visual Studio 統合開発環境 (IDE) のメニュー バーにメニューを追加する方法を示します。 IDE のメニュー バーには、**ファイル**、**編集**、**ビュー**、**ウィンドウ**、および**ヘルプ**のようなメニュー項目が含まれています。  
  
 Visual Studio のメニュー バーに新規メニューを追加する前に、コマンドは、既存のメニュー内に配置する必要があるかどうかを検討してください。 コマンド配置の詳細については、次を参照してください。[メニューと Visual Studio のコマンド](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)です。  
  
 メニューは、プロジェクトの .vsct ファイルで宣言されます。 メニューと .vsct ファイルの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
 このチュートリアルを完了すると、という名前のメニューを作成することができます**TestMenu** 1 つのコマンドを格納しています。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>カスタム コマンド項目テンプレートを含む VSIX プロジェクトを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`TopLevelMenu`です。 VSIX プロジェクトのテンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** / **Extensibility**です。  詳細については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートの追加**TestCommand**です。 **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**にカスタム コマンド**です。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する**TestCommand.cs**です。  
  
## <a name="creating-a-menu-on-the-ide-menu-bar"></a>IDE のメニュー バーでメニューの作成  
  
#### <a name="to-create-a-menu"></a>メニューを作成するには  
  
1.  **ソリューション エクスプ ローラー**TestCommandPackage.vsct を開きます。  
  
     ファイルの最後には、\<シンボル > いくつか含まれているノード\<GuidSymbol > ノード。 GuidTestCommandPackageCmdSet をという名前のノードでは、次のように、新しいシンボルを追加します。  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  空、作成\<メニュー > 内のノード、\<コマンド > ノード、直前に\<グループ >。 \<メニュー > ノードを追加、\<メニュー > 次のように、ノード。  
  
    ```xml  
    <Menus>  
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">  
            <Parent guid="guidSHLMainMenu"  
                    id="IDG_VS_MM_TOOLSADDINS" />  
            <Strings>  
              <ButtonText>TestMenu</ButtonText>  
              <CommandName>TestMenu</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     `guid`と`id`値 メニューのコマンド セットのコマンド セットと、特定のメニューを指定します。  
  
     `guid`と`id`親の値は、ツールとアドイン メニューを含む Visual Studio のメニュー バーのセクションに、メニューを配置します。  
  
     値、`CommandName`文字列は、テキストはメニュー項目に表示されることを指定します。  
  
3.  \<グループ > セクションで、検索、\<グループ > を変更して、\<親 > 要素を追加しました メニューをポイントします。  
  
    ```csharp  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     これにより、新しいメニューのグループの一部です。  
  
4.  検索、`Buttons`セクションです。 注意して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージ テンプレートが生成された、`Button`をその親に設定を持つ要素`MyMenuGroup`です。 その結果、このコマンドは、メニューに表示されます。  
  
## <a name="building-and-testing-the-extension"></a>ビルドと拡張機能のテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスのインスタンスが表示されます。  
  
2.  実験用インスタンスのメニュー バーを含めることは、 **TestMenu**メニュー。  
  
3.  **TestMenu**  メニューのをクリックして**テスト コマンドを呼び出す**です。  
  
     メッセージ ボックスは表示され、"TestCommand パッケージの内部 TopLevelMenu.TestCommand.MenuItemCallback()"メッセージを表示する必要があります。 これは、新しいコマンドが動作することを示します。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)