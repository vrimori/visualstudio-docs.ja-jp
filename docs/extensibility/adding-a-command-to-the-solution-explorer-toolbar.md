---
title: "ソリューション エクスプ ローラーのツールバーにコマンドの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 39
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
ms.openlocfilehash: c5d6e1e597db52e4ba087cd358f1d2bdbd5f208f
ms.lasthandoff: 02/22/2017

---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>ソリューション エクスプ ローラーのツールバーにコマンドの追加
このチュートリアルでは、ボタンを追加する方法、**ソリューション エクスプ ローラー**ツールバーです。  
  
 ツールバーまたはメニューのすべてのコマンドには、Visual Studio でのボタンは呼び出されます。 このボタンをクリックすると、コマンド ハンドラーのコードが実行されます。 通常、関連するコマンドは&1; つのグループ化されます。 メニューまたはツールバーは、グループのコンテナーとして機能します。 優先順位では、グループ内の個々 のコマンドが表示されるメニューまたはツールバーの順序を決定します。 ボタンを防ぐ、可視性を制御することで、ツールバーまたはメニューに表示されていることができます。 記載されているコマンド、 `<VisibilityConstraints>` .vsct ファイルのセクションが関連付けられているコンテキストでのみ表示されます。 可視性は、グループに適用できません。  
  
 メニューのツールバーのコマンドおよび .vsct ファイルの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)します。  
  
> [!NOTE]
>  コマンド テーブル構成 (.ctc) ファイルではなく XML コマンド テーブル (.vsct) ファイルを使用すると、メニューとコマンドが、Vspackage でどのように表示する方法を定義します。 詳細については、次を参照してください。 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、インストールしない、Visual Studio SDK ダウンロード センターからです。 Visual Studio のセットアップのオプション機能として含まれます。 後で、VS SDK をインストールすることもできます。 詳細については、次を参照してください。 [Visual Studio SDK をインストールする](../extensibility/installing-the-visual-studio-sdk.md)です。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して拡張機能の作成  
 という名前の VSIX プロジェクトを作成する`SolutionToolbar`です。 という名前のメニュー コマンド項目テンプレートを追加**ツールバー ・ ボタン**します。 これを行う方法については、次を参照してください。[メニュー コマンドを使用して拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)します。  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>ソリューション エクスプ ローラーのツールバーにボタンの追加  
 このチュートリアルのこのセクションでは、ボタンを追加する方法を示しています、**ソリューション エクスプ ローラー**ツールバーです。 このボタンをクリックすると、コールバック メソッドのコードが実行されます。  
  
1.  ToolbarButtonPackage.vsct ファイルに移動、`<Symbols>`セクションです。 `<GuidSymbol>`ノードには、メニュー グループおよびパッケージのテンプレートによって生成されたコマンドが含まれています。 追加、`<IDSymbol>`コマンドを保持するグループを宣言するには、このノードの要素。  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  `<Groups>`  セクションで、既存のグループの入力後に新しいグループを定義宣言した前の手順でします。  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     親 GUID:ID ペアに設定`guidSHLMainMenu`と`IDM_VS_TOOL_PROJWIN`によりにこのグループが追加、**ソリューション エクスプ ローラー**ツールバーで、優先度の高い値の設定とその他のコマンド グループの後に配置します。  
  
3.  `<Buttons>`セクションで、親の ID を変更、生成された`<Button>`前の手順で定義されているグループを反映するように入力します。 変更された`<Button>`要素は次のようになります。  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
     **ソリューション エクスプ ローラー**既存のボタンの右側に新しいコマンド ボタンがツールバーに表示する必要があります。 [ボタン] アイコンは、取り消し線です。  
  
5.  新規作成 ボタンをクリックします。  
  
     ダイアログ ボックスに、メッセージ**ToolbarButtonPackage 内 SolutionToolbar.ToolbarButton.MenuItemCallback()**が表示されます。  
  
## <a name="controlling-the-visibility-of-a-button"></a>ボタンの表示を制御します。  
 このチュートリアルのこのセクションでは、ツールバーのボタンの表示を制御する方法を示します。 1 つ以上のプロジェクトにコンテキストを設定して、`<VisibilityConstraints>`セクション SolutionToolbar.vsct ファイルの表示のみのプロジェクト、または開いているときにボタンを制限します。  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>1 つまたは複数のプロジェクトが開いているときにボタンを表示するには  
  
1.  `<Buttons>`セクション ToolbarButtonPackage.vsct の&2; つのコマンド フラグを追加すると、既存`<Button>`要素、between、`<Strings>`と`<Icons>`タグ。  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible`と`DynamicVisibility`ようにフラグを設定する必要がそのエントリに、`<VisibilityConstraints>`セクションが有効になります。  
  
2.  作成、`<VisibilityConstraints>`に&2; つのセクション`<VisibilityItem>`エントリです。 終了直後に新しいセクションを置く`</Commands>`タグ。  
  
    ```xml  
    <VisibilityConstraints>  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasSingleProject" />  
        <VisibilityItem guid="guidToolbarButtonPackageCmdSet"  
              id="ToolbarButtonId"  
              context="UICONTEXT_SolutionHasMultipleProjects" />  
    </VisibilityConstraints>  
    ```  
  
     各表示/非表示項目は、指定したボタンを表示する条件を表します。 複数の条件を適用するには、同じボタンの複数のエントリを作成する必要があります。  
  
3.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
     **ソリューション エクスプ ローラー**ツールバーに取り消し線 ボタンが含まれていません。  
  
4.  プロジェクトを含む任意のソリューションを開きます。  
  
     取り消し線 ボタンは、既存のボタンの右側にツールバーが表示されます。  
  
5.  **ファイル** メニューのをクリックして**ソリューションを閉じる**します。 ツールバーのボタンが表示されなくなります。  
  
 によって、ボタンの表示/非表示を制御[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage が読み込まれるまでです。 VSPackage が読み込まれた後、ボタンの表示/非表示は、VSPackage によって制御されます。  詳細については、次を参照してください。[返答 Vs します。OleMenuCommands](../misc/menucommands-vs-olemenucommands.md)します。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニューのおよびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)
