---
title: "作成します。Vsct ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bad1a8cbd8bc0369d405bf0a0c26c4285e143e46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="authoring-vsct-files"></a>作成します。Vsct ファイル
このドキュメントでは、Visual Studio 統合開発環境 (IDE) にメニュー項目、ツールバー、およびその他のユーザー インターフェイス (UI) 要素を追加する .vsct ファイルを作成する方法を示します。 UI 要素を既に .vsct ファイルを持たない Visual Studio パッケージ (VSPackage) を追加する場合は、次の手順を使用します。  
  
 新しいプロジェクトの場合、メニュー コマンド、ツール ウィンドウやカスタム エディターの必須の要素は既に選択内容に応じて .vsct ファイルを生成するために、Visual Studio パッケージ テンプレートを使用することをお勧めします。 VSPackage の要件を満たすには、この .vsct ファイルを変更することができます。 .Vsct ファイルを変更する方法の詳細については、例を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)です。  
  
## <a name="authoring-the-file"></a>ファイルの作成  
 これらのフェーズで .vsct ファイルを作成します。 ファイルとリソースの構造を作成、UI 要素を宣言し、IDE では、UI 要素を配置して、特殊な動作を追加します。  
  
### <a name="file-structure"></a>ファイルの構造  
 .Vsct ファイルの基本的な構造は、 [CommandTable](../../extensibility/commandtable-element.md)ルート要素を含む、[コマンド](../../extensibility/commands-element.md)要素、および[シンボル](../../extensibility/symbols-element.md)要素。  
  
##### <a name="to-create-the-file-structure"></a>ファイル構造を作成するには  
  
1.  次の手順に従って、プロジェクトに .vsct ファイルを追加[する方法: 作成、します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)です。  
  
2.  必要な名前空間を追加、`CommandTable`要素は、次の例で示すようにします。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  `CommandTable`要素を追加、`Commands`すべてのカスタム メニューのツールバー、コマンド グループ、およびコマンドをホストする要素。 カスタムの UI 要素を読み込むことができます、ように、`Commands`要素があります、`Package`属性は、パッケージの名前に設定します。  
  
     後に、`Commands`要素を追加、`Symbols`要素をパッケージ、および名前の Guid を定義し、UI 要素のコマンド Id。  
  
### <a name="including-visual-studio-resources"></a>Visual Studio のリソースを含む  
 使用して、 [Extern](../../extensibility/extern-element.md) Visual Studio のコマンドと、IDE で、UI 要素を挿入するために必要なメニューを定義するファイルにアクセスする要素。 使用して、パッケージの外部で定義されているコマンドを使用する場合、 [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio に通知する要素。  
  
##### <a name="to-include-visual-studio-resources"></a>Visual Studio のリソースを追加するには  
  
1.  上部にある、`CommandTable`要素、1 つ追加`Extern`を設定し、参照する各外部ファイルの要素を`href`属性をファイルの名前にします。 Visual Studio のリソースにアクセスする次のヘッダー ファイルを参照することができます。  
  
    -   Stdidcmd.h は、Visual Studio によって公開されるすべてのコマンドの Id を定義します。  
  
    -   Vsshlids.h には、Visual Studio のメニューのコマンド Id が含まれています。  
  
2.  パッケージが Visual Studio によって、または他のパッケージで定義されているどのようなコマンドを呼び出す場合は、追加、`UsedCommands`要素の後に、`Commands`要素。 この要素での設定、 [UsedCommand](../../extensibility/usedcommand-element.md)コマンドごとに呼び出すが、パッケージの一部ではない要素です。 設定、`guid`と`id`の属性、`UsedCommand`を呼び出すのコマンドの GUID と ID の値を要素。 Guid および Visual Studio の Id のコマンドを検索する方法の詳細については、次を参照してください。 [Guid と Visual Studio コマンドの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)します。 その他のパッケージからコマンドを呼び出すには、GUID、およびそれらのパッケージの .vsct ファイルで定義されているコマンドの ID を使用します。  
  
### <a name="declaring-ui-elements"></a>UI 要素を宣言します。  
 内のすべての新しい UI 要素の宣言、 `Symbols` .vsct ファイルのセクションです。  
  
##### <a name="to-declare-ui-elements"></a>UI 要素を宣言するには  
  
1.  `Symbols`要素、3 つの追加[GuidSymbol](../../extensibility/guidsymbol-element.md)要素。 各`GuidSymbol`要素には、`name`属性および`value`属性。 設定、`name`属性、要素の目的を反映するようにします。 `value`属性は、GUID を受け取ります。 (上、GUID の生成、**ツール**] メニューのをクリックして**GUID の作成**、し、[**レジストリ形式**)。  
  
     最初の`GuidSymbol`要素は、パッケージを表すし、通常、子がありません。 2 番目`GuidSymbol`要素を表しますコマンドは、このオプションを設定すると、し、メニューのグループ、およびコマンドを定義するシンボルのすべてが含まれます。 3 番目`GuidSymbol`要素は、イメージ ストアを表すし、コマンドのアイコンをすべてのシンボルが含まれています。 アイコンを使用するコマンドがない場合は、3 つ目を省略できます`GuidSymbol`要素。  
  
2.  `GuidSymbol` 、コマンド セットを表す要素が 1 つ以上追加[IDSymbol](../../extensibility/idsymbol-element.md)要素。 これらの各は、メニューのツールバー、グループ、または UI に追加するコマンドを表します。  
  
     各`IDSymbol`要素、設定、`name`属性を使用して、対応するメニューのグループ、またはコマンドを参照して、設定の名前に、`value`要素をコマンド id を表す 16 進数にします。2 つ`IDSymbol`を同じ親を持つ要素が同じ値を持つことができます。  
  
3.  場合は、UI 要素のいずれかには、アイコンが必要な追加、`IDSymbol`する各アイコンの要素、`GuidSymbol`イメージ ストアを表す要素。  
  
### <a name="putting-ui-elements-in-the-ide"></a>IDE の UI 要素を配置します。  
 [メニュー](../../extensibility/menus-element.md)要素、[グループ](../../extensibility/groups-element.md)要素、および[ボタン](../../extensibility/buttons-element.md)要素には、メニューのグループ、および、パッケージで定義されているコマンドのすべての定義が含まれています。 使用するか、IDE でこれらのメニューのグループ、およびコマンドを配置、[親](../../extensibility/parent-element.md)またはを使用して、UI 要素の定義の一部である要素、 [CommandPlacement](../../extensibility/commandplacement-element.md)が要素には、他の場所が定義されています。  
  
 各`Menu`、 `Group`、および`Button`要素には、`guid`属性および`id`属性。 常に設定、`guid`の名前に一致する属性、`GuidSymbol`コマンドを表す要素を設定して、設定、`id`属性の名前を`IDSymbol`メニューのグループ、または、内のコマンドを表す要素`Symbols`セクションです。  
  
##### <a name="to-define-ui-elements"></a>UI 要素を定義するには  
  
1.  新しいメニューのサブメニュー、ショートカット メニューやツールバーを定義する場合は、追加、`Menus`要素を`Commands`要素。 次に、各メニューを作成するには、追加、[メニュー](../../extensibility/menu-element.md)要素を`Menus`要素。  
  
     設定、`guid`と`id`の属性、`Menu`要素、および設定、`type`メニューの種類に属性します。 設定することも、`priority`属性を親グループで、メニューの相対的な位置を確立します。  
  
    > [!NOTE]
    >  `priority`属性は、ツールバーとコンテキスト メニューには適用されません。  
  
2.  Visual Studio IDE のすべてのコマンドは、メニューとツールバーの直接の子であるコマンド グループによってホストされる必要があります。 IDE に新しいメニューやツールバーを追加する場合は、新しいコマンド グループを含めるこれら必要があります。 コマンドは、視覚的にグループ化できるように既存のメニューとツールバーをコマンド グループを追加することもできます。  
  
     コマンドの新しいグループを追加する必要がありますを初めて作成、`Groups`要素を追加し、[グループ](../../extensibility/group-element.md)コマンド グループごとに要素。  
  
     設定、`guid`と`id`の各属性`Group`要素、および設定、`priority`親メニューでグループの相対的な位置を確立するために属性。 詳細については、次を参照してください。[ボタンの再利用可能なグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
3.  新しいコマンドを IDE に追加する場合は、追加、`Buttons`要素を`Commands`要素。 次に、各コマンドの追加、[ボタン](../../extensibility/button-element.md)要素を`Buttons`要素。  
  
    1.  設定、`guid`と`id`の各属性`Button`要素、および設定、`type`ボタンの種類に属性します。 設定することも、`priority`親グループ内のコマンドは、の相対的な位置を確立するために属性。  
  
        > [!NOTE]
        >  使用して`type="button"`の標準のメニュー コマンドやツールバーのボタンです。  
  
    2.  `Button`要素を追加、[文字列](../../extensibility/strings-element.md)要素を含む、 [ButtonText](../../extensibility/buttontext-element.md)要素および[CommandName](../../extensibility/commandname-element.md)要素。 `ButtonText`要素は、メニュー項目またはツール バー ボタンのツールヒントのテキスト ラベルを提供します。 `CommandName`要素は、コマンドで使用するコマンドの名前を提供します。  
  
    3.  コマンドがアイコンである場合は、作成、[アイコン](../../extensibility/icon-element.md)内の要素、`Button`要素、およびセットその`guid`と`id`属性を`Bitmap`アイコンの要素。  
  
        > [!NOTE]
        >  ツール バー ボタンのアイコンが必要です。  
  
     詳細については、次を参照してください。 [Menucommand とします。OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)です。  
  
4.  コマンドのいずれかには、アイコンが必要がある場合は、追加、[ビットマップ](../../extensibility/bitmaps-element.md)要素を`Commands`要素。 次に、各アイコンの追加、[ビットマップ](../../extensibility/bitmap-element.md)要素を`Bitmaps`要素。 これは、ビットマップ リソースの場所を指定します。 詳細については、次を参照してください。[アイコンを追加するメニュー コマンドに対する](../../extensibility/adding-icons-to-menu-commands.md)です。  
  
 ほとんどのメニューのグループ、およびコマンドを正しく配置する、親子構造に依存することができます。 非常に大量のコマンド セットの場合は、コマンドの配置を指定することをお勧めメニューのグループ、またはコマンドは、複数の場所に表示する必要があります、または。  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE の UI 要素を配置する親子関係に依存するには  
  
1.  一般的な親は、作成、`Parent`内の各要素`Menu`、 `Group`、および`Command`パッケージで定義されている要素です。  
  
     対象、`Parent`要素は、メニューまたはメニューを含むグループをグループ、またはコマンド。  
  
    1.  設定、`guid`属性の名前を`GuidSymbol`コマンド セットを定義する要素。 ターゲット要素が、パッケージの一部でない場合は、対応する .vsct ファイルで定義されている、そのコマンド セットの guid を使用します。  
  
    2.  設定、`id`に一致する属性、`id`ターゲット メニューまたはグループの属性です。 メニューと Visual Studio によって公開されているグループの一覧については、次を参照してください。 [Guid と Visual Studio メニューの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)または[Guid と Visual Studio ツールバーの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)します。  
  
 IDE では、配置する UI 要素の数が大きい場合、または複数の場所に表示される要素がある場合は、定義で、配置、 [CommandPlacements](../../extensibility/commandplacements-element.md)要素は、次の手順で示すようにします。  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>コマンドの配置を使用して、IDE の UI 要素を配置するには  
  
1.  後に、`Commands`要素を追加、`CommandPlacements`要素。  
  
2.  `CommandPlacements`要素を追加、`CommandPlacement`各メニューのグループ、または配置するコマンドの要素。  
  
     各`CommandPlacement`要素または`Parent`要素が 1 つのメニューのグループ、またはコマンドを 1 つの IDE 場所に配置します。 UI 要素が 1 つの親を持つことができますだけが、コマンド配置を複数持つことができます。 複数の場所で、UI 要素を配置するには追加、`CommandPlacement`所在地ごとの要素。  
  
3.  設定、`guid`と`id`の各属性`CommandPlacement`メニューまたはと同様のグループをホストする要素と、`Parent`要素。 設定することも、 `priority` UI 要素の相対位置を確立するために属性。  
  
 親子関係での配置とコマンドの配置を混在させることができます。 ただし、非常に大量のコマンド セットをお勧めコマンドの配置のみを使用することです。  
  
### <a name="adding-specialized-behaviors"></a>特殊な動作を追加します。  
 使用することができます[CommandFlag](../../extensibility/command-flag-element.md)要素の外観と可視性を変更する、たとえばメニューとコマンドの動作を変更します。 使用して、コマンドが表示されているときにも影響が[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)を使用してキーボード ショートカットを追加または[KeyBindings](../../extensibility/keybindings-element.md)です。 組み込みのビヘイビアー専門的なメニューやコマンドが既に特定の種類。  
  
##### <a name="to-add-specialized-behaviors"></a>特殊な動作を追加するには  
  
1.  UI 要素を表示するコンテキストでのみ特定 UI、たとえば、ソリューションが読み込まれるときに、可視性の制約を使用します。  
  
    1.  後に、`Commands`要素を追加、`VisibilityConstraints`要素。  
  
    2.  各 UI には、制約の項目が、追加、 [VisibilityItem](../../extensibility/visibilityitem-element.md)要素。  
  
    3.  各`VisibilityItem`要素、設定、`guid`と`id`メニューのグループ、またはコマンド、および設定する属性、`context`で定義されている属性をする UI コンテキストを<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>クラスです。 詳細については、次を参照してください。 [VisibilityItem 要素](../../extensibility/visibilityitem-element.md)です。  
  
2.  コードで、表示または UI 項目の可用性を設定するには、次のコマンド フラグの 1 つ以上を使用します。  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     詳細については、次を参照してください。[コマンド フラグ要素](../../extensibility/command-flag-element.md)です。  
  
3.  方法が表示されたら、または要素の外観を動的に変更を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
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
  
    -   テキスト  
  
    -   TextOnly  
  
     詳細については、次を参照してください。[コマンド フラグ要素](../../extensibility/command-flag-element.md)です。  
  
4.  要素でのコマンドを受信したときの処理方法を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
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
  
     詳細については、次を参照してください。[コマンド フラグ要素](../../extensibility/command-flag-element.md)です。  
  
5.  メニューまたはメニューの項目をメニューに依存するキーボード ショートカットをアタッチする追加アンパサンド文字 ('& ') で、`ButtonText`メニューまたはメニュー項目の要素。 アンパサンドに続く文字は、親メニューを開いている場合にアクティブなショートカットです。  
  
6.  コマンドにショートカット メニューに依存しないキーをアタッチするには使用[KeyBindings](../../extensibility/keybindings-element.md)です。 詳細については、次を参照してください。 [KeyBinding 要素](../../extensibility/keybinding-element.md)です。  
  
7.  メニュー テキストをローカライズするを使用して、`LocCanonicalName`要素。 詳細については、次を参照してください。[文字列要素](../../extensibility/strings-element.md)です。  
  
 一部のメニューおよびボタンの種類には、特殊な動作が含まれます。 次の表は、いくつかの特別なメニューおよびボタンの種類について説明します。 その他の種類を参照して、`types`属性の説明を[Menu 要素](../../extensibility/menu-element.md)、[ボタン要素](../../extensibility/button-element.md)、および[コンボ要素](../../extensibility/combo-element.md)です。  
  
 コンボ ボックス  
 コンボ ボックスは、ツールバーの使用できるドロップダウン リストです。 UI にコンボ ボックスを追加するには、作成、[コンボ](../../extensibility/combos-element.md)内の要素、`Commands`要素。 追加し、`Combos`要素、`Combo`を追加するには、各コンボ ボックスの要素。 `Combo`要素と同じである属性として子`Button`要素とも持ちます`DefaultWidth`と`idCommandList`属性。 `DefaultWidth`属性 (ピクセル単位) の幅を設定して、`idCommandList`属性は、コンボ ボックスに入力に使用されるコマンド ID を参照します。 詳細については、次を参照してください。、`Combo`要素のドキュメントです。  
  
 MenuController  
 メニュー コント ローラーは、その横にある矢印の付いたボタンです。 矢印をクリックすると、一覧が開きます。 UI にメニュー コント ローラーを追加するには、作成、`Menu`要素とその`type`属性を**MenuController**または**MenuControllerLatched**目的の動作に応じて、します。 メニュー コント ローラーを作成するには、親として設定、`Group`要素。 メニュー コント ローラーは、そのグループのすべての子をそのドロップダウン リストに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio コマンド テーブル (です。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)