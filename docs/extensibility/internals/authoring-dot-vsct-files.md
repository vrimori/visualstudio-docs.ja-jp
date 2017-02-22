---
title: "作成します。Vsct ファイル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT ファイルの手動作成"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 作成します。Vsct ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

このドキュメントでは、Visual Studio 統合開発環境 \(IDE\) にメニュー項目、ツールバー、およびその他のユーザー インターフェイス \(UI\) 要素を追加する .vsct ファイルを作成する方法を説明します。 .Vsct ファイルがない Visual Studio パッケージ \(VSPackage\) に UI 要素を追加する場合は、次の手順を使用します。  
  
 新しいプロジェクト\] メニュー コマンド、ツール ウィンドウまたはカスタム エディターに必要な要素は既に選択に応じて、.vsct ファイルを生成するためには、Visual Studio パッケージ テンプレートを使用することをお勧めします。 VSPackage の要件を満たすためには、この .vsct ファイルを変更できます。 .Vsct ファイルを変更する方法の詳細については、例を参照してください。 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
## ファイルの作成  
 これらのフェーズで .vsct ファイルを作成します。 ファイルとリソースの構造を作成、UI 要素を宣言し、IDE では、UI 要素を配置してその特殊な動作を追加します。  
  
### ファイルの構造  
 .Vsct ファイルの基本的な構造は、 [CommandTable](../../extensibility/commandtable-element.md) ルート要素を含む、 [コマンド](../../extensibility/commands-element.md) 要素および [シンボル](../../extensibility/symbols-element.md) 要素。  
  
##### ファイル構造を作成するには  
  
1.  .Vsct ファイルをプロジェクトに次の手順に従って、追加 [方法: 作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)します。  
  
2.  必要な名前空間を追加、 `CommandTable` 要素は、次の例で示すようにします。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  `CommandTable` 要素を追加、 `Commands` すべてのカスタム メニューのツールバー、コマンドのグループ、およびコマンドをホストする要素。 カスタムの UI 要素にロードできるように、 `Commands` 要素が必要、 `Package` 属性は、パッケージの名前に設定します。  
  
     後に、 `Commands` 要素を追加、 `Symbols` 要素をパッケージと名前の Guid を定義し、UI 要素のコマンド Id。  
  
### Visual Studio のリソースを含む  
 使用して、 [Extern](../../extensibility/extern-element.md) Visual Studio のコマンドと、IDE で UI 要素を配置するために必要なメニューを定義するファイルにアクセスする要素。 使用して、パッケージの外部で定義されているコマンドを使用する場合は、 [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio に通知する要素。  
  
##### Visual Studio のリソースを追加するには  
  
1.  上部にある、 `CommandTable` 要素、1 つ追加 `Extern` 要素を設定し、参照する外部ファイルごとに、 `href` 属性をファイルの名前にします。 Visual Studio のリソースにアクセスする次のヘッダー ファイルを参照することができます。  
  
    -   Stdidcmd.h は、Visual Studio によって公開されているすべてのコマンドの Id を定義します。  
  
    -   Vsshlids.h には、Visual Studio のメニューのコマンド Id が含まれています。  
  
2.  パッケージが Visual Studio または他のパッケージで定義されたすべてのコマンドを呼び出す場合は、追加、 `UsedCommands` 要素の後に、 `Commands` 要素。 この要素での設定、 [UsedCommand](../../extensibility/usedcommand-element.md) 各コマンドを呼び出すが、パッケージの一部ではないです。 設定、 `guid` と `id` の属性、 `UsedCommand` 要素を呼び出すコマンドの GUID と ID の値。 Guid および Visual Studio の Id のコマンドを検索する方法の詳細については、次を参照してください。 [Guid と、Visual Studio コマンドの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)します。 他のパッケージからのコマンドを呼び出すには、GUID と、これらのパッケージに対して .vsct ファイルで定義されているコマンドの ID を使用します。  
  
### UI 要素を宣言します。  
 内のすべての新しい UI 要素の宣言、 `Symbols` .vsct ファイルのセクションです。  
  
##### UI 要素を宣言するには  
  
1.  `Symbols` 要素、3 つの追加 [GuidSymbol](../../extensibility/guidsymbol-element.md) 要素。 各 `GuidSymbol` 要素には、 `name` 属性と `value` 属性です。 設定、 `name` 属性、要素の目的が反映されるようにします。`value` 属性は、GUID を受け取ります。 \(上、GUID の生成、 **ツール** \] メニューのをクリックして **GUID の作成**, 、し、\[ **レジストリ形式**.\)  
  
     最初の `GuidSymbol` 要素が、パッケージを表し、通常、子がありません。 2 番目 `GuidSymbol` 要素は、コマンド セットにし、メニューのグループ、およびコマンドを定義するシンボルのすべてが含まれます。 3 番目の `GuidSymbol` 要素は、イメージ ストアを表すし、コマンドのアイコンをすべてのシンボルが含まれています。 3 つ目を省略するアイコンを使用するコマンドがない、 `GuidSymbol` 要素。  
  
2.  `GuidSymbol` コマンド セットを表す要素が 1 つ以上追加 [IDSymbol](../../extensibility/idsymbol-element.md) 要素。 これらの各エラーは、メニューのツールバー、グループ、または、UI に追加するコマンドを表します。  
  
     各 `IDSymbol` 要素の設定、 `name` 属性を使用して対応するメニューのグループ、または、コマンドを参照して、設定の名前に、 `value` 要素をコマンド id を表す 16 進数にします。 2 つ `IDSymbol` を同じ親を持つ要素が同じ値を持つことができます。  
  
3.  アイコンが必要な UI 要素のいずれかの場合は、追加、 `IDSymbol` する各アイコンの要素、 `GuidSymbol` をイメージ ストアを表す要素です。  
  
### IDE で UI 要素を配置します。  
 [メニュー](../../extensibility/menus-element.md) 要素、 [グループ](../../extensibility/groups-element.md) 要素、および [ボタン](../../extensibility/buttons-element.md) 要素には、すべてのメニューのグループ、およびパッケージで定義されているコマンドの定義が含まれています。 使用するか IDE でこれらのメニューのグループ、およびコマンドを配置、 [親](../../extensibility/parent-element.md) を使用して、UI 要素の定義の一部である要素、 [CommandPlacement](../../extensibility/commandplacement-element.md) にある要素では、別の場所で定義されています。  
  
 各 `Menu`, 、`Group`, 、および `Button` 要素には、 `guid` 属性と `id` 属性です。 常に設定、 `guid` 属性の名前に一致するように、 `GuidSymbol` コマンドを表す要素が設定し、設定、 `id` 属性の名前を `IDSymbol` メニューのグループ、またはコマンドを表す要素、 `Symbols` セクションです。  
  
##### UI 要素を定義するには  
  
1.  新しいメニューのサブメニュー、ショートカット メニューやツールバーを定義する場合は、追加、 `Menus` 要素を `Commands` 要素。 次に、各メニューを作成するには、追加、 [メニュー](../../extensibility/menu-element.md) 要素を `Menus` 要素。  
  
     設定、 `guid` と `id` の属性、 `Menu` 要素、および設定、 `type` 属性を目的のメニューの種類。 設定することも、 `priority` 属性を親グループで、メニューの相対位置を確立します。  
  
    > [!NOTE]
    >  `priority` 属性は、ツールバーとコンテキスト メニューには適用されません。  
  
2.  Visual Studio IDE のすべてのコマンドは、メニューとツールバーの直接の子であるコマンド グループでホストする必要があります。 IDE に新しいメニューまたはツールバーを追加する場合は、新しいコマンド グループを含めるこれら必要があります。 コマンドは、視覚的にグループ化できるように既存のメニューおよびツールバーにコマンド グループを追加することもできます。  
  
     最初に作成する必要がある新しいコマンド グループを追加すると、 `Groups` 要素、し、追加、 [グループ](../../extensibility/group-element.md) 各コマンド グループの要素。  
  
     設定、 `guid` と `id` それぞれの属性 `Group` 要素、および設定、 `priority` 属性を親メニューでグループの相対位置を確立します。 詳細については、「[ボタンの再利用可能なグループを作成します。](../../extensibility/creating-reusable-groups-of-buttons.md)」を参照してください。  
  
3.  IDE に新しいコマンドを追加する場合は、追加、 `Buttons` 要素を `Commands` 要素。 次に、各コマンドの追加、 [ボタン](../../extensibility/button-element.md) 要素を `Buttons` 要素。  
  
    1.  設定、 `guid` と `id` それぞれの属性 `Button` 要素、および設定、 `type` ボタンの種類を属性です。 設定することも、 `priority` 属性を親グループ内のコマンドは、相対位置を確立します。  
  
        > [!NOTE]
        >  使用する `type="button"` の標準のメニュー コマンドとツールバーのボタンです。  
  
    2.  `Button` 要素を追加、 [文字列](../../extensibility/strings-element.md) を含む要素、 [ButtonText](../../extensibility/buttontext-element.md) 要素および [CommandName](../../extensibility/commandname-element.md) 要素。`ButtonText` 要素がメニュー項目やツール バー ボタンのツールヒント テキスト ラベルを提供します。`CommandName` 要素は、コマンドで使用するコマンドの名前を提供します。  
  
    3.  コマンドとアイコンを持つ場合は、作成、 [アイコン](../../extensibility/icon-element.md) 内の要素、 `Button` 要素、およびセット、 `guid` と `id` 属性を `Bitmap` アイコンの要素。  
  
        > [!NOTE]
        >  ツール バー ボタンのアイコンが必要です。  
  
     詳細については、「[MenuCommand と  OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)」を参照してください。  
  
4.  コマンドのいずれかには、アイコンが必要がある場合は、追加、 [ビットマップ](../../extensibility/bitmaps-element.md) 要素を `Commands` 要素。 次に、各アイコンの追加、 [ビットマップ](../../extensibility/bitmap-element.md) 要素を `Bitmaps` 要素。 これは、ビットマップ リソースの場所を指定します。 詳細については、「[メニュー コマンドにアイコンを追加します。](../../extensibility/adding-icons-to-menu-commands.md)」を参照してください。  
  
 ほとんどのメニューのグループ、およびコマンドを正しく配置するための親子関係構造に依存することができます。 非常に大量のコマンド セット、またはコマンドの配置を指定することをお勧めメニューのグループ、またはコマンドは、複数の場所に表示する必要があります、します。  
  
##### IDE で UI 要素を配置する親子関係に依存するには  
  
1.  一般的な親子関係を作成、 `Parent` 内の各要素 `Menu`, 、`Group`, 、および `Command` パッケージに定義されています。  
  
     対象となる、 `Parent` 要素は、メニューまたはメニューを含むグループをグループ、またはコマンドです。  
  
    1.  設定、 `guid` 属性の名前を `GuidSymbol` コマンド セットを定義する要素。 ターゲット要素が、パッケージの一部でない場合は、対応する .vsct ファイルで定義されている、そのコマンド セットの guid を使用します。  
  
    2.  設定、 `id` と一致する属性、 `id` ターゲット メニューまたはグループの属性です。 メニューおよび Visual Studio によって公開されているグループの一覧については、次を参照してください。 [Guid と Visual Studio のメニューの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) または [Guid と Visual Studio ツールバーの Id](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)です。  
  
 IDE では、配置する UI 要素の数が多い場合、または複数の場所に表示される要素がある場合は、定義、配置、 [CommandPlacements](../../extensibility/commandplacements-element.md) 要素は、次の手順で示すようにします。  
  
##### コマンドの配置を使用して、IDE に UI 要素を配置するには  
  
1.  後に、 `Commands` 要素を追加、 `CommandPlacements` 要素。  
  
2.  `CommandPlacements` 要素を追加、 `CommandPlacement` 各メニューのグループ、または配置するコマンドの要素。  
  
     各 `CommandPlacement` 要素または `Parent` 要素が 1 つのメニューのグループ、またはコマンドを 1 つの IDE 場所に配置します。 UI 要素が持てる親を 1 つだけですが、コマンドの配置を複数持つことができます。 複数の場所で UI 要素を配置する追加の `CommandPlacement` 所在地ごとの要素。  
  
3.  設定、 `guid` と `id` それぞれの属性 `CommandPlacement` メニューまたはと同様のグループをホストする要素と、 `Parent` 要素。 設定することも、 `priority` UI 要素の相対位置を確立するために属性です。  
  
 親子関係での配置とコマンドの配置を混在させることができます。 ただし、非常に大量のコマンド セットには、コマンドの配置のみを使用することを勧めします。  
  
### 特殊な動作を追加します。  
 使用する [CommandFlag](../../extensibility/command-flag-element.md) 要素の外観と表示\/非表示を変更する、メニューとコマンドの動作を次に例を変更します。 使用して、コマンドが表示されている場合にも影響は [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), を使用してキーボード ショートカットを追加または [ショートカット キー](../../extensibility/keybindings-element.md)します。 組み込みのビヘイビアー専門的なメニューやコマンドが既に特定の種類。  
  
##### 特殊な動作を追加するには  
  
1.  UI 要素を表示する UI、特定のコンテキストなどでのみ、ソリューションが読み込まれるときにするには、可視性制約を使用します。  
  
    1.  後に、 `Commands` 要素を追加、 `VisibilityConstraints` 要素。  
  
    2.  制限するために各 UI 項目の追加、 [VisibilityItem](../../extensibility/visibilityitem-element.md) 要素。  
  
    3.  各 `VisibilityItem` 要素で設定されている、 `guid` と `id` メニューのグループ、またはコマンド、および設定する属性、 `context` UI のコンテキストで定義されている属性、 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> クラスです。 詳細については、「[VisibilityItem 要素](../../extensibility/visibilityitem-element.md)」を参照してください。  
  
2.  コードで、表示\/非表示または UI 項目の可用性を設定するには、次のコマンド フラグの 1 つ以上を使用します。  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     詳細については、「[コマンドのフラグ要素](../../extensibility/command-flag-element.md)」を参照してください。  
  
3.  要素の表示、またはを外観を動的に変更を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
    -   通常  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   Pict  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   \[テキスト  
  
    -   TextOnly  
  
     詳細については、「[コマンドのフラグ要素](../../extensibility/command-flag-element.md)」を参照してください。  
  
4.  コマンドを受信したときの要素の動作を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   フィルター キー機能  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     詳細については、「[コマンドのフラグ要素](../../extensibility/command-flag-element.md)」を参照してください。  
  
5.  メニューまたはメニューの項目をメニューに依存するキーボード ショートカットをアタッチするには、アンパサンド文字を追加 \('& '\) で、 `ButtonText` メニューまたはメニュー項目の要素。 アンパサンドに続く文字では、親メニューを開いている場合、アクティブなキーボード ショートカットがあります。  
  
6.  コマンドにショートカット メニューに依存しないキーをアタッチを使用して [ショートカット キー](../../extensibility/keybindings-element.md)します。 詳細については、「[Keybinding を割り当てる要素](../../extensibility/keybinding-element.md)」を参照してください。  
  
7.  メニュー テキストをローカライズするには、使用、 `LocCanonicalName` 要素。 詳細については、「[文字列の要素](../../extensibility/strings-element.md)」を参照してください。  
  
 一部のメニューとボタンの種類には、特殊な動作が含まれます。 次の表は、いくつかの特別なメニューとボタンの種類について説明します。 その他の種類を参照して、 `types` 属性の説明で [Menu 要素](../../extensibility/menu-element.md), 、[Button 要素](../../extensibility/button-element.md), 、および [コンボ要素](../../extensibility/combo-element.md)です。  
  
 コンボ ボックス  
 コンボ ボックスは、ツールバーの使用できるドロップダウン リストです。 UI には、コンボ ボックスを追加するには、作成、 [コンボ](../../extensibility/combos-element.md) 内の要素、 `Commands` 要素。 追加し、 `Combos` 要素、 `Combo` を追加するには、各コンボ ボックスの要素。`Combo` 要素の属性と子としてが同じである `Button` 要素も `DefaultWidth` と `idCommandList` 属性です。`DefaultWidth` 属性 \(ピクセル単位\) の幅を設定して、 `idCommandList` 属性は、コンボ ボックスの設定に使用するコマンド ID を参照します。 詳細については、次を参照してください。、 `Combo` 要素のドキュメントです。  
  
 MenuController  
 メニューの \[コント ローラーは、その横にある矢印の付いたボタンです。 矢印をクリックすると、リストが開きます。 メニューの \[コント ローラーを UI に追加するには、作成、 `Menu` 要素、 `type` 属性を **MenuController** または **MenuControllerLatched**, 希望の動作によって異なります。 親として設定\] メニューの \[コント ローラーを設定する、 `Group` 要素。 メニューの \[コント ローラーは、そのグループのすべての子をドロップダウン リストに表示されます。  
  
## 参照  
 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio コマンド テーブル \(します。Vsct\) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)