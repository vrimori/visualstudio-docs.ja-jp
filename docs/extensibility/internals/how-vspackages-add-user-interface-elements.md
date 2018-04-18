---
title: Vspackage がユーザー インターフェイス要素を追加する方法 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 930ab9e741b2fd5bbc0ca2954192fe5e2c4313d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage がユーザー インターフェイス要素を追加する方法
VSPackage では、ユーザー インターフェイス (UI) 要素、たとえば、メニューのツールバーを追加でき、ツール ウィンドウ、.vsct ファイルを使用して Visual Studio をすることができます。  
  
 UI 要素のデザイン ガイドラインを確認できます[Visual Studio ユーザー エクスペリエンス ガイドライン](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)です。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio コマンド テーブルのアーキテクチャ  
 前述のように、コマンド テーブルのアーキテクチャは、前述のアーキテクチャの原則をサポートします。 抽象化、データ構造、およびコマンド テーブルのアーキテクチャのツールの背後にある次の原則は次のとおりです。  
  
-   項目の次の 3 つの基本的な種類があります: メニューのコマンド、およびグループ。 メニューは、メニューのサブメニュー、ツールバー、またはツール ウィンドウとして、UI で公開することができます。 コマンドは、プロシージャ、ユーザーが、IDE で実行し、メニュー項目、ボタン、リスト ボックス、またはその他のコントロールとして公開できます。 グループは、メニューとコマンドの両方のコンテナーです。  
  
-   各項目は、項目、他のアイテムおよびその動作を変更するフラグと比較して優先順位を表す定義によって指定されます。  
  
-   各アイテムには、項目の親を表す配置します。 UI での複数の場所で表示できるようにする、項目は複数の親にはできます。  
  
     すべてのコマンドは、そのグループ内の唯一の子である場合でも、その親グループが必要です。 標準のすべてのメニューは、親グループも必要です。 ツールバーとツール ウィンドウは、独自の親として機能します。 グループは、その親、メインの Visual Studio メニュー バーまたは、メニューのツールバー、またはツール ウィンドウとして設定できます。  
  
### <a name="how-items-are-defined"></a>項目を定義する方法  
 .Vsct ファイルは XML 形式でします。 .Vsct ファイルでは、パッケージ用の UI 要素を定義し、IDE では、それらの要素が表示される場所を決定します。 すべてのメニューのグループ、またはパッケージ内のコマンド最初に割り当てられる GUID と ID、`Symbols`セクションです。 残りの .vsct ファイル、各メニューのコマンド、およびグループが、GUID と ID の組み合わせによって識別されます。 次の例は、一般的な`Symbols`セクションで、Visual Studio パッケージ テンプレートによって生成されるときに、**メニュー コマンド**テンプレートが選択されています。  
  
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
  
 最上位要素、`Symbols`セクションは、 [GuidSymbol 要素](../../extensibility/guidsymbol-element.md)です。 `GuidSymbol` 要素では、名前がパッケージとその構成要素を識別する、IDE で使用される Guid にマップします。  
  
> [!NOTE]
>  Guid は、Visual Studio パッケージ テンプレートによって自動的に生成されます。 クリックして、一意の GUID を作成することも**GUID の作成**上、**ツール**メニュー。  
  
 最初の`GuidSymbol`要素"guid [PackageName] パッケージ"、パッケージ自体の GUID です。 これは、Visual Studio でパッケージを読み込むために使用する GUID です。 通常、子要素はありません。  
  
 規則では、メニューとコマンドの下にグループ化秒`GuidSymbol`要素、"guid [PackageName] CmdSet"、およびビットマップは、3 つ目で、`GuidSymbol`要素では、"guidImages"です。 この規則に従う必要はありませんが、各メニューのグループ、コマンド、およびビットマップの子である必要があります、`GuidSymbol`要素。  
  
 2 番目の`GuidSymbol`パッケージ コマンド セットを表す要素がいくつか`IDSymbol`要素。 各[IDSymbol 要素](../../extensibility/idsymbol-element.md)値を数値に名前をマップし、メニューのグループ、または、コマンド セットの一部であるコマンドを表すことがあります。 `IDSymbol` 3 番目の要素`GuidSymbol`コマンドのアイコンとして使用できる要素を示すビットマップ。 GUID と ID のペアがない 2 つの子の同じアプリケーション内で一意でなければならないため`GuidSymbol`要素が同じ値を持つことがあります。  
  
### <a name="menus-groups-and-commands"></a>メニューのグループ、およびコマンド  
 メニューのグループ、またはコマンドの GUID と ID を持つ、ときに、IDE に追加できます。 UI 要素はすべて、次の処理が必要です。  
  
-   A`guid`の名前と一致する属性、`GuidSymbol`下にある UI 要素が定義されている要素です。  
  
-   `id` 、関連する名前に一致する属性`IDSymbol`要素。  
  
     同時に、`guid`と`id`属性を作成、*署名*UI 要素のです。  
  
-   A`priority`親メニューまたはグループの UI 要素の配置を決定する属性。  
  
-   A[親要素](../../extensibility/parent-element.md)を持つ`guid`と`id`親メニューまたはグループの署名を指定する属性。  
  
#### <a name="menus"></a>メニュー  
 各メニューとして定義されている、 [Menu 要素](../../extensibility/menu-element.md)で、`Menus`セクションです。 メニューがあります`guid`、 `id`、および`priority`属性、および`Parent`とも、次の追加属性および子要素。  
  
-   A`type`種類のメニューまたはツールバーとして IDE で、メニューが表示されるかどうかを指定する属性。  
  
-   A[文字列要素](../../extensibility/strings-element.md)を格納している、 [ButtonText 要素](../../extensibility/buttontext-element.md)、IDE では、メニューのタイトルを指定して、 [CommandName 要素](../../extensibility/commandname-element.md)、ある名前を指定使用される、**コマンド**ウィンドウ メニューにアクセスします。  
  
-   省略可能なフラグです。 A[コマンド フラグ要素](../../extensibility/command-flag-element.md)外観や、IDE での動作を変更するメニュー定義に表示される可能性があります。  
  
 各`Menu`要素は、ツールバーなどのドッキング可能な要素である場合を除きに、その親としてのグループをいる必要があります。 ドッキング可能なメニューは、自身の親です。 メニューと値の詳細については、`type`属性を参照してください、 [Menu 要素](../../extensibility/menu-element.md)ドキュメント。  
  
 次の例は、Visual Studio メニュー バーで、横に表示されるメニュー、**ツール**メニュー。  
  
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
 定義されている項目は、グループは、 `Groups` .vsct ファイルのセクションです。 グループは、単なるコンテナーです。 これらは表示されませんを除く、IDE のメニュー上の区切り線として。 そのため、[グループ要素](../../extensibility/group-element.md)署名、優先度、および親によってのみが定義されています。  
  
 グループは、メニューの別のグループまたはそれ自体を親として設定できます。 ただし、親は、メニューやツールバー、通常です。 先ほどの例で、メニューの子である、`IDG_VS_MM_TOOLSADDINS`グループ、およびそのグループは、Visual Studio のメニュー バーの子です。 次の例では、グループは、前の例で、メニューの子です。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 メニューの一部になっているために、このグループには通常のコマンドが含まれます。 ただし、その他のメニューこれも含まれる可能性があります。 これはサブメニューの定義方法の例を次に示すようです。  
  
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
 IDE に提供されるコマンドがいずれかとして定義されている、[ボタン要素](../../extensibility/button-element.md)または[コンボ要素](../../extensibility/combo-element.md)です。 メニューまたはツールバーに表示される、コマンドは、その親としてグループが必要です。  
  
##### <a name="buttons"></a>ボタン  
 ボタンが定義されている、`Buttons`セクションです。 メニュー項目、ボタン、または 1 つのコマンドを実行するユーザーがクリックしたその他の要素は、ボタンと見なされます。 いくつかのボタンの種類では、リスト機能を含めることもできます。 ボタンに必要なと同じメニューがある、省略可能な属性があることもでき、 [Icon 要素](../../extensibility/icon-element.md)GUID と、IDE でボタンを表すビットマップの ID を指定します。 ボタンとその属性に関する詳細については、次を参照してください。、[ボタン要素](../../extensibility/buttons-element.md)ドキュメント。  
  
 次の例でボタンは、前の例では、グループの子であるし、そのグループの親メニューのメニュー項目と、IDE で表示されます。  
  
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
  
##### <a name="combos"></a>コンボ  
 コンボがで定義されている、`Combos`セクションです。 各`Combo`要素は、IDE でのドロップダウン リスト ボックスを表します。 リスト ボックスかの値に応じて、ユーザーが書き込み可能なことができない可能性があります、`type`コンボ ボックスの属性です。 コンボが、同じ要素を持つし、ボタンの動作がある、次の追加属性を持つことができますも。  
  
-   A`defaultWidth`ピクセル幅を指定する属性。  
  
-   `idCommandList`リスト ボックスに表示される項目を含むリストを指定する属性。 コマンドの一覧は同じで宣言されなければなりません`GuidSymbol`コンボを含むノードです。  
  
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
 アイコンと共に表示されるコマンドを含める必要があります、`Icon`その GUID と ID を使用して、ビットマップを参照する要素 各ビットマップとして定義されている、[ビットマップ要素](../../extensibility/bitmap-element.md)で、`Bitmaps`セクションです。 唯一の必須の属性を`Bitmap`定義は`guid`と`href`、ソース ファイルを指しています。 ソース ファイルが、リソース ストリップの場合、 **usedList**属性も必要なストリップに利用可能なイメージを一覧表示します。 詳細については、次を参照してください。、[ビットマップ要素](../../extensibility/bitmap-element.md)ドキュメント。  
  
### <a name="parenting"></a>親子関係  
 次のルールは、項目がその親として別のアイテムを呼び出す方法を管理します。  
  
|要素|コマンド テーブルのこのセクションで定義されています。|含まれる場合があります (親、または内の配置によって、 `CommandPlacements`  セクションで、またはその両方)|含めることができます (親と呼ばれる)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|グループ化|[Groups 要素](../../extensibility/groups-element.md)IDE、その他の Vspackage|メニュー、グループ、アイテム自体|メニューのグループ、およびコマンド|  
|メニュー|[メニュー要素](../../extensibility/menus-element.md)IDE、その他の Vspackage|1 ~ *n*グループ|0 ~ *n*グループ|  
|ツール バー|[メニュー要素](../../extensibility/menus-element.md)IDE、その他の Vspackage|項目自体|0 ~ *n*グループ|  
|メニュー項目|[要素の各ボタン](../../extensibility/buttons-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化|-0 ~ *n*グループ|  
|ボタン|[要素の各ボタン](../../extensibility/buttons-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化||  
|コンボ|[コンボ要素](../../extensibility/combos-element.md)IDE、その他の Vspackage|1 ~ *n*項目自体をグループ化||  
  
### <a name="menu-command-and-group-placement"></a>メニューのコマンド、およびグループの配置  
 メニューのグループ、またはコマンドは、IDE で 2 つ以上の場所に表示できます。 複数の場所に表示されるアイテムに追加する必要があります、`CommandPlacements`としてセクション、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)です。 コマンド配置としては、任意のメニューのグループ、またはコマンドを追加することができます。 ただし、状況依存の複数の場所に表示されることはできませんので、この方法でツールバーを配置することはできません。  
  
 コマンド配置が`guid`、 `id`、および`priority`属性。 GUID と ID が配置されている項目のものと一致してする必要があります。 `priority`属性が他のアイテムに関して、アイテムの配置を制御します。 IDE が優先順位が同じ 2 つ以上の項目をマージした場合、配置は未定義、IDE でパッケージをビルドするたびに、同じ順序でパッケージ リソースが読み込まれることが保証されないためです。  
  
 メニューまたはグループが複数の場所に表示された場合、そのメニューまたはグループのすべての子は、各インスタンスに表示されます。  
  
## <a name="command-visibility-and-context"></a>コマンドの可視性とコンテキスト  
 複数 Vspackage がインストールされているときに、メニューのメニュー項目、およびツールバーの不便は IDE をしまう可能性があります。 この問題を回避するのを使用して個々 の UI 要素の表示を制御できます*表示制約*とコマンド フラグ。  
  
##### <a name="visibility-constraints"></a>可視性の制約  
 可視性の制約として設定されて、 [VisibilityItem 要素](../../extensibility/visibilityitem-element.md)で、`VisibilityConstraints`セクションです。 可視性制約では、ターゲット項目が表示されている特定の UI コンテキストを定義します。 メニューまたはこのセクションに含まれているコマンドは、定義済みのコンテキストのいずれかがアクティブな場合にのみ表示されます。 場合は、メニューやコマンドは、このセクションで参照されていません、既定では常にします。 このセクションでは、グループには適用されません。  
  
 `VisibilityItem` 要素は 3 つの属性を次のようにいる必要があります。`guid`と`id`ターゲット UI 要素のおよび`context`です。 `context`属性は、ターゲット項目が表示されます、その値として任意の有効な UI コンテキストを受け取るを指定します。 Visual Studio の UI コンテキストの定数のメンバーである、<xref:Microsoft.VisualStudio.VSConstants>クラスです。 各`VisibilityItem`要素が 1 つのみのコンテキストの値を取ることができます。 2 つ目のコンテキストを適用するには、2 つ目を作成`VisibilityItem`次の例で示すように、同じ項目をポイントする要素。  
  
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
  
##### <a name="command-flags"></a>コマンド フラグ  
 次のコマンド フラグは、メニューとコマンドに適用されるの可視性に影響を与えます。  
  
 通常  
 グループやボタンれていない場合でも、メニューが作成されます。  
  
 に対して有効です。 `Menu`  
  
 CommandWellOnly  
 フラグを適用このコマンドがトップレベルのメニューに表示されない場合、その他のシェルのカスタマイズに使用できるようにするなど、キーにバインドします。 ユーザーが開くことによってこれらのコマンドをカスタマイズできます、VSPackage をインストールした後、**オプション**] ダイアログ ボックスと [コマンドの配置を編集し、**キーボード環境**カテゴリ。 ショートカット メニューのツールバー、メニュー コント ローラー、またはサブメニューの配置には影響しません。  
  
 無効: `Button`、 `Combo`  
  
 DefaultDisabled  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドが無効になります。  
  
 無効: `Button`、 `Combo`  
  
 DefaultInvisible  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドは表示されません。  
  
 組み合わせる必要があります、`DynamicVisibility`フラグ。  
  
 無効: `Button`、 `Combo`、 `Menu`  
  
 DynamicVisibility  
 QueryStatus メソッドまたはコンテキストに含まれている GUID を使用して、コマンドの可視性を変更することができます、`VisibilityConstraints`セクションです。  
  
 ツールバーではなく、メニューに表示されるコマンドに適用されます。 最上位のツールバー項目は、無効にできますが、非表示に、OLECMDF_INVISIBLE フラグは、QueryStatus メソッドから返されたとき。  
  
 メニューのこと、自動的に非表示にするとき、そのメンバーは非表示をこのフラグも示します。 このフラグは、トップレベルのメニューでは、この動作が既にあるために通常サブメニューに割り当てられます。  
  
 組み合わせる必要があります、`DefaultInvisible`フラグ。  
  
 無効: `Button`、 `Combo`、 `Menu`  
  
 NoShowOnMenuController  
 このフラグが付いているコマンドがメニュー コント ローラーに配置されている場合、コマンドはドロップダウン リストでは表示されません。  
  
 に対して有効です。 `Button`  
  
 コマンドのフラグの詳細については、次を参照してください。、[コマンド フラグ要素](../../extensibility/command-flag-element.md)ドキュメント。  
  
##### <a name="general-requirements"></a>一般的な要件  
 表示して有効にする前に、コマンドは次の一連のテストを渡す必要があります。  
  
-   コマンドが正しく配置されています。  
  
-   `DefaultInvisible`フラグが設定されていません。  
  
-   親メニューやツールバーは表示されます。  
  
-   コンテキストのエントリのため、コマンドが非表示は、 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)セクションです。  
  
-   VSPackage の実装コードを<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスが表示され、コマンドを有効にします。 インターフェイス コードなしでは、インターセプトがおよびに対して実行します。  
  
-   ユーザーは、コマンドをクリックするに記載されている手順に従ってなります[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)です。  
  
## <a name="calling-pre-defined-commands"></a>定義済みのコマンドを呼び出す  
 [UsedCommands 要素](../../extensibility/usedcommands-element.md)コマンドにアクセスするその他の Vspackage で、または IDE によって提供される Vspackage を有効にします。 これを行うには、作成、 [UsedCommand 要素](../../extensibility/usedcommand-element.md)GUID とを使用するコマンドの ID を持ちます。 これにより、Visual Studio によって、コマンドが読み込まれます場合でも、現在の Visual Studio の構成の一部ではありません。 詳細については、次を参照してください。 [UsedCommand 要素](../../extensibility/usedcommand-element.md)です。  
  
## <a name="interface-element-appearance"></a>インターフェイス要素の外観  
 選択して、コマンド要素の配置に関する注意点は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 配置に応じて異なる方法で表示される多くの UI 要素を提供します。  
  
-   UI 要素を使用して定義されている、`DefaultInvisible`の VSPackage 実装によって表示されるいずれかである場合を除き、フラグを IDE に表示されませんが、<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>メソッド、特定の UI コンテキストに関連付けられているか、`VisibilityConstraints`セクションです。  
  
-   正常に配置されているコマンドでもは表示されないことができます。 これはため、IDE に自動的にまたは非表示に表示されるいくつかのコマンドは、インターフェイス、VSPackage が (またはない) をによって実装されます。 たとえば、一部の VSPackage の実装インターフェイスを構築原因ビルドに関連するメニュー項目が自動的に表示されます。  
  
-   適用する、 `CommandWellOnly` UI 要素の定義のフラグはカスタマイズでのみ、コマンドを追加できることを意味します。  
  
-   コマンドは、IDE がデザイン ビューである場合、ダイアログ ボックスが表示されるときにのみ、UI、特定のコンテキストでのみ使用可能なことがあります。  
  
-   IDE に表示される特定の UI 要素には、1 つまたは複数のインターフェイスを実装するか、コードを記述する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [メニューとコマンドの拡張](../../extensibility/extending-menus-and-commands.md)