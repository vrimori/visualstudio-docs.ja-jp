---
title: "Visual Studio のメニュー バーにメニューを追加します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メニュー、最上位レベルの作成"
  - "トップレベルのメニュー"
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 51
caps.handback.revision: 51
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio のメニュー バーにメニューを追加します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

このチュートリアルでは、Visual Studio 統合開発環境 \(IDE\) のメニュー バーにメニューを追加する方法を示します。 など、IDE のメニュー バーにメニュー項目が含まれています **ファイル**, 、**編集**, 、**ビュー**, 、**ウィンドウ**, 、および **ヘルプ**します。  
  
 Visual Studio のメニュー バーに新しいメニューを追加する前に、コマンドは、既存のメニュー内に配置する必要があるかどうかを検討してください。 コマンド配置の詳細については、次を参照してください。 [メニューと Visual Studio のコマンド](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)します。  
  
 メニューは、プロジェクトの .vsct ファイルで宣言されます。 メニューおよび .vsct ファイルの詳細については、次を参照してください。 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
 このチュートリアルを完了すると、という名前のメニューを作成することができます **TestMenu** を 1 つのコマンドが含まれています。  
  
## 必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、「[Visual Studio SDK をインストールします。](../extensibility/installing-the-visual-studio-sdk.md)」を参照してください。  
  
## カスタム コマンド項目テンプレートを持つ VSIX プロジェクトを作成します。  
  
1.  という名前の VSIX プロジェクトを作成する `TopLevelMenu`です。 VSIX プロジェクトのテンプレートを見つけることができます、 **新しいプロジェクト** \] ダイアログ ボックス \[ **Visual c\#** \/ **拡張**します。  詳細については、「[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)」を参照してください。  
  
2.  プロジェクトを開いたら、という名前のカスタム コマンド項目テンプレートを追加 **TestCommand**します。**ソリューション エクスプ ローラー**, プロジェクト ノードを右クリックして、選択 **追加\/\[新しい項目の**します。**新しい項目の追加** ダイアログ ボックスに移動 **Visual c\#\/機能拡張** を選択して **にカスタム コマンド**します。**名** ウィンドウの下部にあるフィールドに、コマンド ファイルの名前を変更する **TestCommand.cs**します。  
  
## IDE のメニュー バーでメニューを作成します。  
  
#### メニューを作成するには  
  
1.  **ソリューション エクスプ ローラー**, 、TestCommandPackage.vsct を開きます。  
  
     ファイルの最後には、いくつかの \< GuidSymbol \> ノードを含む \< シンボル \> ノードがあります。 GuidTestCommandPackageCmdSet という名前のノードで新しいシンボルを追加します。  
  
    ```xml  
    <IDSymbol name="TopLevelMenu" value="0x1021"/>  
    ```  
  
2.  \< グループ \> の前に、\< コマンド \> ノードには、空の \< メニュー \> ノードを作成します。 \< メニュー \>\] ノードで、\< Menu \> ノードを追加します。  
  
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
  
     `guid` と `id` \] メニューの値が一連のコマンドと特定のメニューを一連のコマンドで指定します。  
  
     `guid` と `id` 親の値は、ツールとアドインのメニューを含む Visual Studio のメニュー バーのセクションに、メニューを配置します。  
  
     値、 `CommandName` テキストがメニュー項目に表示される文字列を指定します。  
  
3.  \< グループ \> セクションでは、\< グループ \> を見つけ、\< 親 \> 要素に追加したメニューへを変更します。  
  
    ```c#  
    <Groups>  
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>  
          </Group>  
        </Groups>  
    ```  
  
     これにより、新しいメニューのグループの一部です。  
  
4.  検索、 `Buttons` セクションです。 注意して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] パッケージ テンプレートが生成される、 `Button` に設定する親を持つ要素 `MyMenuGroup`します。 その結果、このコマンドは、メニューに表示されます。  
  
## 構築および拡張機能のテスト  
  
1.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスのインスタンスが表示されます。  
  
2.  実験用インスタンスのメニュー バーを含める必要があります、 **TestMenu** メニュー。  
  
3.  **TestMenu** \] メニューのをクリックして **Test コマンドを呼び出す**します。  
  
     メッセージ ボックスが表示され、"TestCommand パッケージ内部 TopLevelMenu.TestCommand.MenuItemCallback\(\)"メッセージを表示する必要があります。 これは、新しいコマンドの動作を示します。  
  
## 参照  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)