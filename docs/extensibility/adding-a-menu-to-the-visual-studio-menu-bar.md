---
title: Visual Studio のメニュー バーにメニューを追加する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b4201e6c09037259888290312c4dce616f77459
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988312"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Visual Studio のメニュー バー メニューに追加します。
このチュートリアルでは、Visual Studio 統合開発環境 (IDE) のメニュー バーにメニューを追加する方法を示します。 IDE のメニュー バーには、**ファイル**、**編集**、**ビュー**、**ウィンドウ**、および**ヘルプ**のようなメニュー項目が含まれています。  

 Visual Studio のメニュー バーに新しいメニューを追加する前に、コマンドは、既存のメニュー内に配置する必要があるかどうかを検討してください。 コマンド配置の詳細については、次を参照してください。 [Visual Studio のメニューとコマンド](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)します。  
  
 メニューが宣言されている、 *.vsct*プロジェクトのファイル。 メニューの詳細については、 *.vsct*ファイルを参照してください[コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 このチュートリアルを完了すると、という名前のメニューを作成することができます**TestMenu** 1 つのコマンドを格納しています。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 詳細については、"[Visual Studio SDK をインストール](../extensibility/installing-the-visual-studio-sdk.md)"を参照してください。  
  
## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>カスタム コマンド項目テンプレートを持つ VSIX プロジェクトを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する`TopLevelMenu`します。 VSIX プロジェクト テンプレートを見つけることができます、**新しいプロジェクト**] ダイアログ ボックス [ **Visual c#** / **Extensibility**します。  詳細については、次を参照してください。[メニュー コマンドを使用して拡張機能を作成する](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
2.  という名前のカスタム コマンド項目テンプレートを追加、プロジェクトが開いたら、 **TestCommand**します。 **ソリューション エクスプ ローラー**でプロジェクト ノードを右クリックし、選択**追加/新しい項目の**します。 **新しい項目の追加**ダイアログ ボックスに移動して**Visual c#/機能拡張**選択と**カスタム コマンド**。 **名前**ウィンドウの下部にあるフィールドに、コマンド ファイル名を変更して*TestCommand.cs*します。  
  
## <a name="create-a-menu-on-the-ide-menu-bar"></a>IDE のメニュー バーにメニューを作成します。  
  
1. **ソリューション エクスプ ローラー**オープン*TestCommandPackage.vsct*します。  
  
    ファイルの最後では、\<シンボル > いくつか含まれているノード\<GuidSymbol > ノード。 GuidTestCommandPackageCmdSet という名前のノード、としては、次のように、新しいシンボルを追加します。  
  
   ```xml  
   <IDSymbol name="TopLevelMenu" value="0x1021"/>  
   ```  
  
2. 空の作成\<メニュー > 内のノード、\<コマンド > ノード、直前に\<グループ >。 \<メニュー > ノードを追加、\<メニュー > 次のように、ノード。  
  
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
  
    `guid`と`id`コマンド セットで、コマンド セットと、特定のメニューにメニューの値が指定されます。  
  
    `guid`と`id`親の値は、ツールとアドインのメニューを含む Visual Studio のメニュー バーのセクションに、メニューを配置します。  
  
    値、`CommandName`文字列は、メニュー項目のテキストが表示されることを指定します。  
  
3. \<グループ > セクションで、検索、\<グループ > を変更して、\<親 > 要素を追加したメニューをポイントします。  
  
   ```csharp  
   <Groups>  
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
         </Group>  
       </Groups>  
   ```  
  
    これにより、新しいメニューのグループの一部です。  
  
4. 検索、`Buttons`セクション。 注意、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージ テンプレートが生成、`Button`をその親に設定を持つ要素`MyMenuGroup`します。 その結果、このコマンドは、メニューに表示されます。  
  
## <a name="build-and-test-the-extension"></a>ビルドし、テストの拡張機能  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスのインスタンスが表示されます。  
  
2.  実験用インスタンスのメニュー バーを含める必要があります、 **TestMenu**メニュー。  
  
3.  **TestMenu**  メニューのをクリックして**テスト コマンドを呼び出す**します。  
  
     メッセージ ボックスが表示され、"TestCommand パッケージ内で TopLevelMenu.TestCommand.MenuItemCallback()"メッセージを表示する必要があります。 これは、新しいコマンドが動作することを示します。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)
