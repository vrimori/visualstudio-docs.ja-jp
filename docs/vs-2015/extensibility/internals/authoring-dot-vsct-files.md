---
title: 作成します。Vsct ファイル |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 50dc50aee377a4685527e57dc2af5d9946639946
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772171"
---
# <a name="authoring-vsct-files"></a>作成します。Vsct ファイル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このドキュメントでは、Visual Studio 統合開発環境 (IDE) にメニュー項目、ツールバー、およびその他のユーザー インターフェイス (UI) 要素を追加する .vsct ファイルを作成する方法を示します。 .Vsct ファイルがまだない Visual Studio パッケージ (VSPackage) を UI 要素を追加する場合は、次の手順を使用します。  
  
 新しいプロジェクトの場合、メニュー コマンド、ツール ウィンドウ、またはカスタム エディターの必須の要素が既に選択内容に応じて .vsct ファイルを生成するためには、Visual Studio パッケージ テンプレートを使用することをお勧めします。 VSPackage の要件を満たすには、この .vsct ファイルを変更することができます。 .Vsct ファイルを変更する方法の詳細については、例を参照してください。[拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)します。  
  
## <a name="authoring-the-file"></a>ファイルの作成  
 次のフェーズで .vsct ファイルを作成します。 ファイルとリソースの構造を作成、UI 要素を宣言、IDE では、UI 要素を配置、および任意の特殊な動作を追加します。  
  
### <a name="file-structure"></a>ファイルの構造  
 .Vsct ファイルの基本的な構造は、 [CommandTable](../../extensibility/commandtable-element.md)ルート要素を含む、[コマンド](../../extensibility/commands-element.md)要素と[シンボル](../../extensibility/symbols-element.md)要素。  
  
##### <a name="to-create-the-file-structure"></a>ファイル構造を作成するには  
  
1.  次の手順に従って、プロジェクトに .vsct ファイルを追加[方法: を作成します。Vsct ファイル](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)します。  
  
2.  必要な名前空間を追加、`CommandTable`要素は、次の例に示すようにします。  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  `CommandTable`要素を追加、`Commands`すべてのカスタム メニューのツールバー、コマンド グループ、およびコマンドをホストする要素。 カスタム UI 要素を読み込むように、`Commands`要素があります、`Package`属性は、パッケージの名前に設定します。  
  
     後に、`Commands`要素を追加、`Symbols`要素をパッケージと名前の Guid を定義し、UI 要素のコマンド Id。  
  
### <a name="including-visual-studio-resources"></a>Visual Studio のリソースを含める  
 使用して、 [Extern](../../extensibility/extern-element.md) Visual Studio のコマンドと、IDE で、UI 要素を配置するために必要なメニューを定義するファイルにアクセスする要素。 使用して、パッケージの外部で定義されているコマンドを使用する場合、 [UsedCommands](../../extensibility/usedcommands-element.md) Visual Studio に通知する要素。  
  
##### <a name="to-include-visual-studio-resources"></a>Visual Studio のリソースを含める  
  
1.  上部にある、`CommandTable`要素、1 つ追加`Extern`要素を設定し、参照する外部のファイルごとに、`href`属性をファイルの名前にします。 Visual Studio のリソースにアクセスする次のヘッダー ファイルを参照することができます。  
  
    -   Stdidcmd.h は、Visual Studio によって公開されるすべてのコマンドの Id を定義します。  
  
    -   Vsshlids.h には、Visual Studio のメニューのコマンド Id が含まれています。  
  
2.  パッケージが Visual Studio によって、または他のパッケージで定義されている任意のコマンドを呼び出す場合は、追加、`UsedCommands`要素の後に、`Commands`要素。 この要素で設定を[UsedCommand](../../extensibility/usedcommand-element.md)各コマンドを呼び出すが、パッケージの一部ではないです。 設定、`guid`と`id`の属性、`UsedCommand`要素を呼び出すコマンドの GUID と ID の値。 Guid と Visual Studio の Id のコマンドを検索する方法の詳細については、次を参照してください。 [Guid と Visual Studio コマンドの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)します。 他のパッケージからコマンドを呼び出すには、GUID と、それらのパッケージの .vsct ファイルで定義されているコマンドの ID を使用します。  
  
### <a name="declaring-ui-elements"></a>UI 要素を宣言します。  
 内のすべての新しい UI 要素の宣言、 `Symbols` .vsct ファイルのセクション。  
  
##### <a name="to-declare-ui-elements"></a>UI 要素を宣言するには  
  
1.  `Symbols`要素、3 つ追加[GuidSymbol](../../extensibility/guidsymbol-element.md)要素。 各`GuidSymbol`要素には、`name`属性と`value`属性。 設定、`name`属性、要素の目的が反映されるようにします。 `value`属性は GUID を受け取ります。 (GUID を生成する、**ツール**] メニューのをクリックして**GUID の作成**、し、[**レジストリ形式**)。  
  
     最初の`GuidSymbol`要素が、パッケージを表すし、通常、子がありません。 2 番目の`GuidSymbol`要素を表しますコマンドは、設定すると、し、メニューのグループ、およびコマンドを定義するシンボルのすべてが含まれます。 3 番目`GuidSymbol`要素は、イメージ ストアを表すし、コマンドのアイコンのすべてのシンボルが含まれています。 アイコンを使用するコマンドがない場合は、3 つ目を省略できます`GuidSymbol`要素。  
  
2.  `GuidSymbol`コマンド セットを表す要素が 1 つ以上追加[IDSymbol](../../extensibility/idsymbol-element.md)要素。 これらの各は、メニューのツールバー、グループ、または UI を追加するコマンドを表します。  
  
     各`IDSymbol`要素、設定、`name`属性を使用して、対応するメニューのグループ、または、コマンドを参照して、設定の名前に、`value`コマンド id を表す 16 進数の要素。2 つ`IDSymbol`が同じ親を持つ要素が同じ値を持つことができます。  
  
3.  UI 要素のいずれかには、アイコンが必要とする場合は、追加、`IDSymbol`する各アイコンの要素、`GuidSymbol`要素、イメージ ストアを表します。  
  
### <a name="putting-ui-elements-in-the-ide"></a>IDE の UI 要素を配置します。  
 [メニュー](../../extensibility/menus-element.md)要素、[グループ](../../extensibility/groups-element.md)要素、および[ボタン](../../extensibility/buttons-element.md)要素には、メニューのグループ、および、パッケージで定義されているコマンドのすべての定義が含まれています。 使用するか、IDE でこれらのメニューのグループ、およびコマンドを配置、[親](../../extensibility/parent-element.md)またはを使用して、UI 要素の定義の一部である要素を[CommandPlacement](../../extensibility/commandplacement-element.md)である要素では、別の場所で定義されています。  
  
 各`Menu`、 `Group`、および`Button`要素には、`guid`属性と`id`属性。 常に設定、`guid`属性の名前に一致するように、`GuidSymbol`コマンドを表す要素を選択し、設定すると、設定、`id`属性の名前を`IDSymbol`メニューのグループ、または、でコマンドを表す要素`Symbols`セクション。  
  
##### <a name="to-define-ui-elements"></a>UI 要素を定義するには  
  
1. 新しいメニューのサブメニュー、ショートカット メニューやツールバーを定義する場合は、追加、`Menus`要素を`Commands`要素。 次に、各メニューを作成するには、追加、[メニュー](../../extensibility/menu-element.md)要素を`Menus`要素。  
  
    設定、`guid`と`id`の属性、`Menu`要素、および設定して、`type`属性をこの種のメニューを選択します。 設定することも、`priority`属性を親グループで、メニューの相対位置を確立します。  
  
   > [!NOTE]
   >  `priority`属性は、ツールバーとコンテキスト メニューには適用されません。  
  
2. Visual Studio IDE のすべてのコマンドは、メニューおよびツールバーの直接の子であるコマンド グループでホストする必要があります。 IDE に新しいメニューまたはツールバーを追加する場合、新しいコマンドのグループが含まれますする必要があります。 コマンドは、視覚的にグループ化できるように、既存のメニューおよびツールバーにコマンドのグループを追加できます。  
  
    最初に作成する必要がある新しいコマンドのグループを追加すると、`Groups`要素を追加し、[グループ](../../extensibility/group-element.md)コマンド グループごとの要素。  
  
    設定、`guid`と`id`の各属性`Group`要素、および設定して、`priority`属性を親メニューのグループの相対位置を確立します。 詳細については、次を参照してください。[ボタンの再利用可能なグループの作成](../../extensibility/creating-reusable-groups-of-buttons.md)です。  
  
3. IDE に新しいコマンドを追加する場合は、追加、`Buttons`要素を`Commands`要素。 次に、各コマンドでは、追加、[ボタン](../../extensibility/button-element.md)要素を`Buttons`要素。  
  
   1. 設定、`guid`と`id`の各属性`Button`要素、および設定して、`type`ボタンの種類に属性します。 設定することも、`priority`属性を親グループで、コマンドの相対位置を確立します。  
  
      > [!NOTE]
      >  使用`type="button"`標準メニュー コマンドとツールバーのボタン。  
  
   2. `Button`要素を追加、[文字列](../../extensibility/strings-element.md)要素を含む、 [ButtonText](../../extensibility/buttontext-element.md)要素と[CommandName](../../extensibility/commandname-element.md)要素。 `ButtonText`要素がメニュー項目、またはツール バー ボタンのツールヒントのテキスト ラベルを提供します。 `CommandName`要素も、コマンドで使用するコマンドの名前を提供します。  
  
   3. コマンドがアイコンである場合は、作成、[アイコン](../../extensibility/icon-element.md)内の要素、`Button`要素、およびセットの`guid`と`id`属性を`Bitmap`アイコンの要素。  
  
      > [!NOTE]
      >  ツール バー ボタンのアイコンがあります。  
  
      詳細については、次を参照してください。 [Menucommand とします。OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)します。  
  
4. コマンドのいずれかには、アイコンが必要とする場合は、追加、[ビットマップ](../../extensibility/bitmaps-element.md)要素を`Commands`要素。 次に、各アイコンの追加、[ビットマップ](../../extensibility/bitmap-element.md)要素を`Bitmaps`要素。 これは、ビットマップ リソースの場所を指定します。 詳細については、次を参照してください。[メニュー コマンドに追加するアイコン](../../extensibility/adding-icons-to-menu-commands.md)します。  
  
   ほとんどのメニューのグループ、およびコマンドを正しく配置する親子構造を利用できます。 非常に大量のコマンド セットでは、コマンドの配置を指定することをお勧め メニューのグループ、またはコマンドは、複数の場所に表示する必要があります、または。  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>IDE の UI 要素を配置する親子関係に依存するには  
  
1. 一般的な親は、作成、`Parent`の各要素`Menu`、 `Group`、および`Command`パッケージで定義されている要素。  
  
    対象、`Parent`要素がメニューやメニューを含むグループをグループ、またはコマンド。  
  
   1.  設定、`guid`属性の名前を`GuidSymbol`コマンド セットを定義する要素。 ターゲット要素でない場合、パッケージの一部は、対応する .vsct ファイルで定義されているそのコマンド セットの guid を使用します。  
  
   2.  設定、`id`と一致する属性、 `id` [ターゲット] メニューまたはグループの属性です。 メニューおよび Visual Studio によって公開されているグループの一覧については、次を参照してください。 [Guid と Visual Studio メニューの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)または[Guid と Visual Studio ツールバーの Id の](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)します。  
  
   IDE では、配置する UI 要素の数が多いがある場合、または複数の場所に表示される要素がある場合は、定義への配置、 [CommandPlacements](../../extensibility/commandplacements-element.md)要素は、次の手順で示すようにします。  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>コマンド配置を使用して、IDE の UI 要素を配置するには  
  
1. 後に、`Commands`要素を追加、`CommandPlacements`要素。  
  
2. `CommandPlacements`要素を追加、`CommandPlacement`要素の各メニューのグループ、または配置するコマンド。  
  
    各`CommandPlacement`要素または`Parent`要素が 1 つのメニューのグループ、またはコマンドを IDE の 1 つの場所に配置します。 UI 要素が持てる親は 1 つだけですが、コマンドの配置を複数持つことができます。 UI 要素を複数の場所に配置するには追加、`CommandPlacement`場所ごとの要素。  
  
3. 設定、`guid`と`id`の各属性`CommandPlacement`ホスティングのメニューまたはグループの場合と同様、する要素の場合、`Parent`要素。 設定することも、 `priority` UI 要素の相対位置を確立するために属性。  
  
   親子関係を配置し、コマンドの配置を混在させることができます。 ただし、非常に大量のコマンド セットでは、コマンドの配置のみを使用することを勧めします。  
  
### <a name="adding-specialized-behaviors"></a>特殊な動作を追加します。  
 使用することができます[CommandFlag](../../extensibility/command-flag-element.md)たとえばメニューとコマンドの動作を変更する、外観と可視性を変更する要素。 使用して、コマンドが表示されている場合に影響することができますも[VisibilityConstraints](../../extensibility/visibilityconstraints-element.md)を使用してキーボード ショートカットを追加または[KeyBindings](../../extensibility/keybindings-element.md)します。 メニューとコマンドが既にある種の専門的なビヘイビアーが組み込まれています。  
  
##### <a name="to-add-specialized-behaviors"></a>特殊な動作を追加するには  
  
1. UI 要素を表示する UI、特定のコンテキストなどでのみソリューションが読み込まれるときに、可視性の制約を使用します。  
  
   1.  後に、`Commands`要素を追加、`VisibilityConstraints`要素。  
  
   2.  各 UI には、制約の項目が、追加、 [VisibilityItem](../../extensibility/visibilityitem-element.md)要素。  
  
   3.  各`VisibilityItem`要素、設定、`guid`と`id`メニューのグループ、またはコマンド、および設定する属性、 `context` UI のコンテキストで定義されている属性、<xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>クラス。 詳細については、次を参照してください。 [VisibilityItem 要素](../../extensibility/visibilityitem-element.md)します。  
  
2. コードで、可視性または UI アイテムの可用性を設定するには、次のコマンド フラグの 1 つ以上を使用します。  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     詳細については、次を参照してください。 [Command Flag 要素](../../extensibility/command-flag-element.md)します。  
  
3. 要素の表示、またはその外観を動的に変更を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
   - 通常  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - pict  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - テキスト  
  
   - TextOnly  
  
     詳細については、次を参照してください。 [Command Flag 要素](../../extensibility/command-flag-element.md)します。  
  
4. コマンドを受信したときの要素の反応を変更するには、次のコマンド フラグの 1 つ以上を使用します。  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - フィルター キー機能  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - PostExec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     詳細については、次を参照してください。 [Command Flag 要素](../../extensibility/command-flag-element.md)します。  
  
5. メニューまたはメニュー項目をメニューに依存するキーボード ショートカットをアタッチする追加のアンパサンド文字 ('& ') で、`ButtonText`メニューまたはメニュー項目の要素。 アンパサンドの後の文字は、親メニューが開いているときにアクティブなキーボード ショートカットが。  
  
6. コマンドにアタッチしてショートカット メニューに依存しないキーを使用して[KeyBindings](../../extensibility/keybindings-element.md)します。 詳細については、次を参照してください。 [KeyBinding 要素](../../extensibility/keybinding-element.md)します。  
  
7. メニュー テキストをローカライズするには、使用、`LocCanonicalName`要素。 詳細については、次を参照してください。[文字列要素](../../extensibility/strings-element.md)します。  
  
   一部のメニューおよびボタンの種類には、特殊な動作が含まれます。 次の表では、いくつかの特別なメニューとボタンの種類について説明します。 他の種類では、次を参照してください。、`types`属性の説明で[メニュー要素](../../extensibility/menu-element.md)、[ボタン要素](../../extensibility/button-element.md)、および[Combo 要素](../../extensibility/combo-element.md)します。  
  
   コンボ ボックス  
   コンボ ボックスは、ツールバーの使用できるドロップダウン リストです。 UI には、コンボ ボックスを追加するには、作成、 [Combos](../../extensibility/combos-element.md)内の要素、`Commands`要素。 追加し、`Combos`要素、`Combo`要素を追加するには、各コンボ ボックス。 `Combo` 要素の属性と子としてが同じである`Button`要素も`DefaultWidth`と`idCommandList`属性。 `DefaultWidth`属性 (ピクセル単位) の幅を設定して、`idCommandList`属性は、コンボ ボックスに入力するために使用するコマンド ID をポイントします。 詳細については、次を参照してください。、`Combo`要素のドキュメント。  
  
   MenuController  
   メニュー コント ローラーは、その横にある矢印の付いたボタンです。 矢印をクリックすると、リストが開きます。 UI には、メニュー コント ローラーを追加するには、作成、`Menu`要素その`type`属性を**MenuController**または**MenuControllerLatched**、目的の動作によって異なります。 親として設定 メニュー コント ローラーを設定する、`Group`要素。 メニュー コント ローラーは、そのグループのすべての子をそのドロップダウン リストに表示されます。  
  
## <a name="see-also"></a>関連項目  
 [拡張メニューとコマンド](../../extensibility/extending-menus-and-commands.md)   
 [Visual Studio コマンド テーブル (します。Vsct) ファイル](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML スキーマ リファレンス](../../extensibility/vsct-xml-schema-reference.md)

