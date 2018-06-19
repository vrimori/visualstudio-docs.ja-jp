---
title: ソリューション エクスプ ローラーのツールバーにコマンドを追加する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f6f732900ff3e73decb1dc01d5c131e26ba50669
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107388"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>ソリューション エクスプ ローラーのツールバーにコマンドを追加します。
このチュートリアルで説明するためのボタンを追加する方法、**ソリューション エクスプ ローラー**ツールバー。  
  
 ツールバーまたはメニューのいずれかのコマンドには、Visual Studio でのボタンは呼び出されます。 このボタンをクリックすると、コマンド ハンドラーでコードが実行されます。 通常、関連するコマンドは化、1 つのグループが形成されます。 メニューまたはツールバーは、グループのコンテナーとして機能します。 優先順位では、グループ内の個々 のコマンドが表示されるメニューまたはツールバーの順序を決定します。 ボタンは、その可視性を制御することで、ツールバーやメニューに表示されるされないようにできます。 記載されているコマンド、 `<VisibilityConstraints>` .vsct ファイルのセクションは、関連付けられたコンテキストでのみが表示されます。 可視性は、グループに適用できません。  
  
 メニューのツールバーのコマンド、および .vsct ファイルの詳細については、次を参照してください。[コマンド、メニュー、およびツールバー](../extensibility/internals/commands-menus-and-toolbars.md)です。  
  
> [!NOTE]
>  コマンド テーブル (.ctc) の構成ファイルではなく XML コマンド テーブル (.vsct) ファイルを使用して、Vspackage でのメニューとコマンドの表示方法を定義します。 詳細については、「 [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 Visual Studio 2015 以降、ダウンロード センターから Visual Studio SDK をインストールすることはできません。 これは Visual Studio のセットアップにオプション機能として含まれるようになりました。 また、後から VS SDK をインストールすることもできます。 より詳細な情報については 、[Visual Studio SDK のインストール](../extensibility/installing-the-visual-studio-sdk.md) に関する記事を参照してください。  
  
## <a name="creating-an-extension-with-a-menu-command"></a>メニュー コマンドを使用して、拡張機能の作成  
 という名前の VSIX プロジェクトを作成する`SolutionToolbar`です。 という名前のメニュー コマンド項目テンプレートを追加**ToolbarButton**です。 これを行う方法については、次を参照してください。[メニュー コマンドを使用して、拡張機能の作成](../extensibility/creating-an-extension-with-a-menu-command.md)です。  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>ソリューション エクスプ ローラーのツールバーにボタンの追加  
 チュートリアルのこのセクションでは、ボタンを追加する方法を示します、**ソリューション エクスプ ローラー**ツールバー。 このボタンをクリックすると、コールバック メソッドでコードが実行されます。  
  
1.  ToolbarButtonPackage.vsct ファイルに移動、`<Symbols>`セクションです。 `<GuidSymbol>`ノードには、メニュー グループおよびパッケージ テンプレートによって生成されたコマンドが含まれています。 追加、`<IDSymbol>`要素にコマンドを保持するグループを宣言するには、このノードをします。  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2.  `<Groups>`  セクションで、既存のグループのエントリの後に新しいグループを定義宣言した前の手順でします。  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     設定を親の GUID:ID ペア`guidSHLMainMenu`と`IDM_VS_TOOL_PROJWIN`により、このグループに追加、**ソリューション エクスプ ローラー**ツールバー、および優先度の高い値の設定、他のコマンド グループの後に配置します。  
  
3.  `<Buttons>`セクションで、生成されたの親の ID を変更する`<Button>`前の手順で定義されているグループを反映するように入力します。 変更された`<Button>`要素は次のようになります。  
  
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
  
     **ソリューション エクスプ ローラー**ツールバーは、既存のボタンの右側に新しいコマンド ボタンを表示する必要があります。 ボタンのアイコンは、取り消し線です。  
  
5.  新規作成 ボタンをクリックします。  
  
     ダイアログ ボックスに、メッセージ**ToolbarButtonPackage 内 SolutionToolbar.ToolbarButton.MenuItemCallback()** が表示されます。  
  
## <a name="controlling-the-visibility-of-a-button"></a>ボタンの表示を制御します。  
 このチュートリアルのこのセクションでは、ツールバーのボタンの表示を制御する方法を示します。 内の 1 つまたは複数のプロジェクトにコンテキストを設定して、`<VisibilityConstraints>`セクション SolutionToolbar.vsct ファイルの表示のみのプロジェクトまたは開いているときにボタンを制限します。  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>1 つまたは複数のプロジェクトが開いているときに、ボタンを表示するには  
  
1.  `<Buttons>`セクション ToolbarButtonPackage.vsct の 2 つのコマンド フラグを追加すると、既存`<Button>`要素、between、`<Strings>`と`<Icons>`タグ。  
  
    ```xml  
    <CommandFlag>DefaultInvisible</CommandFlag>  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
     `DefaultInvisible`と`DynamicVisibility`ようにフラグを設定する必要がありますでそのエントリ、`<VisibilityConstraints>`セクションを反映します。  
  
2.  作成、`<VisibilityConstraints>`を持つ 2 つのセクション`<VisibilityItem>`エントリです。 終了した直後に新しいセクションを配置`</Commands>`タグ。  
  
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
  
     可視性の各項目は、指定したボタンを表示する条件を表します。 複数の条件を適用するには、同じボタンに対して複数のエントリを作成する必要があります。  
  
3.  プロジェクトをビルドし、デバッグを開始します。 実験用インスタンスが表示されます。  
  
     **ソリューション エクスプ ローラー**ツールバーに取り消し線付きのボタンが含まれていません。  
  
4.  プロジェクトを含む任意のソリューションを開きます。  
  
     取り消しボタンは、ツールバーの既存のボタンの右側に表示されます。  
  
5.  **ファイル** メニューのをクリックして**ソリューションを閉じる**です。 ツールバーのボタンが表示されなくなります。  
  
 ボタンの可視性がによって制御される[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage が読み込まれるまでです。 VSPackage が読み込まれた後、ボタンの可視性は、VSPackage によって制御されます。  詳細については、次を参照してください。 [Menucommand とします。OleMenuCommands](../extensibility/menucommands-vs-olemenucommands.md)です。  
  
## <a name="see-also"></a>関連項目  
 [コマンド、メニュー、およびツール バー](../extensibility/internals/commands-menus-and-toolbars.md)