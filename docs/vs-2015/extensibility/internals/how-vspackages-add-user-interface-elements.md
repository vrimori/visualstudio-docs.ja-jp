---
title: Vspackage がユーザー インターフェイス要素を追加する方法 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6265edea1044c1ee7be25725268a792d78a79cc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538612"
---
# <a name="how-vspackages-add-user-interface-elements"></a>VSPackage でユーザー インターフェイス要素を追加する方法
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法 VSPackages に追加のユーザー インターフェイス要素](https://docs.microsoft.com/visualstudio/extensibility/internals/how-vspackages-add-user-interface-elements)します。  
  
VSPackage では、ユーザー インターフェイス (UI) 要素、たとえば、メニューのツールバーを追加でき、ツール ウィンドウ、.vsct ファイルを使用して Visual Studio にすることができます。  
  
 UI 要素のデザイン ガイドラインが見つかります[Visual Studio ユーザー エクスペリエンス ガイドライン](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio コマンド テーブルのアーキテクチャ  
 前述のように、コマンド テーブルのアーキテクチャは、上記のアーキテクチャの原則をサポートします。 抽象化、データ構造、およびツールのコマンド テーブルのアーキテクチャの背後にある原則は次のとおりです。  
  
-   項目の 3 つの基本的な種類があります: メニューのコマンド、およびグループ。 メニューは、メニューのサブメニュー、ツールバー、またはツール ウィンドウとして、UI で公開できます。 コマンドは、IDE では、ユーザーが実行できるし、メニューのボタン、リスト ボックス、または他のコントロールとして公開できるようするプロシージャです。 グループは、メニューとコマンドの両方のコンテナーです。  
  
-   各項目は、アイテム、その優先順位の他の項目とその動作を変更するフラグを記述する定義によって指定されます。  
  
-   各項目には、項目の親を表す配置します。 項目は、UI に複数の場所で表示できるようにする、複数の親を指定できます。  
  
     すべてのコマンドは、そのグループ内の唯一の子である場合でも、その親グループが必要です。 すべての標準のメニューは、親グループも必要です。 ツールバーとツール ウィンドウは、独自の親として機能します。 グループは、その親のメインの Visual Studio のメニュー バー、または、メニューのツールバー、またはツール ウィンドウとして設定できます。  
  
### <a name="how-items-are-defined"></a>項目を定義する方法  
 .Vsct ファイルは XML で書式設定します。 .Vsct ファイルでは、パッケージの UI 要素を定義し、IDE でこれらの要素が表示されるを決定します。 すべてのメニューのグループ、またはパッケージ内のコマンドが最初に割り当てられた GUID と ID、`Symbols`セクション。 .Vsct の残りの部分でファイル、各メニューのコマンド、およびグループは、GUID と ID の組み合わせによって識別されます。 次の例は、一般的な`Symbols`セクション、Visual Studio パッケージ テンプレートによって生成されるときに、**メニュー コマンド**テンプレートが選択されて。  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 最上位の要素、`Symbols`セクションは、 [GuidSymbol 要素](../../extensibility/guidsymbol-element.md)します。 `GuidSymbol` 要素は、パッケージとその構成要素を識別するために、IDE で使用される Guid に名をマップします。  
  
> [!NOTE]
>  Guid は、Visual Studio パッケージ テンプレートによって自動的に生成されます。 クリックして、一意の GUID を作成することも**GUID の作成**上、**ツール**メニュー。  
  
 最初の`GuidSymbol`要素"guid [PackageName] Pkg"、パッケージ自体の GUID です。 これは、Visual Studio によってパッケージの読み込みに使用される GUID です。 通常、子要素はありません。  
  
 慣例により、メニューとコマンドでグループ化された 1 秒あたり`GuidSymbol`要素"guid [PackageName] CmdSet"、およびビットマップは、3 つ目では [`GuidSymbol`要素では、"guidImages"。 この規則に準拠する必要はありませんが、各メニューのグループ、コマンド、およびビットマップの子である必要があります、`GuidSymbol`要素。  
  
 2 番目の`GuidSymbol`パッケージ コマンドのセットを表し、要素は、いくつか`IDSymbol`要素。 各[IDSymbol 要素](../../extensibility/idsymbol-element.md)名前に数値の値をマップし、メニューのグループ、または、コマンド セットの一部であるコマンドを表す場合があります。 `IDSymbol` 、3 番目の要素`GuidSymbol`コマンドのアイコンとして使用できる要素の表すビットマップ。 GUID と ID のペアが同じ 2 つの子がありません、アプリケーション内で一意でなければならないため`GuidSymbol`要素には、同じ値を指定します。  
  
### <a name="menus-groups-and-commands"></a>メニューのグループ、およびコマンド  
 メニューのグループ、またはコマンドの GUID と ID を持つ、ときに、IDE に追加できます。 UI 要素はすべて、次のことがあります。  
  
-   A`guid`属性の名前に一致する、`GuidSymbol`で UI 要素が定義されている要素。  
  
-   `id` 、関連付けられている名前に一致する属性`IDSymbol`要素。  
  
     同時に、`guid`と`id`属性を作成、*署名*の UI 要素。  
  
-   A`priority`属性を親メニューまたはグループの UI 要素の位置を決定します。  
  
-   A[親要素](../../extensibility/parent-element.md)を持つ`guid`と`id`親メニューまたはグループの署名を指定する属性。  
  
#### <a name="menus"></a>メニュー  
 各メニューとして定義されている、[メニュー要素](../../extensibility/menu-element.md)で、`Menus`セクション。 メニューがあります`guid`、 `id`、および`priority`属性、および`Parent`要素と次の追加属性も子。  
  
-   A`type`属性をある種のメニューまたはツールバーとして IDE で、メニューを表示する必要があるかどうかを指定します。  
  
-   A[文字列要素](../../extensibility/strings-element.md)を格納している、 [ButtonText 要素](../../extensibility/buttontext-element.md)、IDE では、メニューのタイトルを指定して、 [CommandName 要素](../../extensibility/commandname-element.md)は、名前を指定します。使用される、**コマンド**ウィンドウ メニューにアクセスします。  
  
-   オプションのフラグ。 A [Command Flag 要素](../../extensibility/command-flag-element.md)外観や IDE での動作を変更するメニュー定義に表示される可能性があります。  
  
 すべて`Menu`要素は、ツールバーなどのドッキング可能な要素である場合を除きに、親としてのグループをいる必要があります。 ドッキング可能なメニューは、それ自身の親です。 メニューと値の詳細については、`type`属性を参照してください、[メニュー要素](../../extensibility/menu-element.md)ドキュメント。  
  
 次の例は、Visual Studio のメニュー バーの横に表示されるメニュー、**ツール**メニュー。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>グループ  
 グループで定義されている項目とは、 `Groups` .vsct ファイルのセクション。 グループは、単なるコンテナーです。 メニューに区切り線として IDE 以外で表示が実行されません。 そのため、[グループ要素](../../extensibility/group-element.md)署名、優先度、および親によってのみ定義されます。  
  
 グループでは、親として、メニューの別のグループ、またはその自体を持つことができます。 ただし、親が通常メニューまたはツールバーです。 先ほどの例で、メニューの子である、`IDG_VS_MM_TOOLSADDINS`グループ、およびそのグループは、Visual Studio のメニュー バーの子。 次の例では、グループは、前の例では、メニューの子です。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 メニューの一部であるため、このグループには通常のコマンドが含まれます。 ただし、その他のメニューも含むことができます。 つまり、次の例に示すように、サブメニューの定義方法。  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>コマンド  
 IDE に提供されるコマンドがいずれかとして定義されている、[ボタン要素](../../extensibility/button-element.md)または[Combo 要素](../../extensibility/combo-element.md)します。 メニューまたはツールバーに表示される、コマンドは、その親グループが必要です。  
  
##### <a name="buttons"></a>ボタン  
 ボタンが定義されている、`Buttons`セクション。 任意のメニュー項目、ボタン、または 1 つのコマンドを実行するユーザーがクリックしたその他の要素は、ボタンと見なされます。 いくつかのボタンの種類では、リスト機能を含めることもできます。 ボタンがあるために必要な同じホストとメニューがある、オプションの属性も持つことができます、 [Icon 要素](../../extensibility/icon-element.md)GUID と、IDE でボタンを表すビットマップの ID を指定します。 ボタンとその属性の詳細については、次を参照してください。、[ボタン要素](../../extensibility/buttons-element.md)ドキュメント。  
  
 次の例では、ボタンは、前の例で、グループの子であるし、は、IDE でそのグループの親メニューにメニュー項目として表示されます。  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Combos  
 Combos がで定義されている、`Combos`セクション。 各`Combo`要素は、IDE でのドロップダウン リスト ボックスを表します。 リスト ボックスがまたはの値に応じて、ユーザーが書き込み可能なことができない可能性があります、`type`コンボ ボックスの属性です。 Combos が同じ要素を持ち、ボタンの動作があると、次の追加属性を持つことができますも。  
  
-   A`defaultWidth`ピクセル幅を指定する属性。  
  
-   `idCommandList`属性リスト ボックスに表示される項目を含むリストを指定します。 同じコマンドの一覧を宣言する必要があります`GuidSymbol`コンボ ボックスを含むノードです。  
  
 次の例では、複合要素を定義します。  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>ビットマップ  
 アイコンと共に表示されるコマンドを含める必要があります、`Icon`その GUID と ID を使用して、ビットマップを参照する要素 各ビットマップとして定義されている、[ビットマップ要素](../../extensibility/bitmap-element.md)で、`Bitmaps`セクション。 唯一の必須の属性を`Bitmap`定義は`guid`と`href`、ソース ファイルを表しています。 ソース ファイルが、リソースのストリップの場合、 **usedList**属性も、ストリップで利用可能なイメージを一覧表示する、必須です。 詳細については、次を参照してください。、[ビットマップ要素](../../extensibility/bitmap-element.md)ドキュメント。  
  
### <a name="parenting"></a>親子関係  
 次の規則は、項目がその親として別のアイテムを呼び出す方法を制御します。  
  
|要素|コマンド テーブルのこのセクションで定義されています。|含まれている可能性があります (親、または内の配置によって、`CommandPlacements`セクション、またはその両方)|含めることができます ("親"と呼ばれます)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|グループ化|[Groups 要素](../../extensibility/groups-element.md)IDE、その他の Vspackage|メニュー、グループ、アイテム自体|メニューのグループ、およびコマンド|  
|メニュー|[Menus 要素](../../extensibility/menus-element.md)IDE、その他の Vspackage|1 ~ *n*グループ|0 ~ *n*グループ|  
|ツール バー|[Menus 要素](../../extensibility/menus-element.md)IDE、その他の Vspackage|項目自体|0 ~ *n*グループ|  
|メニュー項目|[要素をボタン](../../extensibility/buttons-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化|-0 ~ *n*グループ|  
|ボタン|[要素をボタン](../../extensibility/buttons-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化||  
|コンボ|[Combos 要素](../../extensibility/combos-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化||  
  
### <a name="menu-command-and-group-placement"></a>メニューのコマンド、およびグループの配置  
 メニューのグループ、またはコマンドは、IDE では、複数の場所に表示できます。 複数の場所に表示される項目に追加する必要があります、`CommandPlacements`セクションとして、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)します。 コマンドの配置とは、任意のメニューのグループ、またはコマンドを追加できます。 ただし、状況依存の複数の場所に表示されることはできませんので、この方法でツールバーを配置することはできません。  
  
 コマンドの配置が`guid`、 `id`、および`priority`属性。 GUID と ID が配置されている項目の一致する必要があります。 `priority`属性はその他のアイテムに関して、項目の配置を制御します。 IDE には、優先順位が同じ 2 つ以上の項目がマージされる、その配置は、IDE はパッケージ リソースが読み取ることと同じ順序で、パッケージをビルドするたびに保証されないためにと定義できません。  
  
 メニューまたはグループが複数の場所に表示された場合、そのメニューまたはグループのすべての子は、各インスタンスに表示されます。  
  
## <a name="command-visibility-and-context"></a>コマンドの可視性とコンテキスト  
 複数 Vspackage がインストールされると、メニューのメニュー項目やツールバーが豊富に存在するは、IDE をしまう可能性があります。 この問題を回避するためを使用して個々 の UI 要素の表示を制御できます*可視性制約*とコマンドのフラグ。  
  
##### <a name="visibility-constraints"></a>可視性の制約  
 として可視性の制約が設定されて、 [VisibilityItem 要素](../../extensibility/visibilityitem-element.md)で、`VisibilityConstraints`セクション。 可視性の制約は、ターゲット項目が表示されている特定の UI コンテキストを定義します。 メニューまたはこのセクションに含まれているコマンドは、定義されたコンテキストのいずれかがアクティブなときにだけ表示されます。 メニューまたはコマンドがこのセクションで参照されていない場合、既定では常にします。 このセクションでは、グループには適用されません。  
  
 `VisibilityItem` 要素では、3 つの属性を次のようにいる必要があります。`guid`と`id`対象の UI 要素の`context`します。 `context`属性は、ターゲット項目が表示されますおよびはその値として任意の有効な UI コンテキストを指定します。 Visual Studio の UI コンテキストの定数のメンバーである、<xref:Microsoft.VisualStudio.VSConstants>クラス。 すべて`VisibilityItem`要素が 1 つのみのコンテキスト値を取得できます。 2 番目のコンテキストを適用するには、2 つ目を作成`VisibilityItem`次の例に示すように、同じ項目をポイントする要素。  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>コマンドのフラグ  
 次のコマンド フラグ、メニューとコマンドに適用されるの可視性に影響を与えることができます。  
  
 通常  
 グループやボタンれていない場合でも、メニューが作成されます。  
  
 に対して有効です。 `Menu`  
  
 CommandWellOnly  
 フラグを適用この、コマンドは、最上位のメニューに表示されないと、その他のシェルのカスタマイズに使用できるようにする場合など、キーにバインドします。 ユーザーがこれらのコマンドをカスタマイズを開き、VSPackage をインストールした後、**オプション**] ダイアログ ボックスと [コマンドの配置を編集し、**キーボード環境**カテゴリ。 ショートカット メニューのツールバー、メニュー コント ローラー、またはサブメニューへの配置には影響しません。  
  
 に対して無効です: `Button`、 `Combo`  
  
 DefaultDisabled  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドが無効になります。  
  
 に対して無効です: `Button`、 `Combo`  
  
 DefaultInvisible  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドは表示されません。  
  
 組み合わせる必要があります、`DynamicVisibility`フラグ。  
  
 に対して無効です: `Button`、 `Combo`、 `Menu`  
  
 DynamicVisibility  
 QueryStatus メソッドまたはコンテキストに含まれている GUID を使用して、コマンドの可視性を変更することができます、`VisibilityConstraints`セクション。  
  
 ツールバーではなく、メニュー上に表示されるコマンドに適用されます。 最上位レベルのツールバー項目は無効にできますが、非表示に、OLECMDF_INVISIBLE フラグは、QueryStatus メソッドから返されるときに。  
  
 メニューのこと、自動的に非表示にするとき、そのメンバーを非表示をこのフラグも示します。 通常、このフラグは、トップレベルのメニューでは、この動作が既にあるため、サブメニューに割り当てられます。  
  
 組み合わせる必要があります、`DefaultInvisible`フラグ。  
  
 に対して無効です: `Button`、 `Combo`、 `Menu`  
  
 NoShowOnMenuController  
 メニュー コント ローラーでこのフラグを持つコマンドを配置すると場合、コマンドは、ドロップダウン リストでは表示されません。  
  
 に対して有効です。 `Button`  
  
 コマンドのフラグの詳細については、次を参照してください。、 [Command Flag 要素](../../extensibility/command-flag-element.md)ドキュメント。  
  
##### <a name="general-requirements"></a>一般的な要件  
 コマンドは、表示および有効にする前に、次の一連のテストを渡す必要があります。  
  
-   コマンドが正しく配置されています。  
  
-   `DefaultInvisible`フラグは設定されません。  
  
-   親メニューやツールバーが表示されます。  
  
-   コンテキストのエントリのため、コマンドが非表示は、 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)セクション。  
  
-   実装する VSPackage コード、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスが表示され、コマンドを使用します。 インターセプトがし、その実施するインターフェイスのコードはありません。  
  
-   ユーザーは、コマンドをクリックするに記載されている手順に従ってなります[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)します。  
  
## <a name="calling-pre-defined-commands"></a>定義済みのコマンドを呼び出す  
 [UsedCommands 要素](../../extensibility/usedcommands-element.md)または IDE で他の Vspackage によって提供されるコマンドにアクセスする Vspackage を使用します。 これを行うには、作成、 [UsedCommand 要素](../../extensibility/usedcommand-element.md)GUID とコマンドの使用の ID を持ちます。 こう現在の Visual Studio の構成の一部ではない場合でも、Visual Studio によって、コマンドが読み込まれます。 詳細については、次を参照してください。 [UsedCommand 要素](../../extensibility/usedcommand-element.md)します。  
  
## <a name="interface-element-appearance"></a>インターフェイス要素の外観  
 選択して、コマンド要素の配置に関する考慮事項は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 配置に応じて異なる方法で表示される多くの UI 要素を提供します。  
  
-   使用して定義されている UI 要素、`DefaultInvisible`の VSPackage 実装によって表示されるいずれかである場合を除き、フラグを IDE に表示されませんが、<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>メソッドで特定の UI コンテキストに関連付けられているか、`VisibilityConstraints`セクション。  
  
-   正常に配置されているコマンドでもは表示されません。 これは IDE が自動的に非表示にまたはインターフェイスを VSPackage が (またはされていない) に応じて、いくつかのコマンドが表示されますので、実装します。 たとえば、いくつかの VSPackage の実装は、自動的に表示されるビルドに関連するメニュー項目を原因インターフェイス ビルドします。  
  
-   適用、 `CommandWellOnly` UI 要素の定義でフラグはコマンドのカスタマイズによってのみ追加できることを意味します。  
  
-   コマンドは、IDE がデザイン ビューである場合は、ダイアログが表示されます。 場合にのみ、UI、特定のコンテキストなどでのみ使用可能なことがあります。  
  
-   IDE に表示される特定の UI 要素には、1 つまたは複数のインターフェイスを実装またはコードを記述する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)

