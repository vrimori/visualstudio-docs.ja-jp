---
title: Visual Studio の色の共有 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72aaaa4a3eb75043f4a2cf3bdd20352bdd2af93b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856692"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio の共有の色
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

共通の Visual Studio シェル要素を使用する UI を設計する場合、または類似の機能との一貫性をインターフェイス要素に持たせる場合、パッケージ定義ファイルにある既存のトークン名を使用して色を選択し、割り当てます。 これにより、UI が Visual Studio 環境全体で一貫性を保ち、テーマが追加された場合や更新された場合に自動的に更新されるようになります。  
  
 この記事では、類似の UI を構築する際に参照できる一般的な UI 要素と UI 要素で使用されるトークン名について説明します。 これらの色のトークンにアクセスする方法の詳細については、「 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)」を参照してください。  
  
 トークン名は次のように正しく使用してください。  
  
-   **色自体ではなく、機能に基づいてトークン名を使用します。** 一般的な共有色は、特定のインターフェイス要素と関連付けられ、同一または類似した機能に対してのみ使用されることを想定しています。 たとえば、押されているコンボ ボックスの色を、単にその色が好きという理由で進行状況を示す回転アニメーションに再利用しないでください。 コンボ ボックスとアニメーションの機能は異なり、コンボ ボックスに関連付けられている色が変更された場合、アニメーション要素にとっては適切な色でなくなる可能性があります。 色を一貫して使用すると、ユーザーの理解を助け、混乱を避けるために役立ちます。  
  
-   **適切な組み合わせでは、背景色とテキストの色を使用します。** テキストと共に使用することが想定された背景色には、テキストの色が関連付けられています。 その背景に指定されている色以外のテキストの色を使用しないでください。 テキストの色が関連付けられていない背景色は、テキストを表示する予定のサーフェイスで使用しないでください。 テキストの色と背景色の他の組み合わせによって、読み取り不可能なインターフェイスが生成される場合があります。  
  
-   **その場所に適したコントロールの色を使用します。** 特定の状態では、一部の Visual Studio コントロールに個別の境界線の色と背景色がありません。 代わりに、それらのコントロールにはその背後のサーフェイスから色が適用されます。 コントロールを配置する場所に適したトークン名を常に使用してください。  
  
> [!IMPORTANT]
>  「スタート ページ」や"Cider"カテゴリで見つかったトークンは使用しません。  
  
## <a name="command-structures"></a>コマンドの構造  
  
###  <a name="BKMK_CommandMenus"></a> メニュー  
 メニューに Visual Studio 内で複数の場所で発生することができます。 埋め込みドキュメントまたはツールのウィンドウまたは IDE 全体のさまざまな場所で右クリックして、メイン メニュー バー。 他の UI 要素に関連付けられたメニューの実装については、それぞれの要素のセクションで説明します。 Visual Studio 環境で提供される標準のメニュー実装を常に使用してください。 ただし、まれに、標準の Visual Studio メニューにアクセスできないことがあります。 このような場合は、次のトークン名を使用して、UI が Visual Studio の他のメニューと一貫性を保つようにします。  
  
 ![メニューの赤線](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303 000_MenuRedline")  
  
 使用するケース  
 -   カスタム メニューを作成する必要がある場合。  
  
- Visual Studio メニューと一致させる新しい UI コンポーネントがある場合。  
  
  使用しないケース  
  背景色単独の場合。 常に指定された背景と前景の組み合わせを使用します。  
  
#### <a name="menu-title"></a>メニュー タイトル  
 メニュー タイトルは、背景、境界線、タイトル テキスト、および通常、メニューがコマンド バーにあるときは、オプションのグリフで構成されます。  
  
 ![メニュー タイトルの赤線](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303 001_MenuTitleRedline")  
  
 使用するケース  
 カスタム メニュー タイトルを作成する場合。  
  
 使用しないケース  
 -   メニュー タイトルと常に一致させるわけではないすべてのもの。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![既定のメニュー タイトル](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303 002_MenuTitleDefault")  
  
  **メニュー タイトル**  
  
  背景  
  
  なし  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextActive`  
  
  ![既定グリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")  
  
  **グリフのメニュー タイトル**  
  
  前景 (グリフ)  
  
  `Environment.CommandBarMenuGlyph`  
  
  境界線  
  
  なし  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ホバー メニュー タイトル](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303 004_MenuTitleHover")  
  
  **メニュー タイトル**  
  
  背景  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextHover`  
  
  ![ポインターを合わせるとグリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")  
  
  **グリフのメニュー タイトル**  
  
  前景 (グリフ)  
  
  `Environment.CommandBarMenuMouseOverGlyph`  
  
  境界線  
  
  `Environment.CommandBarBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![押されたメニュー タイトル](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303 006_MenuTitlePressed")  
  
  **メニュー タイトル**  
  
  背景  
  
  `Environment.CommandBarMenuBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextActive`  
  
  ![押されているグリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")  
  
  **グリフのメニュー タイトル**  
  
  前景 (グリフ)  
  
  `Environment.CommandBarMenuMouseDownGlyph`  
  
  境界線  
  
  `Environment.CommandBarMenuBorder`  
  
  左側、上部、右側のみ。  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![無効時のグリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")  
  
  **グリフのメニュー タイトル**  
  
  背景  
  
  なし  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextInactive`  
  
  前景 (グリフ)  
  
  `Environment.CommandBarTextInactive`  
  
  境界線  
  
  なし  
  
#### <a name="menu"></a>メニュー  
 個々のメニュー項目は、メニュー テキストとオプションのアイコン、チェック ボックス、またはサブメニュー グリフで構成されます。 その背景色とテキストの色はホバー時に変化します。 この色トークンは、背景と前景のペアです。  
  
 ![メニュー項目の赤線](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303 009_MenuItemRedline")  
  
 使用するケース  
 メニュー バーまたはコマンド バーから起動されるドロップダウン リスト。  
  
 使用しないケース  
 -   別のコンテキストで発生するドロップダウン リスト。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![メニューの既定値](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303 010_MenuDefault")  
  
  **Menu**  
  
  背景  
  
  `Environment.CommandBarMenuBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextActive`  
  
  前景 (サブメニュー グリフ)  
  
  `Environment.CommandBarMenuSubmenuGlyph`  
  
  境界線  
  
  `Environment.CommandBarMenuBorder`  
  
  アイコン チャネルの背景  
  
  `Environment.CommandBarMenuIconBackground`  
  
  区切り記号  
  
  `Environment.CommandBarMenuSeparator`  
  
  影  
  
  `Environment.DropShadowBackground`  
  
  ![チェックされたメニュー](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303 011_MenuChecked")  
  
  **チェック済み**  
  
  チェック マーク  
  
  `Environment.CommandBarCheckBox`  
  
  チェック マークの背景  
  
  `Environment.CommandBarSelectedIcon`  
  
  ![選択したメニュー](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303 012_MenuSelected")  
  
  **選択されています。**  
  
  アイコンの背景  
  
  `Environment.CommandBarSelected`  
  
  アイコンの境界線  
  
  `Environment.CommandBarSelectedBorder`  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![メニュー ホバー](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303 013_MenuHover")  
  
  **メニュー項目**  
  
  背景  
  
  `Environment.CommandBarMenuItemMouseOver`  
  
  前景 (テキスト)  
  
  `Environment.CommandBarMenuItemMouseOver`  
  
  前景 (サブメニュー グリフ)  
  
  `Environment.CommandBarMenuMouseOverSubmenuGlyph`  
  
  ![チェックされたメニュー ホバー](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303 014_MenuHoverChecked")  
  
  **チェック済み**  
  
  チェック マーク  
  
  `Environment.CommandBarCheckBoxMouseOver`  
  
  チェック マークの背景  
  
  `Environment.CommandBarHoverOverSelectedIcon`  
  
  ![選択されたメニュー ホバー](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303 015_MenuHoverSelected")  
  
  **選択されています。**  
  
  アイコンの背景  
  
  `Environment.CommandBarHoverOverSelected`  
  
  アイコンの境界線  
  
  `Environment.CommandBarHoverOverSelectedIconBorder`  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![メニューの無効化](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303 016_MenuDisabled")  
  
  メニュー項目  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextInactive`  
  
  前景 (サブメニュー グリフ)  
  
  `Environment.CommandBarMenuSubmenuGlyph`  
  
  ![メニューの無効化チェック](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303 017_MenuDisabledChecked")  
  
  チェック済み  
  
  チェック マーク  
  
  `Environment.CommandBarCheckBoxDisabled`  
  
  チェック マークの背景  
  
  `Environment.CommandBarSelectedIconDisabled`  
  
### <a name="command-bar"></a>コマンド バー  
 コマンド バーは、Visual Studio IDE 内の複数の場所、特にコマンド シェルフ、およびツールまたはドキュメント ウィンドウへの埋め込みで表示できます。  
  
 通常は、Visual Studio 環境で提供される標準のコマンド バー実装を常に使用してください。 標準メカニズムを使用すると、すべての表示の詳細が正しく表示され、対話型要素が他の Visual Studio のコマンド バーのコントロールと一貫して動作するようになります。 ただし、独自のコマンド バーを作成する必要がある場合は、次のトークン名を使用してスタイルを正しく設定してください。  
  
 ![コマンド バーの赤線](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303 018_CommandBarRedline")  
  
 ![オーバーフロー ボタンの赤線](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303 019_OverflowButtonRedline")  
  
 使用するケース  
 埋め込みコマンド バーが必要だが、標準の Visual Studio のコマンド バー実装を使用できない場所。  
  
 使用しないケース  
 -   コマンド バーに類似していない UI 要素。  
  
-   トークン名が指定されているもの以外のコマンド バー コンポーネント。  
  
#### <a name="command-bar-group"></a>コマンド バー グループ  
 コマンド バー グループは、関連する一連のコマンド バー コントロールで構成され、任意の数のボタン、分割ボタン、ドロップダウン メニュー、コンボ ボックス、またはメニューを含めることができます。 これらのコントロールの色は別々のトークン名によって制御され、このガイドの他の場所で個別に説明されています。 区切り線を使用して、コマンド バー グループを関連するサブグループに分割します。  
  
 ![コマンド バー グループの赤線](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303 020_CommandBarGroupRedline")  
  
 使用するケース  
 埋め込みコマンド バーが必要だが、標準の Visual Studio のコマンド バー実装を使用できない場所。  
  
 使用しないケース  
 -   コマンド バーに類似していない UI 要素。  
  
- トークン名が指定されているもの以外のコマンド バー コンポーネント。  
  
  **既定** (他の状態はありません)  
  
  要素  
  
  トークン名: Category.color  
  
  背景  
  
  `Environment.CommandBarGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  境界線  
  
  `Environment.CommandBarToolBarBorder`  
  
  ドラッグ ハンドル  
  
  `Environment.CommandBarDragHandle`  
  
  区切り記号  
  
  `Environment.CommandBarToolBarSeparator`  
  
  `Environment.CommandBarToolBarSeparatorHighlight`  
  
#### <a name="command-icons"></a>コマンド アイコン  
 ![コマンド アイコンの赤線](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303 021_CommandIconRedline1")  
  
 ![コマンド アイコンの赤線](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303 022_CommandIconRedline2")  
  
 使用するケース  
 コマンド バーに配置されるボタン。  
  
 使用しないケース  
 -   独自のトークン名があるコントロール。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![アイコンの既定値をコマンド](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303 023_CommandIconDefault")  
  
  **既定値**  
  
  背景  
  
  該当なし (コマンド バーの背景から継承)  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextActive`  
  
  境界線  
  
  N/A  
  
  ![コマンド アイコンの既定値が選択されている](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")  
  
  **選択されています。**  
  
  背景  
  
  `Environment.CommandBarSelected`  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextSelected`  
  
  境界線  
  
  `Environment.CommandBarSelectedBorder`  
  
  **ホバー時とキーボード フォーカス**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![コマンド アイコン ホバー](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303 025_CommandIconHover")  
  
  **ポインターを合わせると標準**  
  
  背景  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextHover`  
  
  境界線  
  
  `Environment.CommandBarBorder`  
  
  ![コマンド アイコン ホバーが選択されている](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303 026_CommandIconHoverSelected")  
  
  **ポインターを合わせると選択**  
  
  背景  
  
  `Environment.CommandBarHoverOverSelected`  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextHoverOverSelected`  
  
  境界線  
  
  `Environment.CommandBarHoverOverSelectedIconBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![押されたコマンド アイコン](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303 027_CommandIconPressed")  
  
  **押されたコマンド アイコン**  
  
  背景  
  
  `Environment.CommandBarMouseDownBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextMouseDown`  
  
  境界線  
  
  `Environment.CommandBarBorder`  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![無効になっているコマンド アイコン](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303 028_CommandIconDisabled")  
  
  **無効になっているコマンド アイコン**  
  
  背景  
  
  該当なし (コマンド バーの背景から継承)  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextInactive`  
  
  境界線  
  
  N/A  
  
####  <a name="BKMK_CommandComboBox"></a> コンボ ボックス  
  
> [!IMPORTANT]
>  コンボ ボックスはドロップダウンに似ていますが、編集可能なテキスト領域が含まれます。 ドロップダウンに編集可能なテキスト領域が含まれていない場合は、 [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)に記載した色トークンを使用します。  
  
 ![コンボ ボックスの赤線](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303 029_ComboBoxRedline")  
  
 使用するケース  
 -   カスタム コンボ ボックスを作成する場合。  
  
- コンボ ボックスに類似したコマンド バー コントロールを作成する場合。  
  
  使用しないケース  
  -   コマンド バー UI と常に一致させるわけではないすべてのもの。  
  
- スタイル設定されたコンボ ボックスにアクセスできる場合。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![コンボ ボックスの入力フィールド](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303 030_ComboBoxInputField")  
  
  **入力フィールド**  
  
  背景  
  
  `Environment.ComboBoxBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxText`  
  
  境界線  
  
  `Environment.ComboBoxBorder`  
  
  区切り記号  
  
  区切り記号なし  
  
  ![コンボ ボックスのドロップ&#45;下向きの矢印ボタン](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  該当なし (継承)  
  
  前景 (グリフ)  
  
  `Environment.ComboBoxGlyph`  
  
  ![コンボ ボックス&#47;ドロップ&#45;一覧](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")  
  
  **ドロップダウン リスト**  
  
  背景  
  
  `Environment.ComboBoxPopupBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxItemText`  
  
  境界線  
  
  `Environment.ComboBoxPopupBorder`  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせると、コンボ ボックスの入力フィールド](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")  
  
  **入力フィールド**  
  
  背景  
  
  `Environment.ComboBoxMouseOverBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxMouseOverText`  
  
  境界線  
  
  `Environment.ComboBoxMouseOverBorder`  
  
  区切り記号  
  
  `Environment.ComboBoxMouseOverSeparator`  
  
  ![コンボ ボックス&#47;ドロップ&#45;下向きの矢印ボタンをホバー](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `Environment.ComboBoxButtonMouseOverBackground`  
  
  前景 (グリフ)  
  
  `Environment.ComboBoxMouseOverGlyph`  
  
  ![コンボ ボックス&#47;ドロップ&#45;ダウン ホバー リスト](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")  
  
  **ドロップダウン リスト**  
  
  背景 (メニュー項目)  
  
  `Environment.ComboBoxItemMouseOverBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxItemMouseOverText`  
  
  境界線 (メニュー項目)  
  
  `Environment.ComboBoxItemMouseOverBorder`  
  
  **重点を置いています**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Color.category  
  
  ![フォーカスされたコンボ ボックス入力フィールド](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")  
  
  **入力フィールド**  
  
  背景  
  
  `Environment.ComboBoxFocusedBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxFocusedText`  
  
  境界線  
  
  `Environment.ComboBoxFocusedBorder`  
  
  区切り記号  
  
  `Environment.ComboBoxFocusedButtonSeparator`  
  
  ![コンボ ボックス&#47;ドロップ&#45;フォーカスされたボタン ダウン](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `Environment.ComboBoxFocusedButtonBackground`  
  
  前景 (グリフ)  
  
  `Environment.ComboBoxFocusedGlyph`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Color.category  
  
  ![コンボ ボックスの入力フィールドが押された](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")  
  
  **入力フィールド**  
  
  背景  
  
  `Environment.ComboBoxMouseDownBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxMouseDownText`  
  
  境界線  
  
  `Environment.ComboBoxMouseDownBorder`  
  
  区切り記号  
  
  `Environment.ComboBoxMouseDownSeparator`  
  
  ![コンボ ボックス&#47;ドロップ&#45;下向きの矢印ボタンが押された](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `Environment.ComboBoxButtonMouseDownBackground`  
  
  前景 (グリフ)  
  
  `Environment.ComboBoxMouseDownGlyph`  
  
  **無効**  
  
  ![コンボ ボックスの入力フィールドが無効になっている](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")  
  
  **入力フィールド**  
  
  背景  
  
  `Environment.ComboBoxDisabledBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxDisabledText`  
  
  境界線  
  
  `Environment.ComboBoxDisabledBorder`  
  
  区切り記号  
  
  区切り記号なし  
  
  ![コンボ ボックス&#47;ドロップ&#45;下向きの矢印ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  なし  
  
  前景 (グリフ)  
  
  `Environment.ComboBoxDisabledGlyph`  
  
####  <a name="BKMK_CommandDropDown"></a> ドロップダウン リスト  
  
> [!IMPORTANT]
>  ドロップダウンはコンボ ボックスに似ていますが、編集可能なテキスト領域がありません。 ドロップダウンに編集可能なテキスト領域が含まれる場合は、 [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)に見つかる色トークンを使用します。  
  
 ![Drop&#45;ダウンの赤線](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303 042_DropdownRedline")  
  
 使用するケース  
 カスタム ドロップダウン リスト コントロールを作成する場合。  
  
 使用しないケース  
 -   ドロップダウン リストに類似していないすべてのもの。  
  
- コンボ ボックスまたは分割ボタン。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;選択フィールド ダウン](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303 043_DropdownSelectionField")  
  
  **選択フィールド**  
  
  背景  
  
  `Environment.DropDownBackground`  
  
  前景 (テキスト)  
  
  `DropDownText`  
  
  境界線  
  
  `DropDownBorder`  
  
  区切り記号  
  
  区切り記号なし  
  
  ![Drop&#45;下向きの矢印ボタン](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303 044_DropdownButton")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  なし  
  
  前景 (グリフ)  
  
  `Environment.DropDownGlyph`  
  
  ![Drop&#45;一覧](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303 045_DropdownList")  
  
  **ドロップダウン リスト**  
  
  背景  
  
  `Environment.DropDownPopupBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxItemText`  
  
  境界線  
  
  `Environment.DropDownPopupBorder`  
  
  影  
  
  `Environment.DropShadowBackground`  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;下の選択フィールドにポインターを合わせると](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")  
  
  **選択フィールド**  
  
  背景  
  
  `Environment.DropDownMouseOverBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.DropDownMouseOverText`  
  
  境界線  
  
  `Environment.DropDownMouseOverBorder`  
  
  区切り記号  
  
  `Environment.DropDownButtonMouseOverSeparator`  
  
  ![Drop&#45;下向きの矢印ボタンをホバー](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303 047_DropdownButtonHover")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `Environment.DropDownButtonMouseOverBackground`  
  
  前景 (グリフ)  
  
  `Environment.DropDownMouseOverGlyph`  
  
  ![Drop&#45;ダウン ホバー リスト](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303 048_DropdownListHover")  
  
  **ドロップダウン リスト**  
  
  背景 (メニュー項目)  
  
  `Environment.ComboBoxItemMouseOverBackground`  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxItemMouseOverText`  
  
  境界線 (メニュー項目)  
  
  `Environment.ComboBoxItemMouseOverBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;押された選択フィールド ダウン](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")  
  
  **選択フィールド**  
  
  背景  
  
  `Environment.DropDownMouseDownBackground`  
  
  前景 (テキスト)  
  
  `Environment.DropDownMouseDownText`  
  
  境界線  
  
  `Environment.DropDownMouseDownBorder`  
  
  区切り記号  
  
  `Environment.DropDownButtonMouseDownSeparator`  
  
  ![Drop&#45;下向きの矢印ボタンが押された](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `Environment.DropDownButtonMouseDownBackground`  
  
  前景 (グリフ)  
  
  `Environment.DropDownMouseDownGlyph`  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;下の選択フィールドに無効になっている](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")  
  
  背景  
  
  `Environment.DropDownDisabledBackground`  
  
  前景 (テキスト)  
  
  `Environment.DropDownDisabledText`  
  
  境界線  
  
  `Environment.DropDownDisabledBorder`  
  
  区切り記号  
  
  区切り記号なし  
  
  ![Drop&#45;下向きの矢印ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")  
  
  背景  
  
  N/A  
  
  前景 (グリフ)  
  
  `Environment.DropDownDisabledGlyph`  
  
#### <a name="split-button"></a>分割ボタン  
 分割ボタンは、ボタン、メニュー、コマンド バー テキストなど、他のコマンド バー コントロールと多くのトークン名を共有します。 ここでは利便性のために、すべての必要なアクション ボタンとドロップダウン ボタンのトークン名を繰り返しています。 分割ボタンのドロップダウン リストは、コマンド バー [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)の実装です。  
  
 ![分割ボタンの赤線](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303 053_SplitButtonRedline")  
  
 使用するケース  
 カスタム分割ボタンを構築する場合。  
  
 使用しないケース  
 -   他の種類のボタン。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![分割ボタン](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303 054_SplitButton")  
  
  **分割ボタン (既定値)**  
  
  背景  
  
  なし  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextActive`  
  
  前景 (グリフ)  
  
  `Environment.CommandBarSplitButtonGlyph`  
  
  境界線  
  
  N/A  
  
  区切り記号  
  
  N/A  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせると、分割ボタン](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303 055_SplitButtonHover")  
  
  **分割ボタン (ホバー時)**  
  
  背景  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextHover`  
  
  前景 (グリフ)  
  
  `Environment.CommandBarSplitButtonMouseOverGlyph`  
  
  境界線  
  
  `Environment.CommandBarBorder`  
  
  区切り記号  
  
  `Environment.CommandBarSplitButtonSeparator`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![分割ボタンが押された](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303 056_SplitButtonPressed")  
  
  **(押されている) 分割ボタン**  
  
  背景  
  
  `Environment.CommandBarMouseDownBackgroundBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `Environment.CommandBarTextMouseDown`  
  
  前景 (グリフ)  
  
  `Environment.CommandBarSplitButtonMouseDownGlyph`  
  
  境界線  
  
  `Environment.CommandBarBorder`  
  
  区切り記号  
  
  N/A  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![分割ボタンが無効になっている](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303 057_SplitButtonDisabled")  
  
  **分割ボタン (無効)**  
  
  背景  
  
  N/A  
  
  前景 (テキスト)  
  
  `Environment.ComboBoxItemTextInactive`  
  
  前景 (グリフ)  
  
  `Environment.CommandBarTextInactive`  
  
  境界線  
  
  N/A  
  
  区切り記号  
  
  N/A  
  
#### <a name="more-options-and-overflow-buttons"></a>"その他のオプション" ボタンと "オーバーフロー" ボタン  
 [その他のオプション] ボタンは、関連するコマンド バー ボタンを追加または削除して、コマンド バー グループをカスタマイズできる場合に使用します。 [オーバーフロー] ボタンは、横のスペースが不足しているためにコマンド バーが切り詰められた場合に表示され、クリックすると、表示できないコマンド バー ボタンを含むメニューが表示されます。 これら 2 つのボタンの色は、同じトークン名のセットによって制御されます。  
  
 ![その他のオプションの赤線](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303 058_MoreOptionsRedline")  
  
 使用するケース  
 カスタムの [その他のオプション] または [オーバーフロー] ボタン。  
  
 使用しないケース  
 [その他のオプション] または [オーバーフロー] ボタンと同様の機能を持たないボタン。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![その他のオプション](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303 059_MoreOptions")  
  
 **その他のオプション**  
  
 ![オーバーフロー ボタン](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303 060_Overflow")  
  
 **オーバーフロー**  
  
 背景  
  
 `Environment.CommandBarOptionsBackground`  
  
 前景 (グリフ)  
  
 `Environment.CommandBarOptionsGlyph`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせると、その他のオプション](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303 061_MoreOptionsHover")  
  
 **その他のオプション**  
  
 ![ポインターを合わせるとオーバーフロー](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303 062_OverflowOptions")  
  
 **オーバーフロー**  
  
 背景  
  
 `Environment.CommandBarOptionsMouseOverBackgroundBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (グリフ)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![その他のオプションが押された](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303 063_MoreOptionsPressed")  
  
 **その他のオプション**  
  
 ![押されたオーバーフロー](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303 064_OverflowPressed")  
  
 **オーバーフロー**  
  
 背景  
  
 `Environment.CommandBarOptionsMouseDownBackgroundBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (グリフ)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
## <a name="document-windows"></a>ドキュメント ウィンドウ  
 Visual Studio 環境で提供されるため、ドキュメント ウィンドウをレプリケートする必要はありません。 ただし、UI が Visual Studio 環境のこの部分と常に一貫性のある状態で表示されるように、ドキュメント ウィンドウで使用する色を活用することができます。  
  
 ドキュメント ウィンドウの色のトークンを使用する場合は、類似の要素に対してのみ、常にペアで使用するように注意する必要があります。 そうしない場合、UI に予期しない結果が発生します。  
  
### <a name="document-window-frame"></a>ドキュメント ウィンドウ フレーム  
 ドキュメント ウィンドウは IDE にドッキングしたり、別のウィンドウとしてフローティングさせたりすることができます。 ドキュメント ウィンドウは、IDE の外部にフローティングしているときも、ドキュメント ウェル内に存在し、IDE の一部であるときと同じ背景、境界線、テキスト、タブの色を持ちます。 ただし、ドキュメントは、独自の背景、境界線、テキストの色を持つフレーム内に配置されます。 ツール ウィンドウをドキュメント ウェルにドッキングした場合、ツール ウィンドウはタブの動作と色をドキュメント ウィンドウのトークン名から継承します。  
  
 ![ドッキングされたドキュメント ウィンドウの赤線](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")  
  
 **ドッキングされたドキュメント ウィンドウ**  
  
 ![フローティング ドキュメント ウィンドウの赤線](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")  
  
 **フローティング ドキュメント ウィンドウ**  
  
 使用するケース  
 ドキュメント ウィンドウと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ドキュメント: ドッキングまたはフローティング  
  
 背景  
  
 ドキュメントの種類によって異なります  
  
 前景 (テキスト)  
  
 ドキュメントの種類によって異なります  
  
 境界線  
  
 `Environment.ToolWindowBorder`  
  
 ![フォーカスされたフレーム](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303 067_FrameFocused")  
  
 **フォーカスされたフレーム: フローティング、**  
  
 背景  
  
 `Environment.ToolWindowFloatingFrame`  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowFloatingFrame`  
  
 前景 (グリフ)  
  
 `Environment.RaftedWindowButtonActiveGlyph`  
  
 境界線  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 境界線 (グリフ)  
  
 `Environment.RaftedWindowButtonActiveBorder`  
  
 透明に設定されます  
  
 ![フォーカスされていないフレーム](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303 068_FrameUnfocused")  
  
 **フレーム: フローティング、フォーカスされていません。**  
  
 背景  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 前景 (グリフ)  
  
 `Environment.RaftedWindowButtonInactiveGlyph`  
  
 境界線  
  
 `Environment.MainWindowInactiveBorder`  
  
 境界線 (グリフ)  
  
 `Environment.RaftedWindowButtonInactiveBorder`  
  
 透明に設定されます  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせるとフォーカスされたフレーム](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303 069_FrameFocusedHover")  
  
 **フォーカスされたフレーム: フローティング、**  
  
 背景 (グリフ)  
  
 `Environment.RaftedWindowButtonHoverActive`  
  
 前景 (グリフ)  
  
 `Environment.RaftedWindowButtonHoverActiveGlyph`  
  
 境界線 (グリフ)  
  
 `Environment.RaftedWindowButtonHoverActiveBorder`  
  
 ![フレーム ポインターを合わせるとフォーカスされていない](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303 070_FrameUnfocusedHover")  
  
 **フレーム: フローティング、フォーカスされていません。**  
  
 背景 (グリフ)  
  
 `EnvironmentRaftedWindowButtonHoverInactive`  
  
 前景 (グリフ)  
  
 `Environment.RaftedWindowButtonHoverInactiveGlyph`  
  
 境界線 (グリフ)  
  
 `Environment.RaftedWindowButtonHoverInactiveBorder`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![押されたフォーカスされたフレーム](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303 071_FrameFocusedPressed")  
  
 **フォーカスされたフレーム: フローティング、**  
  
 背景 (グリフ)  
  
 `Environment.RaftedWindowButtonDown`  
  
 前景 (グリフ)  
  
 `Environment.RaftedWindowButtonDownGlyph`  
  
 境界線 (グリフ)  
  
 `Environment.RaftedWindowButtonDownBorder`  
  
### <a name="document-tabs"></a>ドキュメント タブ  
 ドキュメント タブはタブ チャネル内に存在し、現在どのドキュメントが開いているか、およびどのドキュメントが現在選択されているか、またはアクティブなドキュメントであるかを示します。 ツール ウィンドウも、ユーザーが配置した場合、ドキュメント タブ チャネルにドッキングできます。 この場合、ツール ウィンドウではドキュメント ウィンドウと同じタブの色が使用されます。 ドキュメント ウィンドウの色と常に一致する UI を作成する場合は (テーマの更新や、新しいテーマがインストールされた場合を含む)、これらの色のトークンを参照します。  
  
 ![[ドキュメント] タブの赤線](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303 072_DocumentTabRedline")  
  
 使用するケース  
 ドキュメント タブと一致し、テーマの更新や新しいテーマの色を自動的に取得する UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
#### <a name="open-document-tabs"></a>開いているドキュメントのタブ  
 開いている各ドキュメントには、ドキュメント タブ チャネルに名前を表示するタブがあります。 ドキュメントはバックグラウンドで選択したり開いたりすることができ、タブはこれらの状態を反映します。  
  
- 選択されているタブは、現在ドキュメント ウェルに表示されているドキュメントを表します。 選択されているタブには、ドキュメント ウェルの上端にまたがって拡張するドキュメントの境界線があります。  
  
- 背景タブは、現在選択されていないドキュメント タブです。クリックすると、それらは選択されたタブになり、トークン名からすべての背景、境界線、テキストの色を取得します。  
  
  ![開いているドキュメント タブの赤線](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")  
  
  使用するケース  
  カスタム ドキュメント タブを作成する場合。  
  
  使用しないケース  
  -   一時的な (プレビュー) タブ。  
  
- シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
#### <a name="selected-tab"></a>選択されているタブ  
 **重点を置いています**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![重点を置いて選択されているタブ](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303 074_SelectedTabFocused")  
  
 **選択されているドキュメント タブ、重点を置いています**  
  
 背景  
  
 `Environment.FileTabSelectedGradientTop`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.FileTabSelectedText`  
  
 境界線  
  
 `Environment.FileTabSelectedBorder`  
  
 背景と同じ色に設定されます。  
  
 ドキュメントの境界線  
  
 `Environment.FileTabDocumentBorderBackground`  
  
 **フォーカスされていません。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされていないが選択されているタブ](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303 075_SelectedTabUnfocused")  
  
 **選択されているドキュメント タブ、フォーカスされていません。**  
  
 背景  
  
 `Environment.FileTabInactiveGradientTop`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.FileTabInactiveText`  
  
 境界線  
  
 `Environment.FileTabInactiveBorder`  
  
 背景と同じ色に設定されます。  
  
 ドキュメントの境界線  
  
 `Environment.FileTabInactiveDocumentBorderBackground`  
  
#### <a name="background-tab"></a>背景タブ  
 **既定値**  
  
 ![背景タブ](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303 076_BackgroundTab")  
  
 **背景タブ既定**  
  
 背景  
  
 `Environment.FileTabBackground`  
  
 前景 (テキスト)  
  
 `Environment.FileTabText`  
  
 境界線  
  
 `Environment.FileTabBorder`  
  
 背景と同じ色に設定されます。  
  
 **マウス ポインターを移動します。**  
  
 ![ホバー時の背景タブ](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303 077_BackgroundTabHover")  
  
 **ホバー時の背景タブ**  
  
 背景  
  
 `Environment.FileTabHotGradientTop`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.FileTabHotText`  
  
 境界線  
  
 `Environment.FileTabHotBorder`  
  
 背景と同じ色に設定されます。  
  
#### <a name="preview-tab"></a>プレビュー タブ  
 プレビュー タブは、ユーザーがソリューション エクスプローラーのツール ウィンドウで項目をクリックすると、ドキュメント タブ チャネルの右側に表示されます。 プレビュー タブはドキュメントのプレビューとして機能し、ユーザーはドキュメント タブ チャネルの左側でドキュメントを開いたままにできます。 プレビュー タブは一度に 1 つのみ開くことができます。 プレビュー タブには、開いているタブと同様に、背景と選択された状態の両方があり、アクティブな状態でフォーカスされている場合とフォーカスされていない場合があります。  
  
 ![[プレビュー] タブの赤線](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303 078_PreviewTabRedline")  
  
 使用するケース  
 一時的なプレビューを作成し、一部の要素を現在のプレビュー タブの色と一致させるすべての場所。  
  
 使用しないケース  
 -   一時的 (プレビュー) でないすべての種類のドキュメントまたはタブ。  
  
- シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
  **選択されたプレビュー タブ: フォーカス**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![フォーカスされたプレビュー タブ](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303 079_PreviewTabFocused")  
  
  **フォーカスされたプレビュー タブ**  
  
  背景  
  
  `Environment.FileTabProvisionalSelectedActive`  
  
  前景 (テキスト)  
  
  `Environment.FileTabProvisionalSelectedActiveForeground`  
  
  境界線  
  
  `Environment.FileTabProvisionalSelectedActiveBorder`  
  
  背景と同じ色に設定されます。  
  
  ドキュメントの境界線  
  
  `Environment.FileTabProvisionalSelectedActiveBorder`  
  
  **選択されたプレビュー タブ: フォーカスされていません。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![フォーカスされていないプレビュー タブ](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303 080_PreviewTabUnfocused")  
  
  **フォーカスされていない [プレビュー] タブ**  
  
  背景  
  
  `Environment.FileTabProvisionalSelectedInactive`  
  
  前景 (テキスト)  
  
  `Environment.FileTabProvisionalSelectedInactiveForeground`  
  
  境界線  
  
  `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
  ドキュメントの境界線  
  
  `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
  **背景プレビュー タブ: 既定**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![プレビューの背景タブ](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303 081_PreviewBackgroundTab")  
  
  **プレビュー タブ背景タブ**  
  
  背景  
  
  `Environment.FileTabProvisionalInactive`  
  
  前景 (テキスト)  
  
  `Environment.FileTabProvisionalInactiveForeground`  
  
  境界線  
  
  `Environment.FileTabProvisionalInactiveBorder`  
  
  背景と同じ色に設定されます。  
  
  **背景プレビュー タブ: ホバー**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせるとプレビューの背景タブ](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")  
  
  **ポインターを合わせると、プレビュー タブ背景タブ**  
  
  背景  
  
  `Environment.FileTabProvisionalHover`  
  
  前景 (テキスト)  
  
  `Environment.FileTabProvisionalHoverForeground`  
  
  境界線  
  
  `Environment.FileTabProvisionalHoverBorder`  
  
  背景と同じ色に設定されます。  
  
#### <a name="document-overflow-button"></a>ドキュメント オーバーフロー ボタン  
 ドキュメント オーバーフロー ボタンは、すべてのドキュメント タブに適した垂直スペースが現在の構成にあるかどうかに関係なく、1 つ以上のドキュメントが開いている場合に表示されます。 **CommandBarMenu** 色 (「 [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)」を参照) で制御されるドキュメント オーバーフロー ドロップダウン メニューには、表示と非表示の両方の開いているすべてのドキュメントのリストが表示され、オーバーフロー グリフは開いているすべてのドキュメントがタブ チャネルに表示されるかどうかに応じて変化します。  
  
 ![オーバーフローの赤線](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303 083_OverflowRedline")  
  
 使用するケース  
 カスタム ドキュメント オーバーフロー ボタンを作成する場合。  
  
 使用しないケース  
 -   オーバーフロー ボタンと類似していない UI。  
  
- コマンド バー オーバーフロー ボタン。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303 084_Overflow")  
  
  **ドキュメント オーバーフロー ボタン**  
  
  背景  
  
  `Environment.DocWellOverflowButtonBackground`  
  
  前景 (グリフ)  
  
  `Environment.DocWellOverflowButtonGlyph`  
  
  境界線  
  
  N/A  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせるとオーバーフロー](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303 085_OverflowHover")  
  
  **ポインターを合わせると、ドキュメント オーバーフロー ボタン**  
  
  背景  
  
  `Environment.DocWellOverflowButtonMouseOverBackground`  
  
  前景 (グリフ)  
  
  `Environment.DocWellOverflowButtonMouseOverGlyph`  
  
  境界線  
  
  `Environment.DocWellOverflowButtonMouseOverBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![押されたオーバーフロー](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303 086_OverflowPressed")  
  
  **ドキュメント オーバーフロー ボタンが押されました。**  
  
  背景  
  
  `Environment.DocWellOverflowButtonMouseDownBackground`  
  
  前景 (グリフ)  
  
  `Environment.DocWellOverflowButtonMouseDownGlyph`  
  
  境界線  
  
  `Environment.DocWellOverflowButtonMouseDownBorder`  
  
## <a name="tool-windows"></a>ツール ウィンドウ  
 Visual Studio 環境で提供されるため、ツール ウィンドウをレプリケートする必要はありません。 ただし、UI が Visual Studio 環境のこの部分と常に一貫性のある状態で表示されるように、ツール ウィンドウで使用する色を活用することができます。  
  
 ![ツール ウィンドウの赤線](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303 087_ToolWindowRedline")  
  
 使用するケース  
 ツール ウィンドウと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
### <a name="tool-window-frame"></a>ツール ウィンドウ フレーム  
 Visual Studio のツール ウィンドウはさまざまなタスクに使用され、いくつかの異なる状態の 1 つで配置できます。 ツール ウィンドウが開いている場合、ドキュメント領域の 4 辺のいずれかに割り当てることができます。 ツール ウィンドウは IDE の外部でフローティングさせることもでき、ユーザーの画面内の任意の場所に再配置できます。 フローティング ウィンドウは、常に IDE の一番上に配置されます。 最後に、ツール ウィンドウはドキュメント ウィンドウとしてドッキングし、ドキュメント ウェルのタブとして表示できます。 ドキュメント ウィンドウとしてドッキングされたツール ウィンドウは、ドキュメント ウィンドウのトークン名を使用して一部の色が付けられます。  
  
 ![ツール ウィンドウ フレームの赤線](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")  
  
 使用するケース  
 ツール ウィンドウと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
 **ドッキング**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツール ウィンドウとドッキング](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303 089_ToolWindowDocked")  
  
 背景  
  
 `Environment.ToolWindowBackground`  
  
 境界線  
  
 `Environment.ToolWindowBorder`  
  
 **フローティング: フォーカス**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされたツール ウィンドウ](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303 090_ToolWindowFocused")  
  
 背景  
  
 `Environment.ToolWindowBackground`  
  
 境界線  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 **フローティング: フォーカスされていません。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツール ウィンドウのフォーカスされていない](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303 091_ToolWindowUnfocused")  
  
 背景  
  
 `Environment.ToolWindowBackground`  
  
 境界線  
  
 `Environment.MainWindowInactiveBorder`  
  
### <a name="tool-window-title-bar"></a>ツール ウィンドウのタイトル バー  
 タイトル バーの境界線は実際の境界線ではありませんが、タイトル バーの上部にわたる太い線です。 フォーカスされていない状態のトークン名はありません。  
  
 ![ツール ウィンドウのタイトル バーの赤線](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")  
  
 使用するケース  
 ツール ウィンドウと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
 **重点を置いています**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![タイトル バーに重点を置いて](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303 093_TitleBarFocused")  
  
 **フォーカスされたタイトル バー**  
  
 背景  
  
 `Environment.TitleBarActiveGradientBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.TitleBarActiveText`  
  
 境界線  
  
 `Environment.TitleBarActiveBorder`  
  
 背景と同じ色に設定されます。  
  
 ドラッグ ハンドル  
  
 `Environment.TitleBarDragHandleActive`  
  
 **フォーカスされていません。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされていないタイトル バー](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303 094_TitleBarUnfocused")  
  
 **フォーカスされていないタイトル バー**  
  
 背景  
  
 `Environment.TitleBarInactiveGradientBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.TitleBarInactiveText`  
  
 境界線  
  
 N/A  
  
 ドラッグ ハンドル  
  
 `Environment.TitleBarDragHandle`  
  
#### <a name="title-bar-buttons"></a>タイトル バー ボタン  
 ![タイトル バー ボタンの赤線](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")  
  
 使用するケース  
 ツール ウィンドウのタイトル バーの色のトークンを使用する UI に表示されるボタン。  
  
 使用しないケース  
 -   その他の場所に表示されるボタン。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![タイトル バーのフォーカスされたボタン](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")  
  
  **重点を置いています**  
  
  背景  
  
  N/A  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonActiveGlyph`  
  
  境界線  
  
  N/A  
  
  ![タイトル バー ボタンのフォーカスされていない](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")  
  
  **フォーカスされていません。**  
  
  背景  
  
  N/A  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonInactiveGlyph`  
  
  境界線  
  
  N/A  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせるとフォーカスされたタイトル バー ボタン](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")  
  
  **重点を置いています**  
  
  背景  
  
  `Environment.ToolWindowButtonHoverActive`  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonHoverActiveGlyph`  
  
  境界線  
  
  `Environment.ToolWindowButtonHoverActiveBorder`  
  
  ![タイトル バー ボタンにポインターを合わせるとフォーカスされていない](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")  
  
  **フォーカスされていません。**  
  
  背景  
  
  `Environment.ToolWindowButtonHoverInactive`  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonHoverInactiveGlyph`  
  
  境界線  
  
  `Environment.ToolWindowButtonHoverInactiveBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![タイトル バー ボタンのフォーカスおよび押された](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")  
  
  **重点を置いています**  
  
  背景  
  
  `Environment.ToolWindowButtonDown`  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonDownActiveGlyph`  
  
  境界線  
  
  `Environment.ToolWindowButtonDownBorder`  
  
  ![フォーカスされず押されたタイトル バー ボタンをクリックして](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")  
  
  **フォーカスされていません。**  
  
  背景  
  
  `Environment.ToolWindowButtonDown`  
  
  前景 (グリフ)  
  
  `Environment.ToolWindowButtonDownInactiveGlyph`  
  
  境界線  
  
  `Environment.ToolWindowButtonDownBorder`  
  
### <a name="tool-window-tabs"></a>ツール ウィンドウ タブ  
 ![ツール ウィンドウ タブの赤線](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303 102_ToolWindowTabRedline")  
  
 使用するケース  
 ツール ウィンドウと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
 **選択されているタブ**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツール ウィンドウ タブに重点を置いて](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")  
  
 **選択された状態でフォーカスのあるツール ウィンドウ タブ**  
  
 背景  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowTabSelectedActiveText`  
  
 境界線  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 背景と同じ色に設定されます。  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされていないツール ウィンドウのタブ](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")  
  
 **選択された状態でフォーカスされていないツール ウィンドウ タブ**  
  
 背景  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowTabSelectedText`  
  
 境界線  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 背景と同じ色に設定されます。  
  
 **[背景] タブ**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツール ウィンドウの背景タブ](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")  
  
 **背景ツール ウィンドウ タブ**  
  
 背景  
  
 `Environment.ToolWindowTabGradientBegin`  
  
 グラデーション境界は、Visual Studio 2013 で同じ色の値に設定されます。  
  
 `Environment.ToolWindowTabGradientEnd`  
  
 グラデーション境界は、Visual Studio 2013 で同じ色の値に設定されます。  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowTabText`  
  
 境界線  
  
 `Environment.ToolWindowTabBorder`  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせると、ツール ウィンドウの背景タブ](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")  
  
 **ポインターを合わせると、背景ツール ウィンドウ タブ**  
  
 背景  
  
 `Environment.ToolWindowTabMouseOverBackgroundBegin`  
  
 グラデーション境界は、Visual Studio 2013 で同じ色の値に設定されます。  
  
 `Environment.ToolWindowTabMouseOverBackgroundEnd`  
  
 グラデーション境界は、Visual Studio 2013 で同じ色の値に設定されます。  
  
 前景 (テキスト)  
  
 `Environment.ToolWindowTabMouseOverText`  
  
 境界線  
  
 `Environment.ToolWindowTabMouseOverBorder`  
  
 背景と同じ色に設定されます。  
  
### <a name="auto-hide-tabs"></a>自動非表示タブ  
 ![自動&#45;非表示の赤線](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303 107_AutoHideRedline")  
  
 使用するケース  
 自動非表示ツール ウィンドウ タブと一致させる UI を作成するすべての場所。  
  
 使用しないケース  
 シェルにテーマの更新がある場合に自動的に変更しない UI。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![自動&#45; タブを非表示に](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303 108_AutoHideTab")  
  
 **既定の自動非表示タブ**  
  
 背景  
  
 `Environment.AutoHideTabBackgroundBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.AutoHideTabText`  
  
 境界線  
  
 `Environment.AutoHideTabBorder`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![自動&#45;ホバー タブを非表示に](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303 109_AutoHideTabHover")  
  
 **ポインターを合わせると、自動的に隠す タブ**  
  
 背景  
  
 `Environment.AutoHideTabMouseOverBackgroundBegin`  
  
 最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
 前景 (テキスト)  
  
 `Environment.AutoHideTabMouseOverText`  
  
 境界線  
  
 `Environment.AutoHideTabMouseOverBorder`  
  
## <a name="common-shared-controls"></a>コモン共有コントロール  
 標準の Visual Studio のコマンド バーを機能で使用する場合、スタイル設定されたシェル コントロールにアクセスでき、これらのコモン コントロールを再テンプレート化する必要はありません。 ただし、カスタム コマンド バーを作成する必要がある場合は、カスタム コントロールも構築することが必要な場合があります。 その場合は、UI が Visual Studio の他の部分と一貫性を持つように、次の各コントロールに正しいトークン名を使用してください。  
  
### <a name="search-box"></a>検索ボックス  
 可能な場合は常に、Visual Studio 環境で提供されるコモン検索コントロールを使用します。 検索ボックスの色は、入力フィールド、動作設定ボタン、ドロップダウン ボタン、ドロップダウン メニューのトークン名が格納されている **ShellColors.pkgdef** ファイルの "SearchControl" カテゴリにあります。  
  
 検索ボックスは次の複数の状態のいずれかの場合があり、一部の状態は相互に排他的です。  
  
- "フォーカスされている" または "フォーカスされていない" は、カーソルがテキスト ボックス内にあるかどうかを示します。  
  
- "アクティブ" または "非アクティブ" は、ユーザーがテキスト ボックスに検索クエリを入力したかどうかを示します。  
  
- "ホバー" は、ユーザーがマウスを使用して検索ボックスの上にマウス ポインターを置いたことを意味します (この状態は他のすべての状態よりもオーバーライドされます)。  
  
- "無効" は、現在のコンテキストに対して検索機能がオフになっていることを意味します。  
  
  ![検索ボックスの赤線](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303 110_SearchBoxRedline")  
  
  使用するケース  
  カスタム検索ボックスを設計する場合。  
  
  使用しないケース  
  -   検索ボックス以外のすべてのもの。  
  
- 検索ボックスの UI と常に一致させるわけではないすべてのもの。  
  
  **重点を置いています**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![フォーカスされた検索入力フィールド](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")  
  
  **入力フィールド**  
  
  背景  
  
  `SearchControl.FocusedBackground`  
  
  前景 (テキスト)  
  
  `SearchControl.FocusedBackground`  
  
  境界線  
  
  `SearchControl.FocusedBorder`  
  
  区切り記号  
  
  `SearchControl.FocusedDropDownSeparator`  
  
  ![フォーカスされた検索操作ボタン](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")  
  
  **アクション ボタン**  
  
  背景  
  
  なし  
  
  前景 (検索グリフ)  
  
  `SearchControl.SearchGlyph`  
  
  前景 (停止グリフ)  
  
  `SearchControl.StopGlyph`  
  
  前景 (クリア グリフ)  
  
  `SearchControl.ClearGlyph`  
  
  境界線  
  
  N/A  
  
  ![検索ドロップダウン&#45;フォーカスされたボタン ダウン](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `SearchControl.FocusedDropDownButton`  
  
  前景 (グリフ)  
  
  `SearchControl.FocusedDropDownButtonGlyph`  
  
  境界線  
  
  `SearchControl.FocusedDropDownButtonBorder`  
  
  **フォーカスされていません。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![検索入力フィールドのフォーカスされていない](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")  
  
  **アクティブな入力フィールド**  
  
  背景  
  
  `SearchControl.SearchActiveBackground`  
  
  前景 (テキスト)  
  
  `SearchControl.SearchActiveBackground`  
  
  境界線  
  
  `SearchControl.UnfocusedBorder`  
  
  区切り記号  
  
  `SearchControl.DropDownSeparator`  
  
  ![フォーカスされず非アクティブな入力フィールドを検索](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")  
  
  **非アクティブな入力フィールド**  
  
  背景  
  
  `SearchControl.Unfocused`  
  
  前景 (テキスト)  
  
  `SearchControl.Unfocused`  
  
  境界線  
  
  `SearchControl.UnfocusedBorder`  
  
  区切り記号  
  
  `SearchControl.DropDownSeparator`  
  
  ![フォーカスされていない検索操作ボタン](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")  
  
  **アクション ボタン**  
  
  背景  
  
  N/A  
  
  前景 (検索グリフ)  
  
  `SearchControl.SearchGlyph`  
  
  前景 (停止グリフ)  
  
  `SearchControl.StopGlyph`  
  
  前景 (クリア グリフ)  
  
  `SearchControl.ClearGlyph`  
  
  境界線  
  
  N/A  
  
  ![検索ドロップダウン&#45;下向きの矢印ボタンのフォーカスされていない](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `SearchControl.UnfocusedDropDownButton`  
  
  前景 (グリフ)  
  
  `SearchControl.UnfocusedDropDownButtonGlyph`  
  
  境界線  
  
  `SearchControl.UnfocusedDropDownButtonBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![検索操作ボタンが押された](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")  
  
  **アクション ボタン**  
  
  背景  
  
  `SearchControl.ActionButtonMouseDown`  
  
  前景 (グリフ)  
  
  `SearchControl.ActionButtonMouseDownGlyph`  
  
  境界線  
  
  `SearchControl.ActionButtonMouseDownBorder`  
  
  ![検索ドロップダウン&#45;下向きの矢印ボタンが押された](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  `SearchControl.MouseDownDropDownButton`  
  
  前景 (グリフ)  
  
  `SearchControl.MouseDownDropDownButtonGlyph`  
  
  境界線  
  
  `SearchControl.MouseDownDropDownButtonBorder`  
  
  **強調表示されている (テキストのみ)**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![検索入力フィールドの強調表示](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")  
  
  **テキストが強調表示の入力フィールド**  
  
  背景  
  
  `SearchControl.Selection`  
  
  前景 (テキスト)  
  
  `SearchControl.FocusedBackground`  
  
  境界線  
  
  なし  
  
  区切り記号  
  
  `SearchControl.FocusedDropDownSeparator`  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![無効にされた検索入力フィールド](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")  
  
  **入力フィールド**  
  
  背景  
  
  `SearchControl.Disabled`  
  
  前景 (テキスト)  
  
  `SearchControl.Disabled`  
  
  境界線  
  
  `SearchControl.DisabledBorder`  
  
  区切り記号  
  
  `SearchControl.DropDownSeparator`  
  
  ![検索操作ボタンが無効になっている](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")  
  
  **アクション ボタン**  
  
  背景  
  
  なし  
  
  前景 (グリフ)  
  
  `SearchControl.ActionButtonDisabledGlyph`  
  
  境界線  
  
  なし  
  
  ![検索ドロップダウン&#45;下向きの矢印ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")  
  
  **ドロップダウン ボタン**  
  
  背景  
  
  なし  
  
  前景 (グリフ)  
  
  `SearchControl.DisabledDownButtonGlyph`  
  
  境界線  
  
  なし  
  
#### <a name="search-drop-down-lists"></a>検索ドロップダウン リスト  
 検索ボックスのドロップダウン メニューは、Visual Studio の他のドロップダウン メニューより少し複雑になる可能性があります。 "提案される検索" と "検索オプション" の各セクションは、メニューに単独または一緒に表示され、それぞれに別の色が付けられます。 これらの 2 つのセクションが一緒に表示される場合は線で区切られ、ドロップダウン メニュー全体が境界線で囲まれます。  
  
 ![検索ドロップダウン&#45;ダウンの赤線](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303 124_SearchDropdownRedline")  
  
 使用するケース  
 -   カスタム検索ドロップダウン リストを作成する場合。  
  
- 正しいリスト コンポーネントの正しいトークン名。  
  
  使用しないケース  
  -   他のコンテキストで表示されるドロップダウン リスト。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定 (他の状態はありません)**  
  
  要素  
  
  トークン名: Category.color  
  
  境界線  
  
  `SearchControl.PopupBorder`  
  
  区切り記号  
  
  `SearchControl.PopupSectionHeaderSeparator`  
  
  影  
  
  `Environment.DropShadowBackground`  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![推奨される検索](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303 125_SearchSuggested")  
  
  **提案される検索**  
  
  背景  
  
  `SearchControl.PopupItemsListBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `SearchControl.PopupItemText`  
  
  ![検索チェック ボックスをオン](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303 126_SearchCheckbox")  
  
  **検索オプション (チェック ボックス)**  
  
  ![検索オプション](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303 127_SearchOptions")  
  
  **検索オプション (リンク)**  
  
  背景  
  
  `SearchControl.PopupSectionBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (チェック ボックス テキスト)  
  
  `SearchControl.PopupCheckboxText`  
  
  前景 (リンク テキスト)  
  
  `SearchControl.PopupButtonText`  
  
  ヘッダーの背景  
  
  `SearchControl.PopupSectionHeaderGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (ヘッダー テキスト)  
  
  `SearchControl.PopupSectionHeaderText`  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ポインターを合わせると推奨される検索](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303 128_SearchSuggestedHover")  
  
  **提案される検索**  
  
  背景  
  
  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (テキスト)  
  
  `SearchControl.PopupMouseOverItemText`  
  
  境界線  
  
  `SearchControl.PopupControlMouseOverBorder`  
  
  ![ポイント時の検索 チェック ボックス](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303 129_SearchCheckboxHover")  
  
  **提案される検索 (チェック ボックス)**  
  
  ![ホバー時オプションを検索](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303 130_SearchOptionsHover")  
  
  **検索オプション**  
  
  背景  
  
  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (チェック ボックス テキスト)  
  
  `SearchControl.PopupCheckboxMouseDownText`  
  
  前景 (リンク テキスト)  
  
  `SearchControl.PopupButtonMouseDownText`  
  
  境界線  
  
  `SearchControl.PopupControlMouseOverBorder`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![押された推奨される検索](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")  
  
  **提案される検索 (チェック ボックス)**  
  
  ![押されたオプションの検索](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303 132_SearchOptionsPressed")  
  
  **検索オプション**  
  
  チェック ボックスの背景  
  
  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (チェック ボックス テキスト)  
  
  `SearchControl.PopupCheckboxMouseDownText`  
  
  リンクの背景  
  
  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`  
  
  最新のテーマの UI では使用されませんが、この背景にはグラデーション境界と値があります。  
  
  前景 (リンク テキスト)  
  
  `SearchControl.PopupButtonMouseDownText`  
  
### <a name="hyperlink"></a>ハイパーリンク  
 ハイパーリンクは、前景と背景の組み合わせがない 1 つのコントロールです。 すべての場合において、ハイパーリンクの前景色を使用します。この色は濃色、灰色、白の背景で正しく表示されます。 ハイパーリンク コントロールの色トークンを使用しない場合、"押されている" ことを示す既定のシステム カラー (明るい赤) が表示されます。 これは、コントロールで適切な環境の色トークンが使用されていないことを示します。  
  
 ![ハイパーリンクの赤線](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303 133_HyperlinkRedline")  
  
 使用するケース  
 カスタム ハイパーリンクを作成する必要がある場合。  
  
 使用しないケース  
 ハイパーリンク以外のすべてのもの。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ハイパーリンクの既定値](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303 134_Hyperlink")  
  
 前景 (テキスト)  
  
 `Environment.PanelHyperlink`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせるとハイパーリンク](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303 135_HyperlinkHover")  
  
 前景 (テキスト)  
  
 `Environment.PanelHyperlinkHover`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![押されたハイパーリンク](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303 136_HyperlinkPressed")  
  
 前景 (テキスト)  
  
 `Environment.PanelHyperlinkPressed`  
  
 **無効**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![無効にされたハイパーリンク](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303 137_HyperlinkDisabled")  
  
 前景 (テキスト)  
  
 `Environment.PanelHyperlinkDisabled`  
  
### <a name="infobar"></a>情報バー  
 情報バーは該当するコンテキストの詳細を提供するために使用され、常にドキュメント ウィンドウまたはツール ウィンドウの上部に表示されます。  
  
 ![情報バーの赤線](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303 138_InfobarRedline")  
  
 使用するケース  
 カスタム情報バーを作成する場合。  
  
 使用しないケース  
 情報バーに類似していない UI 要素。  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![情報バー](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303 139_Infobar")  
  
 **情報バー**  
  
 背景  
  
 `Environment.InfoBackground`  
  
 前景 (テキスト)  
  
 `Environment.InfoText`  
  
 境界線  
  
 `Environment.ToolWindowBorder`  
  
### <a name="scroll-bar"></a>スクロール バー  
 スクロール バーは Visual Studio 環境によってスタイルが設定され、テーマを指定する必要はありません。 ただし、常に、UI が Visual Studio 環境のこの部分と一貫性が表示されるように、スクロール バーで使用する色を活用することをことがあります。  
  
 ![スクロール バーの赤線](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303 140_ScrollbarRedline")  
  
 使用するケース  
 Visual Studio のスクロール バーと一致させる UI を作成する場合。  
  
 使用しないケース  
 スクロール バーの UI と常に一致させるわけではないすべてのもの。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![スクロール バー](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303 141_Scrollbar")  
  
 **スクロール バー**  
  
 スクロール バー  
  
 `Environment.ScrollBarBackground`  
  
 前景 (つまみ)  
  
 `Environment.ScrollBarThumbBackground`  
  
 ![スクロール バーの矢印](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303 142_ScrollbarArrow")  
  
 **スクロール バーの矢印**  
  
 背景  
  
 `Environment.ScrollBarArrowBackground`  
  
 スクロール バーと同じ色に設定されます。  
  
 前景 (グリフ)  
  
 `Environment.ScrollBarArrowGlyph`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせるとスクロール バー](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303 143_ScrollbarHover")  
  
 **スクロール バー**  
  
 スクロール バー  
  
 `Environment.ScrollBarBackground`  
  
 前景 (つまみ)  
  
 `Environment.ScrollBarThumbMouseOverBackground`  
  
 ![スクロール バーの矢印のホバー](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303 144_ScrollbarArrowHover")  
  
 **スクロール バーの矢印**  
  
 背景  
  
 `Environment.ScrollBarArrowMouseOverBackground`  
  
 スクロール バーと同じ色に設定されます。  
  
 前景 (グリフ)  
  
 `Environment.ScrollBarArrowGlyphMouseOver`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![スクロール バーが押された](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303 145_ScrollbarPressed")  
  
 **スクロール バー**  
  
 スクロール バー  
  
 `Environment.ScrollBarBackground`  
  
 前景 (つまみ)  
  
 `Environment.ScrollBarThumbPressedBackground`  
  
 ![スクロール バーの矢印が押された](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")  
  
 **スクロール バーの矢印**  
  
 背景  
  
 `Environment.ScrollBarArrowPressedBackground`  
  
 スクロール バーと同じ色に設定されます。  
  
 前景 (グリフ)  
  
 `Environment.ScrollBarArrowGlyphPressed`  
  
###  <a name="BKMK_TreeView"></a> ツリー ビュー  
 ソリューション エクスプローラー、サーバー エクスプローラー、クラス ビューなど、いくつかのツール ウィンドウでは、色が TreeView カテゴリの色の名前によって制御される階層組織スキームが実装されます。 ツリー ビューのすべての項目に背景色とテキスト色があります。 入れ子にされた子要素がある項目には、項目が展開されているか折りたたまれているかを示すグリフもあります。  
  
 ![ツリー ビューの赤線](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303 147_TreeViewRedline")  
  
 使用するケース  
 階層組織ビューを実装する必要があるすべての場所。  
  
 使用しないケース  
 -   ツリー ビューに類似していないすべてのもの。  
  
- 指定以外の背景と前景の組み合わせ。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ツリー ビュー](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303 148_TreeView")  
  
  背景  
  
  `TreeView.Background`  
  
  前景 (テキスト)  
  
  `TreeView.Background`  
  
  前景 (グリフ)  
  
  `TreeView.Glyph`  
  
  境界線  
  
  なし  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ツリー ビューのホバー](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303 149_TreeViewHover")  
  
  背景  
  
  `TreeView.Background`  
  
  前景 (テキスト)  
  
  `TreeView.Background`  
  
  前景 (グリフ)  
  
  `TreeView.GlyphMouseOver`  
  
  境界線  
  
  なし  
  
  **上にドラッグします。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ドラッグされたツリー ビュー](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303 150_TreeViewDragOver")  
  
  背景  
  
  `TreeView.DragOverItem`  
  
  前景 (テキスト)  
  
  `TreeView.DragOverItem`  
  
  前景 (グリフ)  
  
  `TreeView.DragOverItemGlyph`  
  
  境界線  
  
  なし  
  
  **選択されています。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ツリー ビューに重点を置いた](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303 151_TreeViewFocused")  
  
  **重点を置いています**  
  
  背景  
  
  `TreeView.SelectedItemActive`  
  
  前景 (テキスト)  
  
  `TreeView.SelectedItemActive`  
  
  前景 (グリフ)  
  
  `TreeView.SelectedItemActiveGlyph`  
  
  境界線  
  
  `TreeView.FocusVisualBorder`  
  
  ![ツリー ビューがフォーカスされていない](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303 152_TreeViewUnfocused")  
  
  **フォーカスされていません。**  
  
  背景  
  
  `TreeView.SelectedItemInactive`  
  
  前景 (テキスト)  
  
  `TreeView.SelectedItemInactive`  
  
  前景 (グリフ)  
  
  `TreeView.SelectedItemInactiveGlyph`  
  
  境界線  
  
  なし  
  
  **マウスの選択**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![ツリー ビュー ポイントしたときに重点を置いて](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")  
  
  **重点を置いています**  
  
  背景  
  
  `TreeView.SelectedItemActive`  
  
  前景 (テキスト)  
  
  `TreeView.SelectedItemActive`  
  
  前景 (グリフ)  
  
  `TreeView.SelectedItemActiveGlyphMouseOver`  
  
  境界線  
  
  なし`TreeView.FocusVisualBorder`  
  
  ![ツリー ビュー フォーカスされていないポインターを合わせると](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")  
  
  **フォーカスされていません。**  
  
  背景  
  
  `TreeView.SelectedItemInactive`  
  
  前景 (テキスト)  
  
  `TreeView.SelectedItemInactive`  
  
  前景 (グリフ)  
  
  `TreeView.SelectedItemActiveGlyphMouseOver`  
  
  境界線  
  
  なし  
  
### <a name="button-controls"></a>ボタン コントロール  
 ![ボタン コントロールの赤線](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303 155_ButtonControlRedline")  
  
 使用するケース  
 Visual Studio のテーマ (淡色、濃色、青、またはシステムのハイコントラスト テーマ) と統合するドキュメント ウェル内のボタン。  
  
 使用しないケース  
 Visual Studio のテーマの一部でないカスタム背景に対して表示されるボタン。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ボタン](../../extensibility/ux-guidelines/media/0303-156-button.png "0303 156_Button")  
  
 ボタン  
  
 `CommonControls.Button`  
  
 ボタンの境界線  
  
 `CommonControls.ButtonBorder`  
  
 **無効**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303 157_ButtonDisabled")  
  
 ボタン  
  
 `CommonControls.ButtonDisabled`  
  
 ボタンの境界線  
  
 `CommonControls.ButtonBorderDisabled`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ホバー時ボタン](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303 158_ButtonHover")  
  
 ボタン  
  
 `CommonControls.ButtonHover`  
  
 ボタンの境界線  
  
 `CommonControls.ButtonBorderHover`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ボタンが押された](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303 159_ButtonPressed")  
  
 ボタン  
  
 `CommonControls.ButtonPressed`  
  
 ボタンの境界線  
  
 `CommonControls.ButtonBorderPressed`  
  
 **重点を置いています**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされたボタン](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303 160_ButtonFocused")  
  
 ボタン  
  
 `CommonControls.ButtonFocused`  
  
 ボタンの境界線  
  
 `CommonControls.ButtonBorderFocused`  
  
### <a name="check-box-controls"></a>チェック ボックス コントロール  
 ![チェック ボックスの赤線](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303 161_CheckboxRedline")  
  
 使用するケース  
 ドキュメント ウェル内に含まれるチェック ボックス コントロール。  
  
 使用しないケース  
 チェック ボックス コントロールでない UI。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![チェック ボックスをオン](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303 162_Checkbox")  
  
 背景  
  
 `CommonControls.CheckBoxBackground`  
  
 境界線  
  
 `CommonControls.CheckBoxBorder`  
  
 テキスト  
  
 `CommonControls.CheckBoxText`  
  
 グリフ  
  
 `CommonControls.CheckBoxGlyph`  
  
 **無効**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![チェック ボックスを無効になっている](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303 163_CheckboxDisabled")  
  
 背景  
  
 `CommonControls.CheckBoxBackgroundDisabled`  
  
 境界線  
  
 `CommonControls.CheckBoxBorderDisabled`  
  
 テキスト  
  
 `CommonControls.CheckBoxTextDisabled`  
  
 グリフ  
  
 `CommonControls.CheckBoxGlyphDisabled`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![チェック ボックスをホバー](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303 164_CheckboxHover")  
  
 背景  
  
 `CommonControls.CheckBoxBackgroundHover`  
  
 境界線  
  
 `CommonControls.CheckBoxBorderHover`  
  
 テキスト  
  
 `CommonControls.CheckBoxTextHover`  
  
 グリフ  
  
 `CommonControls.CheckBoxGlyphHover`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![押されたチェック ボックス](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303 165_CheckboxPressed")  
  
 背景  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 境界線  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 テキスト  
  
 `CommonControls.CheckBoxTextPressed`  
  
 グリフ  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
 **重点を置いています**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![フォーカスされたチェック ボックス](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303 166_CheckboxFocused")  
  
 背景  
  
 `CommonControls.CheckBoxBackgroundFocused`  
  
 境界線  
  
 `CommonControls.CheckBoxBorderFocused`  
  
 テキスト  
  
 `CommonControls.CheckBoxTextFocused`  
  
 グリフ  
  
 `CommonControls.CheckBoxGlyphFocused`  
  
### <a name="drop-boxcombo-box-controls"></a>ドロップ ボックス/コンボ ボックス コントロール  
 ![Drop&#45;ダウン&#47;コンボ ボックスの赤線](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")  
  
 使用するケース  
 ドキュメント ウェルに含まれるドロップダウンとコンボ ボックス。  
  
 使用しないケース  
 -   ドロップダウンまたはコンボ ボックスでない UI。  
  
- コマンド バーの [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) または [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) 。  
  
  **既定値**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;コンボ ボックス](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303 168_DropDownComboBox")  
  
  背景  
  
  `CommonControls.ComboBoxBackground`  
  
  境界線  
  
  `CommonControls.ComboBoxBorder`  
  
  テキスト  
  
  `CommonControls.ComboBoxText`  
  
  区切り記号  
  
  `CommonControls.ComboBoxSeparator`  
  
  グリフ  
  
  `CommonControls.ComboBoxGlyph`  
  
  グリフの背景  
  
  `CommonControls.ComboBoxGlyphBackground`  
  
  **無効**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;無効にされたコンボ ボックス](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")  
  
  背景  
  
  `CommonControls.ComboBoxBackgroundDisabled`  
  
  境界線  
  
  `CommonControls.ComboBoxBorderDisabled`  
  
  テキスト  
  
  `CommonControls.ComboBoxTextDisabled`  
  
  区切り記号  
  
  `CommonControls.ComboBoxSeparatorDisabled`  
  
  グリフ  
  
  `CommonControls.ComboBoxGlyphDisabled`  
  
  グリフの背景  
  
  `CommonControls.ComboBoxGlyphBackgroundDisabled`  
  
  **マウス ポインターを移動します。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;ポインターを合わせると、コンボ ボックス](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")  
  
  背景  
  
  `CommonControls.ComboBoxBackgroundHover`  
  
  境界線  
  
  `CommonControls.ComboBoxBorderHover`  
  
  テキスト  
  
  `CommonControls.ComboBoxTextHover`  
  
  区切り記号  
  
  `CommonControls.ComboBoxSeparatorHover`  
  
  グリフ  
  
  `CommonControls.ComboBoxGlyphHover`  
  
  グリフの背景  
  
  `CommonControls.ComboBoxGlyphBackgroundHover`  
  
  **押されました。**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;押されたコンボ ボックス](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")  
  
  背景  
  
  `CommonControls.ComboBoxBackgroundPressed`  
  
  境界線  
  
  `CommonControls.ComboBoxBorderPressed`  
  
  テキスト  
  
  `CommonControls.ComboBoxTextPressed`  
  
  区切り記号  
  
  `CommonControls.ComboBoxSeparatorPressed`  
  
  グリフ  
  
  `CommonControls.ComboBoxGlyphPressed`  
  
  グリフの背景  
  
  `CommonControls.ComboBoxGlyphBackgroundPressed`  
  
  **重点を置いています**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;フォーカスされたコンボ ボックス](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")  
  
  背景  
  
  `CommonControls.ComboBoxBackgroundFocused`  
  
  境界線  
  
  `CommonControls.ComboBoxBorderFocused`  
  
  テキスト  
  
  `CommonControls.ComboBoxTextFocused`  
  
  区切り記号  
  
  `CommonControls.ComboBoxSeparatorFocused`  
  
  グリフ  
  
  `CommonControls.ComboBoxGlyphFocused`  
  
  グリフの背景  
  
  `CommonControls.ComboBoxGlyphBackgroundFocused`  
  
  **テキスト入力の選択**  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  ![Drop&#45;ダウン&#47;コンボ ボックスのテキスト入力](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")  
  
  ハイライト  
  
  `CommonControls.ComboBoxTextInputSelection`  
  
  **押されている-リスト項目ビュー**  
  
  ![Drop&#45;ダウン&#47;コンボ ボックスのリスト ビュー](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")  
  
  背景  
  
  `CommonControls.ComboBoxListBackground`  
  
  `CommonControls.ComboBoxListBackgroundHover`  
  
  `CommonControls.ComboBoxListItemBackgroundPressed`  
  
  `CommonControls.ComboBoxListItemBackgroundFocused`  
  
  境界線  
  
  `CommonControls.ComboBoxListBorder`  
  
  `CommonControls.ComboBoxListBorderHover`  
  
  `CommonControls.ComboBoxListBorderPressed`  
  
  `CommonControls.ComboBoxListBorderFocused`  
  
  項目のテキスト  
  
  `CommonControls.ComboBoxListItemText`  
  
  `CommonControls.ComboBoxListItemTextHover`  
  
  `CommonControls.ComboBoxListItemTextPressed`  
  
  `CommonControls.ComboBoxListItemTextFocused`  
  
  背景の影  
  
  `CommonControls.ComboBoxListBackgroundShadow`  
  
### <a name="tabular-data-grid-controls"></a>表形式のデータ (グリッド) コントロール  
 表形式のデータ コントロール (グリッド コントロールとも呼ばれる) は、複数列の大量のデータを表示するために使用する Visual Studio のコモン コントロールです。 標準の表形式のデータ コントロールは、[エラー一覧] ツール ウィンドウ、IntelliTrace レポート、メモリ ヒープ ビューなど、Visual Studio 内の複数の場所にあります。 提供される標準の表形式のデータ コントロールを常に使用します。 まれに、標準の表形式のデータ コントロールにアクセスできないことがあります。 このような場合は、次のトークン名を使用して、UI が Visual Studio の他の表形式のデータ コントロールと一貫性を保つようにします。  
  
 ![表形式のデータ&#40;グリッド コントロール&#41;の赤線](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")  
  
 使用するケース  
 表形式コントロールまたはグリッド コントロール。  
  
 使用しないケース  
 表形式またはグリッド コントロール以外の UI。  
  
#### <a name="column-headers"></a>列ヘッダー  
 列ヘッダーは、背景、境界線、タイトル テキスト、およびグリッドがその列で並べ替えられたときに通常使用されるオプションのグリフで構成されます。  
  
 状態  
  
 要素  
  
 トークン名: Category.color  
  
 既定値  
  
 背景  
  
 `Header.Default`  
  
 前景 (テキスト)  
  
 `Environment.CommandBarTextActive`  
  
 前景 (グリフ)  
  
 `Header.Glyph`  
  
 境界線  
  
 `Header.SeparatorLine`  
  
 ホバー  
  
 背景  
  
 `Header.MouseOver`  
  
 前景 (テキスト)  
  
 `Environment.CommandBarTextHover`  
  
 前景 (グリフ)  
  
 `Header.MouseOverGlyph`  
  
 境界線  
  
 `Header.SeparatorLine`  
  
 押されている  
  
 背景  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 前景 (テキスト)  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 前景 (グリフ)  
  
 `CommonControls.CheckBoxTextPressed`  
  
 境界線  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
#### <a name="list-view-items"></a>リスト ビュー項目  
 リスト ビュー項目は、背景とコンテンツで構成されます。 コンテンツは、テキスト、アイコン、またはその両方の場合があります。  
  
 状態  
  
 要素  
  
 トークン名: Category.color  
  
 既定値  
  
 背景  
  
 透明  
  
 前景 (テキスト)  
  
 `Environment.CommandBarTextActive`  
  
 境界線  
  
 なし  
  
 選択済み (アクティブ)  
  
 背景  
  
 `TreeView.SelectedItemActive`  
  
 前景 (テキスト)  
  
 `TreeView.SelectedItemActiveText`  
  
 境界線  
  
 なし  
  
 選択済み (非アクティブ)  
  
 背景  
  
 `TreeView.SelectedItemInactive`  
  
 前景 (テキスト)  
  
 `TreeView.SelectedItemInactiveText`  
  
 境界線  
  
 なし  
  
## <a name="manifest-designer"></a>マニフェスト デザイナー  
 マニフェスト デザイナーは、Windows 8 および Windows Phone 8 プロジェクトのマニフェスト ファイルを編集しやすくするための手段として設計されています。 使用可能な共有フレームワークはありませんが、向き/ナビゲーション タブと全体的な構造のデザイン レイアウトおよび色を一致させることが適切な場合があります。 レイアウトの詳細については、「 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)」を参照してください。  
  
 ![マニフェスト デザイナーの赤線](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303 175_ManifestDesignerRedline")  
  
 使用するケース  
 -   マニフェスト デザイナーと同様のデザイナー。  
  
- ドキュメント ウェル内のエディターの上部でコモン タブ コントロールを使用する代わり。  
  
  使用しないケース  
  -   7 つ以上のタブがある場合。  
  
- マニフェスト デザイナーのように構造化されていないすべての UI。  
  
  状態  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  既定 (選択済み)  
  
  タブ  
  
  背景  
  
  `ManifestDesigner.TabActive`  
  
  境界線  
  
  なし  
  
  [説明ペイン]  
  
  背景  
  
  `ManifestDesigner.DescriptionPane`  
  
  コンテンツ ページ  
  
  背景  
  
  `ManifestDesigner.Background`  
  
  ダイアログ ヘルパー テキスト  
  
  `ManifestDesigner.WatermarkText`  
  
  このトークン名はその機能に一致しません。  
  
  選択されていない  
  
  タブ  
  
  背景  
  
  `ManifestDesigner.Tab.Inactive`  
  
  ホバー  
  
  タブ  
  
  背景  
  
  `ManifestDesigner.Tab.Mouseover`  
  
## <a name="tagging"></a>タグ付け  
 Visual Studio は、タグ付けをサポートしています。タグ付けにより、ユーザーは追跡のために検索可能なキーワードを宣言できます。 たとえば、プロジェクト マネージャーと開発者は、Team Foundation Server (TFS) を使用して作業項目にタグを付けることができます。 次の表に、タグ自体と、ホバー時および選択済み状態で表示される "アイコンを閉じる" グリフの両方の色の名前を示します。  
  
 ![タグ付けの赤線](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303 176_TaggingRedline")  
  
 使用するケース  
 タグ付けをサポートする UI。  
  
 使用しないケース  
 他の種類の UI。  
  
### <a name="tag"></a>タグ  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![タグ](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303 177_Tag")  
  
 **既定値**  
  
 背景  
  
 `Tag.Background`  
  
 前景 (テキスト)  
  
 `Tag.Background`  
  
 ![ポインターを合わせるとタグ付け](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303 178_TagHover")  
  
 **マウス ポインターを移動します。**  
  
 背景  
  
 `Tag.HoverBackground`  
  
 前景 (テキスト)  
  
 `Tag.HoverBackgroundText`  
  
 ![押されたタグ](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303 179_TagPressed")  
  
 **押されました。**  
  
 背景  
  
 `Tag.PressedBackground`  
  
 前景 (テキスト)  
  
 `Tag.PressedBackgroundText`  
  
 ![選択されたタグ](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303 180_TagSelected")  
  
 **選択されています。**  
  
 背景  
  
 `Tag.SelectedBackground`  
  
 前景 (テキスト)  
  
 `Tag.SelectedBackgroundText`  
  
### <a name="glyph-close-icon"></a>グリフ (アイコンを閉じる)  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![タグ&#40;グリフ&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303 181_TagGlyph")  
  
 **既定 (既定タグ)**  
  
 背景  
  
 N/A  
  
 前景 (グリフ)  
  
 `Tag.TagHoverGlyph`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![タグ&#40;グリフ&#41;ホバー](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303 182_TagGlyphHover")  
  
 **ホバー (既定タグ)**  
  
 背景  
  
 `Tag.TagHoverGlyphHoverBackground`  
  
 前景 (グリフ)  
  
 `Tag.TagHoverGlyphHover`  
  
 境界線  
  
 `Tag.TagHoverGlyphHoverBorder`  
  
 **押されました。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![タグ&#40;グリフ&#41;押された](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303 183_TagGlyphPressed")  
  
 **(既定タグ) を押す**  
  
 背景  
  
 `Tag.TagHoverGlyphPressedBackground`  
  
 前景 (グリフ)  
  
 `Tag.TagHoverGlyphPressed`  
  
 境界線  
  
 `Tag.TagHoverGlyphPressedBorder`  
  
 **タグ/グリフが選択されている既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![選択されたタグ](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303 184_TagSelected")  
  
 **既定 (選択されたタグ)**  
  
 背景  
  
 N/A  
  
 前景 (グリフ)  
  
 `Tag.TagSelectedGlyph`  
  
 **タグの選択/グリフ ホバー**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ポインターを合わせると選択されたタグ](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303 185_TagSelectedHover")  
  
 **ホバー (選択されたタグ)**  
  
 背景  
  
 `Tag.TagSelectedGlyphHoverBackground`  
  
 前景 (グリフ)  
  
 `Tag.TagSelectedGlyphHover`  
  
 境界線  
  
 `Tag.TagSelectedGlyphHoverBorder`  
  
 **タグを選択/押されているグリフ**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![選択されたタグ押された](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303 186_TagSelectedPressed")  
  
 **押された (タグの選択)**  
  
 背景  
  
 `Tag.TagSelectedGlyphPressedBackground`  
  
 前景 (グリフ)  
  
 `Tag.TagSelectedGlyphPressed`  
  
 境界線  
  
 `Tag.TagSelectedGlyphPressedBorder`  
  
## <a name="shell"></a>Shell  
  
### <a name="background"></a>背景  
 環境の背景色は、2 つのレイヤーで構成されます。 下部レイヤーは、IDE 全体にわたる単色です。 上部レイヤーは、コマンド シェルフの下、および IDE の左端と右端のツール ウィンドウ自動非表示チャネルの間に収まります。 Visual Studio 2013 の時点で、上部と下部の背景レイヤーは、ライト テーマとダーク テーマで同じ色に設定されます。  
  
 ![バック グラウンドのシェルの赤線](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303 187_ShellBackgroundRedline")  
  
 使用するケース  
 Visual Studio 環境の背景を一致させる場所。  
  
 使用しないケース  
 -   背景サーフェイスではない場所の塗りつぶし。  
  
- 前景要素を配置する背景。  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  下部レイヤー  
  
  背景  
  
  `Environment.EnvironmentBackground`  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  上部レイヤー  
  
  背景  
  
  *グラデーションは、Visual Studio 2013 のライトとダーク テーマで同じ色の値に設定を停止します。*  
  
  `Environment.EnvironmentBackgroundGradientBegin`  
  
  `Environment.EnvironmentBackgroundGradientEnd`  
  
  `Environment.EnvironmentBackgroundGradientMiddle1`  
  
  `Environment.EnvironmentBackgroundGradientMiddle2`  
  
### <a name="command-shelf"></a>コマンド シェルフ  
 コマンド シェルフの背景には 2 セットのトークン名が使用されます。1 セットはメニュー バーが位置する場所、もう 1 セットはコマンド バーが位置する場所に使用されます。 個々のコマンド バー グループには、独自の背景色値があります。これについては「コマンド バー」セクションで詳しく説明しています。 メニュー バーとコマンド バーのテキストについては、それぞれメニューとコマンド バーのセクションで説明しています。  
  
 ![コマンド シェルフの赤線](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303 188_CommandShelfRedline")  
  
 使用するケース  
 -   メニューまたはツール バーを配置する領域。  
  
- 正しい背景/でしょうか。 前景トークン名の組み合わせ。  
  
  使用しないケース  
  コマンド シェルフに類似していない領域。  
  
  コンポーネント  
  
  要素  
  
  トークン名: Category.color  
  
  メニュー バー  
  
  背景  
  
  *グラデーションは、Visual Studio 2013 のライトとダーク テーマで同じ色の値に設定を停止します。*  
  
  `Environment.CommandShelfHighlightGradientBegin`  
  
  `Environment.CommandShelfHighlightGradientMiddle`  
  
  `Environment.CommandShelfHighlightGradientEnd`  
  
  コマンド バー  
  
  背景  
  
  *グラデーションは、Visual Studio 2013 のライトとダーク テーマで同じ色の値に設定を停止します。*  
  
  `Environment.CommandShelfBackgroundGradientBegin`  
  
  `Environment.CommandShelfBackgroundGradientMiddle`  
  
  `Environment.CommandShelfBackgroundGradientEnd`  
  
## <a name="toolbox"></a>ツールボックス  
 ツールボックスは、Visual Studio で最も頻繁に使用されるコモン ツール ウィンドウの 1 つです。 これは基本的に、特別なテーマとスタイルが適用されたツリー コントロールです。  
  
 ![ツールボックスの赤線](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303 189_ToolboxRedline")  
  
 使用するケース  
 常にシェル ツールボックスと一貫性を維持するツール ウィンドウを設計する場合。  
  
 使用しないケース  
 ツールボックス UI と類似していないすべてのもの、またはシェル ツールボックスの色を変更した場合に UI に問題が発生するかどうか不明な場合。  
  
 **既定値**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツールボックスの親ノード](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303 190_ToolboxParentNode")  
  
 **親ノード**  
  
 ![ツールボックスの子ノード](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303 191_ToolboxChildNode")  
  
 **子ノード**  
  
 背景  
  
 `Environment.ToolboxContent`  
  
 見出し  
  
 `Environment.ToolWindowBackground`  
  
 個々の項目、または利用可能なコントロールがない場合はウィンドウ全体  
  
 境界線  
  
 なし  
  
 前景 (グリフ)  
  
 `Environment.ToolboxContent`  
  
 前景 (テキスト)  
  
 `Environment.ToolboxContent`  
  
 **マウス ポインターを移動します。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツールボックスの子ノードのホバー](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")  
  
 **子ノードにホバー時のツールボックス**  
  
 背景  
  
 `Environment.ToolboxContentMouseOver`  
  
 個々の項目のみ  
  
 境界線  
  
 なし  
  
 前景 (テキスト)  
  
 `Environment.ToolboxContentMouseOver`  
  
 個々の項目のみ  
  
 **選択されています。**  
  
 コンポーネント  
  
 要素  
  
 トークン名: Category.color  
  
 ![ツールボックスの親ノードに重点を置いて](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")  
  
 **フォーカスされた親ノード**  
  
 ![ツールボックスの子ノードに重点を置いて](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")  
  
 **フォーカスされた子ノード**  
  
 背景  
  
 `TreeView.SelectedItemActive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 境界線  
  
 `TreeView.FocusVisualBorder`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 前景 (グリフ)  
  
 `TreeView.SelectedItemActive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 前景 (テキスト)  
  
 `TreeView.SelectedItemActive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 ![フォーカスされていないツールボックスの親ノード](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")  
  
 **フォーカスされていない親ノード**  
  
 ![フォーカスされていないツールボックスの子ノード](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")  
  
 **フォーカスされていない子ノード**  
  
 背景  
  
 `TreeView.SelectedItemInactive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 境界線  
  
 なし  
  
 前景 (グリフ)  
  
 `TreeView.SelectedItemInactive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから  
  
 前景 (テキスト)  
  
 `TreeView.SelectedItemInactive`  
  
 [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから

