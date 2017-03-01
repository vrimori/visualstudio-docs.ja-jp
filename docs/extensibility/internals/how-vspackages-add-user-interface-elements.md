---
title: "Vspackage でのユーザー インターフェイス要素を追加する方法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
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
ms.openlocfilehash: 6bf44a2b1fa029753c4b3c00f911070a2132bb75
ms.lasthandoff: 02/22/2017

---
# <a name="how-vspackages-add-user-interface-elements"></a>Vspackage でのユーザー インターフェイス要素を追加する方法
VSPackage では、ユーザー インターフェイス (UI) 要素、たとえば、メニューのツールバーを追加でき、ツール ウィンドウ、.vsct ファイルを使用して Visual Studio をすることができます。  
  
 UI 要素のデザインのガイドラインを検索する[Visual Studio のユーザー エクスペリエンス ガイドライン](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)します。  
  
## <a name="the-visual-studio-command-table-architecture"></a>Visual Studio コマンド テーブルのアーキテクチャ  
 前述のように、コマンド テーブルのアーキテクチャには、前述のアーキテクチャの原則がサポートしています。 抽象化、データ構造体およびコマンド テーブルのアーキテクチャのツールの背後にある次の原則は次のとおりです。  
  
-   次の&3; つの基本的な種類の項目がある: メニューのコマンド、およびグループ。 メニューは、メニューのサブメニュー、ツールバー、またはツール ウィンドウとして、UI で公開できます。 コマンドは、ユーザーは、IDE で実行し、メニュー項目、ボタン、リスト ボックス、またはその他のコントロールとして公開できるプロシージャです。 グループは、メニューとコマンドの両方のコンテナーです。  
  
-   各項目は、アイテム、その他のアイテムおよびその動作を変更するフラグと比較して優先順位を表す定義によって指定されます。  
  
-   各アイテムには、項目の親を表す配置します。 UI で複数の場所に表示できるように、項目は複数の親にはできます。  
  
     すべてのコマンドは、そのグループ内の唯一の子である場合でも、その親グループが必要です。 標準のすべてのメニューは、親グループも必要です。 ツールバーとツール ウィンドウは、独自の親として機能します。 グループは、メインの Visual Studio のメニュー バーで、親、または、メニューのツールバー、またはツール ウィンドウとして設定できます。  
  
### <a name="how-items-are-defined"></a>項目を定義する方法  
 .Vsct ファイルは XML で書式設定します。 .Vsct ファイルは、パッケージの UI 要素を定義し、IDE 内でのそれらの要素の表示場所を決定します。 すべてのメニューのグループ、またはパッケージ内のコマンドは、最初に割り当てられた GUID と ID、`Symbols`セクションです。 .Vsct の残りの部分でファイル、各メニューのコマンド、およびグループは、GUID と ID の組み合わせによって識別されます。 次の例は、標準的な`Symbols`セクションのように、Visual Studio パッケージ テンプレートによって生成されたときに、**メニュー コマンド**テンプレートで選択します。  
  
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
  
 トップレベルの要素、`Symbols`セクションは、 [GuidSymbol 要素](../../extensibility/guidsymbol-element.md)します。 `GuidSymbol`要素は、パッケージとその構成要素を識別するために、IDE で使用される Guid に名前をマップします。  
  
> [!NOTE]
>  Guid は、Visual Studio パッケージ テンプレートによって自動的に生成されます。 クリックして、一意の GUID を作成することもできます。 **GUID の作成**上、**ツール**メニュー。  
  
 最初の`GuidSymbol`要素"guid [PackageName] Pkg"、パッケージ自体の guid を指定します。 これは、Visual Studio によって、パッケージを読み込むために使用する GUID です。 通常、子要素はありません。  
  
 規則では、メニューとコマンドはグループ化された&1; 秒未満`GuidSymbol`要素"guid [PackageName] CmdSet"、およびビットマップは、3 つ目で、`GuidSymbol`要素、"guidImages"です。 この規則に準拠する必要はありませんが、各メニューのグループ、コマンド、およびビットマップの子である必要があります、`GuidSymbol`要素。  
  
 2 番目の`GuidSymbol`パッケージ コマンド セットを表す要素がいくつか`IDSymbol`要素。 各[IDSymbol 要素](../../extensibility/idsymbol-element.md)値を数値には、名をマップし、メニューのグループ、または一連のコマンドの一部であるコマンドを表すことがあります。 `IDSymbol`&3; つ目の要素`GuidSymbol`コマンドのアイコンとして使用できる要素表すビットマップです。 GUID と ID のペアは、アプリケーションでは、同一のない&2; つの子で一意であるため`GuidSymbol`要素が同じ値を持つことがあります。  
  
### <a name="menus-groups-and-commands"></a>メニューのグループ、およびコマンド  
 メニューのグループ、またはコマンドの GUID と ID を持つと、は、IDE に追加できます。 UI 要素はすべて、次の処理が必要です。  
  
-   A`guid`属性の名前に一致する、`GuidSymbol`下にある UI 要素が定義されています。  
  
-   `id` 、関連する名前に一致する属性`IDSymbol`要素。  
  
     同時に、`guid`と`id`属性を作成、*署名*の UI 要素。  
  
-   A`priority`属性をその親メニューやグループ内の UI 要素の位置を決定します。  
  
-   A[親要素](../../extensibility/parent-element.md)を持つ`guid`と`id`親メニューまたはグループの署名を指定する属性です。  
  
#### <a name="menus"></a>メニュー  
 各メニューとして定義されている、 [Menu](../../extensibility/menu-element.md)で、`Menus`セクションです。 メニューがあります`guid`、 `id`、および`priority`属性、および`Parent`要素、および次の追加の属性もと子要素。  
  
-   A`type`一種のメニューまたはツールバーとして IDE でにこのメニューを表示するかどうかを指定する属性です。  
  
-   A[文字列要素](../../extensibility/strings-element.md)を含む、 [ButtonText 要素](../../extensibility/buttontext-element.md)、IDE では、メニューのタイトルを指定して、 [CommandName 要素](../../extensibility/commandname-element.md)で使用されている名前を指定、**コマンド**ウィンドウ メニューにアクセスします。  
  
-   省略可能なフラグです。 A[コマンド フラグ要素](../../extensibility/command-flag-element.md)外観や、IDE での動作を変更する メニューの 定義に含めることはできます。  
  
 各`Menu`要素グループが必要、親としてなど、ツールバーのドッキング可能な要素でない限り、します。 ドッキング可能なメニューは、自身の親です。 メニューと値の詳細については、`type`属性を参照してください、 [Menu](../../extensibility/menu-element.md)ドキュメントです。  
  
 次の例では、Visual Studio のメニュー バーの横に表示されるメニュー、**ツール**メニュー。  
  
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
 定義されている項目は、グループは、 `Groups` .vsct ファイルのセクションです。 グループは、単なるコンテナーです。 メニューの区切り線として IDE 以外でこれらは現れません。 したがって、[グループ要素](../../extensibility/group-element.md)署名、優先順位、および親によってのみ定義されます。  
  
 グループは、メニューの別のグループまたはそれ自体を親として設定できます。 ただし、親は、メニューまたはツールバー、通常です。 先ほどの例で、メニューの子である、`IDG_VS_MM_TOOLSADDINS`グループ、およびそのグループは、Visual Studio のメニュー バーの子です。 次の例では、グループは、先ほどの例で、メニューの子です。  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 メニューの一部である、このグループには通常のコマンドが含まれます。 ただし、その他のメニューも含むことがあります。 これはサブメニューの定義方法の例を次に示すようです。  
  
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
 IDE に提供されるコマンドがいずれかとして定義されている、 [Button 要素](../../extensibility/button-element.md)または[コンボ要素](../../extensibility/combo-element.md)します。 メニューまたはツールバーに表示される、コマンドは、その親グループが必要です。  
  
##### <a name="buttons"></a>ボタン  
 ボタンが定義されている、`Buttons`セクションです。 任意のメニュー項目、ボタン、または&1; つのコマンドを実行するユーザーがクリックしたその他の要素は、ボタンと見なされます。 いくつかのボタンの種類では、リスト機能を含めることもできます。 ボタンのために必要な同じとメニューがある、省略可能な属性であることもでき、 [Icon 要素](../../extensibility/icon-element.md)GUID と、IDE でボタンを表すビットマップの ID を指定します。 ボタンとその属性の詳細については、次を参照してください。、[ボタン要素](../../extensibility/buttons-element.md)ドキュメントです。  
  
 次の例では、ボタンは、前の例のグループの子であり、そのグループの親メニューのメニュー項目として、IDE が表示されます。  
  
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
 コンボが定義されている、`Combos`セクションです。 各`Combo`要素は、IDE でのドロップダウン リスト ボックスを表します。 リスト ボックスかの値に応じて、ユーザーが書き込み可能なことができない可能性があります、`type`コンボ ボックスの属性です。 コンボが同じ要素を持つし、ボタンの動作が、次の追加属性こともできます。  
  
-   A`defaultWidth`ピクセルの幅を指定する属性です。  
  
-   `idCommandList`リスト ボックスに表示される項目を含むリストを指定する属性です。 同じコマンドの一覧を宣言する必要があります`GuidSymbol`コンボ ボックスを含むノードです。  
  
 次の例では、コンボ要素を定義します。  
  
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
 アイコンと共に表示されるコマンドを含める必要があります、`Icon`ビットマップをその GUID と ID を使用して参照要素 各ビットマップとして定義されている、[ビットマップ要素](../../extensibility/bitmap-element.md)で、`Bitmaps`セクションです。 唯一の必須の属性を`Bitmap`は定義`guid`と`href`、ソース ファイルを指しています。 ソース ファイルが、リソースのストリップの場合、 **usedList**属性は、ストリップに利用可能なイメージを一覧表示する必要もします。 詳細については、次を参照してください。、[ビットマップ要素](../../extensibility/bitmap-element.md)ドキュメントです。  
  
### <a name="parenting"></a>親子関係  
 次の規則は、項目が親と別のアイテムを呼び出す方法を制御します。  
  
|要素|コマンド テーブルのこのセクションで定義されています。|含まれる場合があります (親、または内の配置によって、 `CommandPlacements`  セクションで、またはその両方)|含めることがあります ("親"と呼ばれます)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|グループ化|[Groups 要素](../../extensibility/groups-element.md)IDE、その他の vspackages にあります。|メニューで、グループ、項目自体|メニューのグループ、およびコマンド|  
|メニュー|[メニュー要素](../../extensibility/menus-element.md)IDE、その他の vspackages にあります。|1 ~ *n*グループ|0 ~ *n*グループ|  
|ツール バー|[メニュー要素](../../extensibility/menus-element.md)IDE、その他の vspackages にあります。|項目自体|0 ~ *n*グループ|  
|メニュー項目|[要素をボタン](../../extensibility/buttons-element.md)IDE、その他の vspackages にあります。|1 ~ *n*項目自体をグループ化|-0 *n*グループ|  
|ボタン|[要素をボタン](../../extensibility/buttons-element.md)IDE、その他の vspackages にあります。|1 ~ *n*項目自体をグループ化||  
|コンボ|[コンボ要素](../../extensibility/combos-element.md)IDE、その他の vspackages にあります。|1 ~ *n*項目自体をグループ化||  
  
### <a name="menu-command-and-group-placement"></a>メニューのコマンド、およびグループの配置  
 メニューのグループ、またはコマンドは、IDE の&1; つ以上の場所に表示できます。 複数の場所に表示されるアイテムに追加する必要があります、`CommandPlacements`としてセクション、 [CommandPlacement 要素](../../extensibility/commandplacement-element.md)します。 コマンドの配置とは、任意のメニューのグループ、またはコマンドを追加できます。 ただし、状況依存の複数の場所に表示されることはできませんので、この方法でツールバーを配置することはできません。  
  
 コマンドの配置が`guid`、 `id`、および`priority`属性です。 GUID と ID が配置されている項目のものに一致する必要があります。 `priority`属性がその他のアイテムに関して、アイテムの配置によって決まります。 IDE が優先順位が同じ&2; つ以上の項目をマージした場合、配置は未定義 IDE で、パッケージをビルドするたびに、同じ順序でリソースをパッケージが読み込まれることが保証されないためです。  
  
 メニューまたはグループが複数の場所に表示された場合、そのメニューまたはグループのすべての子は、各インスタンスに表示されます。  
  
## <a name="command-visibility-and-context"></a>コマンドの可視性とコンテキスト  
 複数ある Vspackage がインストールされると、メニューのメニュー項目、およびツールバーが豊富に存在は、IDE をしまう可能性があります。 この問題を回避するのを使用して個々 の UI 要素の表示を制御できます*可視性制約*とコマンドのフラグ。  
  
##### <a name="visibility-constraints"></a>可視性制約  
 として表示制限が設定されて、 [VisibilityItem 要素](../../extensibility/visibilityitem-element.md)で、`VisibilityConstraints`セクションです。 可視性制約では、ターゲット項目が表示されている特定の UI コンテキストを定義します。 メニューまたはここに含まれているコマンドは、定義済みのコンテキストのいずれかがアクティブにのみ表示されます。 メニューまたはコマンドは、このセクションで参照されていない場合、既定では常にします。 このセクションでは、グループには適用されません。  
  
 `VisibilityItem`要素は次のように&3; つの属性を持つ必要があります。`guid`と`id`の対象の UI 要素と`context`です。 `context`属性は、ターゲット項目が表示され、その値として有効な UI コンテキストを指定します。 <xref:Microsoft.VisualStudio.VSConstants>クラス</xref:Microsoft.VisualStudio.VSConstants>のメンバーである Visual Studio の UI コンテキスト定数 各`VisibilityItem`要素が&1; つのみのコンテキスト値を取得します。 2 番目のコンテキストを適用するには、1 秒間を作成`VisibilityItem`の次の例に示すように、同じ項目をポイントする要素。  
  
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
 次のコマンド フラグは、メニューとコマンドに適用されるの可視性に影響を与えます。  
  
 通常  
 グループやボタンれていない場合でも、メニューが作成されます。  
  
 有効期間:`Menu`  
  
 CommandWellOnly  
 フラグを適用このトップレベルのメニューにコマンドが表示されないと、その他のシェルのカスタマイズに使用できるようにする場合など、キーにバインドすることです。 ユーザーがこれらのコマンドをカスタマイズを開いて、VSPackage をインストールした後、**オプション** ダイアログ ボックスと コマンドの配置を編集して、**キーボード環境**カテゴリ。 ショートカット メニューのツールバー、メニューのコント ローラー、またはサブメニューの配置には影響しません。  
  
 に対して無効です: `Button`、`Combo`  
  
 DefaultDisabled  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドが無効になります。  
  
 に対して無効です: `Button`、`Combo`  
  
 DefaultInvisible  
 既定では、コマンドを実装する VSPackage が読み込まれていないか、QueryStatus メソッドが呼び出されていない場合、コマンドは表示されません。  
  
 組み合わせる必要があります、`DynamicVisibility`フラグ。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 アドインまたはコンテキストに含まれている GUID を使用してコマンドの表示/非表示を変更することができます、`VisibilityConstraints`セクションです。  
  
 ツールバーではなくのメニューに表示されるコマンドに適用されます。 トップレベルのツール バー アイテムは無効にできますが、非表示に、OLECMDF_INVISIBLE フラグは、QueryStatus メソッドから返されたとき。  
  
 メニューのことに自動的に非表示にするそのメンバーが非表示をこのフラグも示されます。 このフラグは、トップレベルのメニューでは、この動作が既にあるために通常サブメニューに割り当てられます。  
  
 組み合わせる必要があります、`DefaultInvisible`フラグ。  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 このフラグが付いているコマンドがメニュー コント ローラーに配置されている場合、コマンドがドロップダウン リストに表示されません。  
  
 有効期間:`Button`  
  
 コマンドのフラグの詳細については、次を参照してください。、[コマンド フラグ要素](../../extensibility/command-flag-element.md)ドキュメントです。  
  
##### <a name="general-requirements"></a>一般的な要件  
 コマンドは、表示され有効にする前に、次の一連のテストを渡す必要があります。  
  
-   コマンドが正常に配置されます。  
  
-   `DefaultInvisible`フラグが設定されていません。  
  
-   親メニューまたはツールバーが表示されます。  
  
-   コマンドは、コンテキスト エントリのためは非表示ではない、 [VisibilityConstraints 要素](../../extensibility/visibilityconstraints-element.md)セクションです。  
  
-   実装するコードを VSPackage、<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>インターフェイスが表示され、コマンドを有効にします</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>。 インターフェイス コードなしでは、それがインターセプトし、それに対処し、します。  
  
-   」で説明されている手順に従って、コマンドをクリックするとになります[ルーティング アルゴリズム](../../extensibility/internals/command-routing-algorithm.md)します。  
  
## <a name="calling-pre-defined-commands"></a>定義済みのコマンドを呼び出す  
 [UsedCommands 要素](../../extensibility/usedcommands-element.md)コマンドにアクセスするその他の vspackages にあるか、IDE に用意されている Vspackage を使用します。 これを行うには、作成、 [UsedCommand 要素](../../extensibility/usedcommand-element.md)GUID および使用するコマンドの ID を持ちます。 こう現在の Visual Studio の構成の一部ではない場合でも、コマンドは、Visual Studio によって読み込まれます。 詳細については、次を参照してください。 [UsedCommand 要素](../../extensibility/usedcommand-element.md)します。  
  
## <a name="interface-element-appearance"></a>インターフェイス要素の外観  
 選択して、コマンドの要素の配置に関する注意事項は次のとおりです。  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]配置に応じて異なる方法で表示される多くの UI 要素を提供します。  
  
-   UI 要素を使用して定義されている、`DefaultInvisible`の VSPackage 実装によって表示されるいずれかである場合を除き、フラグを IDE に表示されませんが、<xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>メソッド、UI の特定のコンテキストに関連付けられているか、`VisibilityConstraints`セクション</xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>。  
  
-   正常に配置されているコマンドまでは表示されません。 これは、IDE に自動的に表示または非表示コマンドによっては、ある VSPackage が (またはされていない) インターフェイスによってために実装されます。 たとえば、いくつかの実装を VSPackage のインターフェイスを構築原因ビルドに関連するメニュー項目が自動的に表示されます。  
  
-   適用する、 `CommandWellOnly` UI 要素の定義でフラグのカスタマイズによってのみ、コマンドを追加できることを意味します。  
  
-   コマンドは、IDE がデザイン ビューである場合、ダイアログ ボックスが表示された場合のみ、UI、特定のコンテキストなどでのみ使用可能なことがあります。  
  
-   IDE に表示する特定の UI 要素には、1 つまたは複数のインターフェイスを実装するか、コードを記述できます。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)
