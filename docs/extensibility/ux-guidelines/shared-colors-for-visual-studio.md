---
title: Visual Studio の色の共有 |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 195ec36affc9ede9efc61ead2cdede8233ebb65a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54928907"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio の共有の色
共通の Visual Studio シェル要素を使用する UI を設計するか、インターフェイス要素に同様の機能と一致するかは、パッケージ定義ファイルで既存のトークン名を使用して、選択し、色を割り当てます。 これにより、UI が Visual Studio 環境全体で一貫性を保ち、テーマが追加された場合や更新された場合に自動的に更新されるようになります。  

この記事では、類似の UI を構築する際に参照できる一般的な UI 要素と UI 要素で使用されるトークン名について説明します。 これらの色のトークンにアクセスする方法の詳細については、「 [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)」を参照してください。  

トークン名は次のように正しく使用してください。  

-   **色自体ではなく、機能に基づいてトークン名を使用します。** 一般的な共有色は、特定のインターフェイス要素と関連付けられ、同一または類似した機能に対してのみ使用されることを想定しています。 たとえば、押されているコンボ ボックスの色を、単にその色が好きという理由で進行状況を示す回転アニメーションに再利用しないでください。 コンボ ボックスとアニメーションの機能が異なると、アニメーション要素にとって適切な色を使用、色は、コンボ ボックスの変更に関連付けられている場合、できなく可能性があります。 色を一貫して使用すると、ユーザーの理解を助け、混乱を避けるために役立ちます。  

-   **適切な組み合わせでは、背景色とテキストの色を使用します。** テキストと共に使用することが想定された背景色には、テキストの色が関連付けられています。 その背景に指定されている色以外のテキストの色を使用しないでください。 関連付けられているテキストの色がない場合は、テキストを表示するが、画面の背景色を使用しないでください。 他のテキストと背景色の組み合わせは、読み取り不可能なインターフェイスがあります。  

-   **その場所に適したコントロールの色を使用します。** 特定の状態の Visual Studio の一部のコントロールは、個別の境界線と背景色がありません。 代わりに、それらのコントロールにはその背後のサーフェイスから色が適用されます。 コントロールを配置する場所に適したトークン名を常に使用してください。  

> [!IMPORTANT]
> 「スタート ページ」や"Cider"カテゴリにあるトークンを使用しないでください。  

## <a name="common-shared-controls"></a>コモン共有コントロール

機能で標準の Visual Studio のコマンド バーを使用すると、スタイル設定されたシェル コントロールへのアクセスが必要があります。 これらのコモン コントロールを再テンプレート化することはできません。 ただし、カスタム コマンド バーを作成する必要がある場合は、カスタム コントロールも構築することが必要な場合があります。 その場合は、UI が Visual Studio の他の部分と一貫性を持つように、次の各コントロールに正しいトークン名を使用してください。

### <a name="button-controls"></a>ボタン コントロール

![ボタン コントロールの赤線](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303 155_ButtonControlRedline")

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for Visual Studio のテーマ (ライト、濃色、青、またはシステムのハイコントラスト テーマ) と統合するドキュメント ウェル内のボタン。 | ... for Visual Studio のテーマの一部ではないカスタム背景に対して表示されるボタン。 |

**標準的な状態のボタンをクリックします。**

![標準ボタン](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />標準のボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| ボタン | `CommonControls.Button` |
| ボタンの境界線 | `CommonControls.ButtonBorder` |

**Button: 既定の状態**

![既定のボタン](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />既定のボタン

| 要素 | トークン名:Category.color | 
| --- | --- | 
| ボタン | `CommonControls.ButtonDefault` |
| ボタンの境界線 | `CommonControls.ButtonBorderDefault` |

**無効な状態のボタンをクリックします。**  

![無効にされたボタン](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />無効にされたボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| ボタン | `CommonControls.ButtonDisabled` |
| ボタンの境界線 | `CommonControls.ButtonBorderDisabled` |

**Button: ホバー状態**  

![ホバー時ボタン](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />ホバー時のボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| ボタン | `CommonControls.ButtonHover` |
| ボタンの境界線 | `CommonControls.ButtonBorderHover` |

**押された状態のボタンをクリックします。**  

![押されたボタン](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />押されたボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| ボタン | `CommonControls.ButtonPressed` |
| ボタンの境界線 | `CommonControls.ButtonBorderPressed` |

**フォーカスされた状態のボタン。**  

![フォーカスされたボタン](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />フォーカスされたボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| ボタン | `CommonControls.ButtonFocused` |
| ボタンの境界線 | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>チェック ボックス コントロール  
![チェック ボックスをオン (の赤線)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303 161_CheckboxRedline")<br />チェック ボックスをオン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... チェック ボックス コントロールをドキュメント内に含まれているのもです。 | ... ui、チェック ボックス コントロールがありません。 |

**チェック ボックスをオンします既定の状態。**  

![チェック ボックスをオン](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303 162_Checkbox")<br />既定のチェック ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackground` |
| 境界線 | `CommonControls.CheckBoxBorder` |
| テキスト | `CommonControls.CheckBoxText` |
| グリフ | `CommonControls.CheckBoxGlyph` |

**チェック ボックスをオン: 無効の状態**  

![無効のチェック ボックス](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303 163_CheckboxDisabled")<br />無効のチェック ボックス  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundDisabled` |
| 境界線 | `CommonControls.CheckBoxBorderDisabled` |
| テキスト | `CommonControls.CheckBoxTextDisabled` |
| グリフ | `CommonControls.CheckBoxGlyphDisabled` |

**チェック ボックスをオン: 状態をホバー**  

 ![チェック ボックスをホバー](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303 164_CheckboxHover")<br />ホバー時のチェック ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundHover` |
| 境界線 | `CommonControls.CheckBoxBorderHover` |
| テキスト | `CommonControls.CheckBoxTextHover` |
| グリフ | `CommonControls.CheckBoxGlyphHover` |  

**チェック ボックスをオン: 状態の押されました。**  

![押されたチェック ボックス](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303 165_CheckboxPressed")<br />押されたチェック ボックス  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 境界線 | `CommonControls.CheckBoxBorderPressed` |
| テキスト | `CommonControls.CheckBoxTextPressed` |
| グリフ | `CommonControls.CheckBoxGlyphPressed` |  

**チェック ボックスをオン: 状態の重点を置いています。**  

![フォーカスされたチェック ボックスをオン](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303 166_CheckboxFocused")<br />フォーカスがある チェック ボックス  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundFocused` |
| 境界線 | `CommonControls.CheckBoxBorderFocused` |
| テキスト | `CommonControls.CheckBoxTextFocused` |
| グリフ | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>ドロップダウンとコンボ ボックス
![ドロップダウン/コンボ ボックス (の赤線)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303 167_DropDownComboBoxRedline")<br />ドロップダウン/コンボ ボックス (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ドロップダウンとコンボ ボックスのドキュメントもします。 | ... for ドロップダウンまたはコンボ ボックスのない UI。 |  
| | コマンド バーの...[ドロップダウン](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)または[コンボ ボックス](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)します。 |

**ドロップダウンとコンボ ボックス: 既定の状態**  

![ドロップダウン/コンボ ボックスの既定](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303 168_DropDownComboBox")<br />既定値のドロップダウン/コンボ ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackground` |
| 境界線 | `CommonControls.ComboBoxBorder` |
| テキスト | `CommonControls.ComboBoxText` |
| 区切り記号 | `CommonControls.ComboBoxSeparator` |
| グリフ | `CommonControls.ComboBoxGlyph` |
| グリフの背景 | `CommonControls.ComboBoxGlyphBackground` |

**ドロップダウンとコンボ ボックス: 無効の状態**  

![ドロップダウン/コンボ ボックスを無効になっている](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303 169_DropDownComboBoxDisabled")<br />無効になっているドロップダウン/コンボ ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundDisabled` |
| 境界線 | `CommonControls.ComboBoxBorderDisabled` |
| テキスト | `CommonControls.ComboBoxTextDisabled` |
| 区切り記号 | `CommonControls.ComboBoxSeparatorDisabled` |
| グリフ | `CommonControls.ComboBoxGlyphDisabled` |
| グリフの背景 | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**ドロップダウンとコンボ ボックス: 状態をホバー**  

![ポインターを合わせるとドロップダウン/コンボ ボックス](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303 170_DropDownComboBoxHover")<br />ホバー時のドロップダウン/コンボ ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundHover` |
| 境界線 | `CommonControls.ComboBoxBorderHover` |
| テキスト | `CommonControls.ComboBoxTextHover` |
| 区切り記号 | `CommonControls.ComboBoxSeparatorHover` |
| グリフ | `CommonControls.ComboBoxGlyphHover` |
| グリフの背景 | `CommonControls.ComboBoxGlyphBackgroundHover` |

**ドロップダウンとコンボ ボックス: 状態の押されました。**  

![押されたドロップダウン/コンボ ボックス](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303 171_DropDownComboBoxPressed")<br />押されたドロップダウン/コンボ ボックス  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundPressed` |
| 境界線 | `CommonControls.ComboBoxBorderPressed` |
| テキスト | `CommonControls.ComboBoxTextPressed` |
| 区切り記号 | `CommonControls.ComboBoxSeparatorPressed` |
| グリフ | `CommonControls.ComboBoxGlyphPressed` |
| グリフの背景 | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**ドロップダウンとコンボ ボックスのリスト項目ビュー: 状態の押されました。**  

 ![リスト項目のビューが押されたドロップダウン/コンボ ボックス](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303 174_DropDownComboBoxListView")<br />リスト項目のビューが押されたドロップダウン/コンボ ボックス  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| 境界線 | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| 項目のテキスト | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| 背景の影 | `CommonControls.ComboBoxListBackgroundShadow` |

**ドロップダウンとコンボ ボックス: 状態の重点を置いています。**  

![フォーカスを持つドロップダウン/コンボ ボックス](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303 172_DropDownComboBoxFocused")<br />フォーカスを持つドロップダウン/コンボ ボックス

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.ComboBoxBackgroundFocused` |
| 境界線 | `CommonControls.ComboBoxBorderFocused` |
| テキスト | `CommonControls.ComboBoxTextFocused` |
| 区切り記号 | `CommonControls.ComboBoxSeparatorFocused` |
| グリフ | `CommonControls.ComboBoxGlyphFocused` |
| グリフの背景 | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**ドロップダウンとコンボ ボックス テキスト入力の選択。**  

![ドロップダウン/コンボ ボックスのテキスト入力選択](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303 173_DropDownComboBoxTextInput")<br />ドロップダウン/コンボ ボックスのテキスト入力の選択  

| 要素 | トークン名:Category.color |
| --- | --- |
| ハイライト | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>表形式のデータ (グリッド) コントロール  
表形式のデータ コントロール (グリッド コントロールとも呼ばれる) は、複数列の大量のデータを表示するために使用する Visual Studio のコモン コントロールです。 標準の表形式のデータ コントロールは、[エラー一覧] ツール ウィンドウ、IntelliTrace レポート、メモリ ヒープ ビューなど、Visual Studio 内の複数の場所にあります。 提供される標準の表形式のデータ コントロールを常に使用します。 まれに、標準の表形式のデータ コントロールにアクセスできないことがあります。 このような場合は、次のトークン名を使用して、UI が Visual Studio の他の表形式のデータ コントロールと一貫性を保つようにします。  

![表形式のデータ/グリッド コントロール (の赤線)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303 197_TabularDataGridControlRedline")<br />表形式のデータ/グリッド コントロール (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... の表形式またはグリッド コントロール。 | ... for 表形式またはグリッド コントロールではない UI。 |

#### <a name="column-headers"></a>列ヘッダー  
列ヘッダーは、背景、境界線、タイトル テキスト、およびグリッドがその列で並べ替えられたときに通常使用されるオプションのグリフで構成されます。  

**列ヘッダー: 既定の状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Header.Default` |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 前景 (グリフ) | `Header.Glyph` |
| 境界線 | `Header.SeparatorLine` |

**列ヘッダー: 状態をホバー**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Header.MouseOver` |
| 前景 (テキスト) | `Environment.CommandBarTextHover` |
| 前景 (グリフ) | `Header.MouseOverGlyph` |
| 境界線 | `Header.SeparatorLine` |

**列ヘッダー: 状態の押されました。**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `CommonControls.CheckBoxBackgroundPressed` |
| 前景 (テキスト) | `CommonControls.CheckBoxBorderPressed` |
| 前景 (グリフ) | `CommonControls.CheckBoxTextPressed` |
| 境界線 | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>リスト ビュー項目  
 リスト ビュー項目は、背景とコンテンツで構成されます。 コンテンツは、テキスト、アイコン、またはその両方の場合があります。  

**ビューの項目を一覧表示します既定の状態。**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | 透明 |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 境界線 | なし |

**ビュー項目の一覧: アクティブな状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (テキスト) | `TreeView.SelectedItemActiveText` |
| 境界線 | なし |

**ビューの項目を一覧表示: 非アクティブな状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (テキスト) | `TreeView.SelectedItemInactiveText` |
| 境界線 | なし |  

### <a name="ui-text"></a>UI テキスト

#### <a name="instructional-text"></a>説明のテキスト
説明のテキストは、処理ダイアログまたはドキュメントのページの内容の著名な主な説明を示します。

![既定の説明テキスト](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />既定の説明テキスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>セカンダリの説明テキスト
テキストとコントロールの多くは、ドキュメントのページでは、いくつか説明のテキストは、別の色の値を使用します。 伝達する情報が最も重要なと UI 要素の全体的な密度を抑えるために役立ちます。 (も参照してください、以下のセクションのヒント テキスト)。

![セカンダリの指示テキスト](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />セカンダリの説明テキスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>ヒント テキスト
空のコントロール、または次に行うことをユーザーに表示する画面の空のドキュメントにコントロールを下でヒント テキストが表示されます。 ヒントのテキストは、ウィンドウまたはコントロールの背景で使用できます。

**既定のヒント テキスト**

![既定のヒント テキスト](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />既定のヒント テキスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.ControlEditHintText` |

**必要なヒント テキスト**

![ヒント テキストが必要な](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />必要なヒント テキスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.ControlRequiredHintText` |
| 背景 | `Environment.ControlRequiredBackground` |

**検索ボックス コントロールのテキスト**

> 参照してください[検索ボックス](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes)の検索コントロールに関連するその他の色のトークン。

![検索ボックス コントロールのテキスト](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />検索ボックス コントロールのテキスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>ハイパーリンク  
ハイパーリンクは、前景色と背景の組み合わせがない 1 つのコントロールです。 すべてのケースでは、濃色、灰色、白の背景で正しく表示されますフォア グラウンドのハイパーリンクの色を使用します。 ハイパーリンク コントロールの色トークンを使用しない場合は、システムの既定の色「を押すと、」赤で点滅はこれが表示されます。 コントロールで適切な環境の色トークンを使用していないことを示します。  

![ハイパーリンク (の赤線)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303 133_HyperlinkRedline")<br />ハイパーリンク (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム ハイパーリンクを作成する必要がある場合。 | ... のすべてのハイパーリンクのないもの。 |

**ハイパーリンク: 既定の状態**  

![既定のハイパーリンク](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303 134_Hyperlink")<br />既定のハイパーリンク

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.PanelHyperlink` |

**ハイパーリンク: ホバー状態**

![ポインターを合わせるとハイパーリンク](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303 135_HyperlinkHover")<br />ホバー時のハイパーリンク  

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.PanelHyperlinkHover` |

**押された状態のハイパーリンク:**

![押されたハイパーリンク](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303 136_HyperlinkPressed")<br />押されたハイパーリンク  

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.PanelHyperlinkPressed` |

**ハイパーリンク: 無効の状態**

![無効なハイパーリンク](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303 137_HyperlinkDisabled")<br />無効なハイパーリンク  

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>情報の表示  
情報バーは該当するコンテキストの詳細を提供するために使用され、常にドキュメント ウィンドウまたはツール ウィンドウの上部に表示されます。  

![情報バー (の赤線)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303 138_InfobarRedline")<br />情報バー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム情報バーを作成するときにします。 | ... の UI 要素は、情報バーに似ています。 |

**情報バー: 既定の状態**

![既定の情報バー](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303 139_Infobar")<br />既定の情報バー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.InfoBarBackground` |
| 前景 (テキスト) | `InfoBar.InfoBar` |
| 境界線 | `InfoBar.InfoBarBorder` |

**情報バーを閉じる (&times;) ボタンをクリックします既定の状態。**

![既定の情報バーを閉じる (&times;) ボタン](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />既定の情報バーを閉じる (&times;) ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButton` |
| 境界線 | `InfoBar.CloseButtonBorder` |
| グリフ | `InfoBar.CloseButtonGlyph` |

**情報バーを閉じる (&times;) ボタン: ホバー状態**

![Infobar Close (&times;) button on hover](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />情報バーを閉じる (&times;) ボタンをホバー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonHover` |
| 境界線 | `InfoBar.CloseButtonHoverBorder` |
| グリフ | `InfoBar.CloseButtonHoverGlyph` |

**情報バーを閉じる (&times;) ボタン: 状態の押されました。**

![情報バーを閉じる押された (&times;) ボタン](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />情報バーを閉じる押された (&times;) ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.CloseButtonDown` |
| 境界線 | `InfoBar.CloseButtonDownBorder` |
| グリフ | `InfoBar.CloseButtonDownGlyph` |

**ハイパーリンク ボタンの情報バー: 既定の状態**

![既定の情報バーのハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />既定の情報バーのハイパーリンク ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `InfoBar.Hyperlink` |

**ハイパーリンク ボタンの情報バー: 状態をホバー**

![ホバー時の情報バー ハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />ホバー時の情報バー ハイパーリンク ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Infobar.HyperlinkMouseOver`<br />(下線) の使用 |

**ハイパーリンク ボタンの情報バー: 状態の押されました。**

![情報バーが押されたハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />情報バーが押されたハイパーリンク ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Infobar.HyperlinkMouseDown`<br />(下線) の使用 |

**情報バー (文) 内のハイパーリンクのインライン: 既定の状態**

![既定のインライン情報バーのハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />既定のインライン情報バーのハイパーリンク ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `InfoBar.Hyperlink` |

**情報バー (文) 内のハイパーリンクのインライン: 状態をホバー**

![ポインターを合わせると、情報バー インライン ハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />ポインターを合わせると、情報バー インライン ハイパーリンク ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Infobar.HyperlinkMouseOver`<br />(下線) の使用 |

**情報バー (文) 内のハイパーリンクのインライン: 状態の押されました。**

![押された状態の情報バー インライン ハイパーリンク ボタン](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />情報バー インライン ハイパーリンク ボタンが押されました。

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Infobar.HyperlinkMouseDown`<br />(下線) の使用 |

**情報バー ボタンをクリックします既定の状態。**

![既定の情報バー ボタン](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />既定の情報バーのボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.Button` |
| 前景 (テキスト) | `InfoBar.Button` |
| 境界線 | `InfoBar.ButtonBorder` |

**情報バーのボタン: ホバー状態**

![ホバー時の情報バー ボタン](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />ホバー時の情報バー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseOver` |
| 前景 (テキスト) | `InfoBar.ButtonMouseOver` |
| 境界線 | `InfoBar.ButtonMouseOverBorder` |

**情報バーのボタン: 状態の押されました。**

![押された状態の情報バーのボタン](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />押された状態の情報バーのボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonMouseDown` |
| 前景 (テキスト) | `InfoBar.ButtonMouseDown` |
| 境界線 | `InfoBar.ButtonMouseDownBorder` |

**情報バーのボタン: 無効の状態**

![情報バーを無効になっているボタン](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />情報バーを無効になっているボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonDisabled` |
| 前景 (テキスト) | `InfoBar.ButtonDisabled` |
| 境界線 | `InfoBar.ButtonDisabledBorder` |

**情報バーのボタン: 状態の重点を置いています。**

![フォーカスのある情報バーのボタン](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />フォーカスのある情報バーのボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `InfoBar.ButtonFocus` |
| 前景 (テキスト) | `InfoBar.ButtonFocus` |
| 境界線 | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>スクロール バー  
スクロール バーは、Visual Studio 環境によってスタイルがおよび構成される必要はありません。 ただし、常に、UI が Visual Studio 環境のこの部分と一貫性が表示されるように、スクロール バーで使用する色を活用することをことがあります。  

![スクロール バー (の赤線)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303 140_ScrollbarRedline")<br />スクロール バー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... する UI を作成しているときに、Visual Studio のスクロール バーを一致させます。 | 常に一致するものには... スクロール バーの UI。 |

**スクロール バー: 既定の状態**  

![既定のスクロール バー](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303 141_Scrollbar")<br />既定のスクロール バー

| 要素 | トークン名:Category.color |
| --- | --- |
| スクロール バー | `Environment.ScrollBarBackground` |
| 前景 (つまみ) | `Environment.ScrollBarThumbBackground` |

**スクロール バー: 状態をホバー**

![ポインターを合わせるとスクロール バー](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303 143_ScrollbarHover")<br />ホバー時のスクロール バー

| 要素 | トークン名:Category.color |
| --- | --- |
| スクロール バー | `Environment.ScrollBarBackground` |
| 前景 (つまみ) | `Environment.ScrollBarThumbMouseOverBackground` |

*スクロール バー: 状態の押されました。**

![押されたスクロール バー](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303 145_ScrollbarPressed")<br />スクロール バーを押す  

| 要素 | トークン名:Category.color |
| --- | --- |
| スクロール バー | `Environment.ScrollBarBackground` |
| 前景 (つまみ) | `Environment.ScrollBarThumbPressedBackground` |

**スクロール バーの矢印: 既定の状態**  

![既定のスクロール バーの矢印](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303 142_ScrollbarArrow")<br />既定のスクロール バーの矢印

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowBackground`<br />(スクロール バーと同じ色に設定します。) |
| 前景 (グリフ) | `Environment.ScrollBarArrowGlyph` |

**スクロール バーの矢印: 状態をホバー**

![スクロール バーの矢印のホバー](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303 144_ScrollbarArrowHover")<br />ホバー時のスクロール バーの矢印  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowMouseOverBackground`<br />(スクロール バーと同じ色に設定します。) |
| 前景 (グリフ) | `Environment.ScrollBarArrowGlyphMouseOver` |

**スクロール バーの矢印: 状態の押されました。**  

![押されたスクロール バーの矢印](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303 146_ScrollbarArrowPressed")<br />スクロール バーの矢印を押す

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ScrollBarArrowPressedBackground`<br />(スクロール バーと同じ色に設定します。) |
| 前景 (グリフ) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>検索ボックス  
可能な場合は常に、Visual Studio 環境で提供されるコモン検索コントロールを使用します。 検索ボックスの色は、入力フィールド、動作設定ボタン、ドロップダウン ボタン、ドロップダウン メニューのトークン名が格納されている **ShellColors.pkgdef** ファイルの "SearchControl" カテゴリにあります。  

検索ボックスは次の複数の状態のいずれかの場合があり、一部の状態は相互に排他的です。  

-   "フォーカスされている" または "フォーカスされていない" は、カーソルがテキスト ボックス内にあるかどうかを示します。  

-   "アクティブ" または "非アクティブ" は、ユーザーがテキスト ボックスに検索クエリを入力したかどうかを示します。  

-   "ホバー" は、ユーザーがマウスを使用して検索ボックスの上にマウス ポインターを置いたことを意味します (この状態は他のすべての状態よりもオーバーライドされます)。  

-   "無効" は、現在のコンテキストに対して検索機能がオフになっていることを意味します。  

![検索ボックス (の赤線)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303 110_SearchBoxRedline")<br />検索ボックス (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム検索ボックスを設計している場合。 | ... のすべての検索ボックスのないもの。 |
| | ... 常に検索条件に一致するものはすべてのボックスの UI を実行します。 |

**検索入力フィールドの重点を置いています。**

![フォーカスされた検索入力フィールド](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303 111_SearchInputFieldFocused")<br />検索入力フィールドの重点を置いています。  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedBackground` |
| 前景 (テキスト) | `SearchControl.FocusedBackground` |
| 境界線 | `SearchControl.FocusedBorder` |
| 区切り記号 | `SearchControl.FocusedDropDownSeparator` |

**フォーカスされていない、アクティブな検索入力フィールド**

![検索入力フィールドのフォーカスされていない](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303 114_SearchInputFieldUnfocused")<br />フォーカスされていない、アクティブな検索入力フィールド

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.SearchActiveBackground` |
| 前景 (テキスト) | `SearchControl.SearchActiveBackground` |
| 境界線 | `SearchControl.UnfocusedBorder` |
| 区切り記号 | `SearchControl.DropDownSeparator` |

**フォーカスされていない、非アクティブな検索入力フィールド**

![フォーカスされていない、非アクティブな検索入力フィールド](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />フォーカスされていない、非アクティブな検索入力フィールド  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.Unfocused` |
| 前景 (テキスト) | `SearchControl.Unfocused` |
| 境界線 | `SearchControl.UnfocusedBorder` |
| 区切り記号 | `SearchControl.DropDownSeparator` |

**強調表示された検索入力フィールド (テキストのみ)**

![強調表示された検索入力フィールド](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303 120_SearchInputFieldHighlight")<br />強調表示された検索入力フィールド

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.Selection` |
| 前景 (テキスト) | `SearchControl.FocusedBackground` |
| 境界線 | なし |
| 区切り記号 | `SearchControl.FocusedDropDownSeparator` |

**無効な検索入力フィールド**

![無効な検索入力フィールド](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303 121_SearchInputFieldDisabled")<br />無効な検索入力フィールド

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.Disabled` |
| 前景 (テキスト) | `SearchControl.Disabled` |
| 境界線 | `SearchControl.DisabledBorder` |
| 区切り記号 | `SearchControl.DropDownSeparator` |

**フォーカスされた検索操作ボタン**

![フォーカスされた検索操作ボタン](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303 112_SearchActionButtonFocused")<br />フォーカスされた検索操作ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (検索グリフ) | `SearchControl.SearchGlyph` |
| 前景 (停止グリフ) | `SearchControl.StopGlyph` |
| 前景 (クリア グリフ) | `SearchControl.ClearGlyph` |
| 境界線 | N/A |

**フォーカスされていない検索操作ボタン**  

![フォーカスされていない検索操作ボタン](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303 115_SearchActionButtonUnfocused")<br />フォーカスされていない検索操作ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (検索グリフ) | `SearchControl.SearchGlyph` |
| 前景 (停止グリフ) | `SearchControl.StopGlyph` |
| 前景 (クリア グリフ) | `SearchControl.ClearGlyph` |
| 境界線 | N/A |

**押された検索操作ボタン**

![押された検索操作ボタン](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />押された検索操作ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.ActionButtonMouseDown` |
| 前景 (グリフ) | `SearchControl.ActionButtonMouseDownGlyph` |
| 境界線 | `SearchControl.ActionButtonMouseDownBorder` |

**無効な検索操作ボタン**

![検索操作ボタンが無効になっている](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303 122_SearchActionButtonDisabled")<br />無効な検索操作ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (グリフ) | `SearchControl.ActionButtonDisabledGlyph` |
| 境界線 | なし |

**フォーカスされた検索ドロップダウン ボタン**

![フォーカスされた検索ドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303 113_SearchDropdownButtonFocused")<br />フォーカスされた検索ドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.FocusedDropDownButton` |
| 前景 (グリフ) | `SearchControl.FocusedDropDownButtonGlyph` |
| 境界線 | `SearchControl.FocusedDropDownButtonBorder` |

**フォーカスされていない検索ドロップダウン ボタン**

![フォーカスされていない検索ドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303 116_SearchDropdownButtonUnfocused")<br />フォーカスされていない検索ドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.UnfocusedDropDownButton` |
| 前景 (グリフ) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| 境界線 | `SearchControl.UnfocusedDropDownButtonBorder` |

**押された検索ドロップダウン ボタン**

![押された検索ドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />押された検索ドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.MouseDownDropDownButton` |
| 前景 (グリフ) | `SearchControl.MouseDownDropDownButtonGlyph` |
| 境界線 | `SearchControl.MouseDownDropDownButtonBorder` |

**無効化された検索ドロップダウン ボタン**

![無効な検索ドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303 123_SearchDropdownButtonDisabled")<br />無効化された検索ドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | なし |
| 前景 (グリフ) | `SearchControl.DisabledDownButtonGlyph` |
| 境界線 | なし |

#### <a name="search-drop-down-lists"></a>検索ドロップダウン リスト  
検索ボックスのドロップダウン メニューには、Visual Studio での他のドロップダウン メニューより少し複雑になる可能性があります。 「提案される検索」と「検索オプション」のセクションでは、またはメニューで、両方を表示でき、それぞれが個別に色が設定します。 これらの 2 つのセクションが一緒に表示される場合は線で区切られ、ドロップダウン メニュー全体が境界線で囲まれます。  

![検索ボックスの一覧 (の赤線)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303 124_SearchDropdownRedline")<br />検索ボックスの一覧 (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム検索ドロップダウン リストを作成する場合。 | に対する他のコンテキストで表示されるドロップダウン リスト。 |
| ... 正しいリスト コンポーネントの正しいトークン名。 | 背景と前景の組み合わせが指定した以外すべて。 |

**ドロップダウン リストの要素を検索します。**

| 要素 | トークン名:Category.color |
| --- | --- |
| 境界線 | `SearchControl.PopupBorder` |
| 区切り記号 | `SearchControl.PopupSectionHeaderSeparator` |
| 影 | `Environment.DropShadowBackground` |

**検索をお勧めします既定の状態。**

![既定の提案される検索](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303 125_SearchSuggested")<br />既定の提案される検索  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `SearchControl.PopupItemText` |

**検索をお勧めします状態をホバー。**

![ポインターを合わせると検索をお勧め](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303 128_SearchSuggestedHover")<br />ポインターを合わせると、提案される検索

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `SearchControl.PopupMouseOverItemText` |
| 境界線 | `SearchControl.PopupControlMouseOverBorder` |

**検索オプション: 既定の状態**

![検索チェック ボックスをオン](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303 126_SearchCheckbox")<br />既定の検索オプション (チェック ボックス)  

![検索オプション](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303 127_SearchOptions")<br />既定の検索オプション (リンク)  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (チェック ボックス テキスト) | `SearchControl.PopupCheckboxText` |
| 前景 (リンク テキスト) | `SearchControl.PopupButtonText` |
| ヘッダーの背景 | `SearchControl.PopupSectionHeaderGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (ヘッダー テキスト) | `SearchControl.PopupSectionHeaderText` |

**検索オプション: 状態をホバー**

![検索オプション (チェック ボックス) がポインターを合わせると](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303 129_SearchCheckboxHover")<br />ポインターを合わせると、検索オプション (チェック ボックス)  

![検索オプション (リンク) がポインターを合わせると](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303 130_SearchOptionsHover")<br />ポインターを合わせると、検索オプション (リンク)  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (チェック ボックス テキスト) | `SearchControl.PopupCheckboxMouseDownText` |
| 前景 (リンク テキスト) | `SearchControl.PopupButtonMouseDownText` |
| 境界線 | `SearchControl.PopupControlMouseOverBorder` |

**検索オプション: 状態の押されました。**  

![検索オプション (チェック ボックス) が押された](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303 131_SearchSuggestedPressed")<br />検索オプション (チェック ボックス) を押す   

![検索オプション (リンク) が押された](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303 132_SearchOptionsPressed")<br />検索オプション (リンク) を押す  

| 要素 | トークン名:Category.color |
| --- | --- |
| チェック ボックスの背景 | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (チェック ボックス テキスト) | `SearchControl.PopupCheckboxMouseDownText` |
| リンクの背景 | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (リンク テキスト) | `SearchControl.PopupButtonMouseDownText` |

###  <a name="BKMK_TreeView"></a> ツリー ビュー  
ソリューション エクスプ ローラー、サーバー エクスプ ローラー、クラス ビューなどのいくつかのツール ウィンドウの色の名前によって色が制御されます階層組織スキームを実装する、`TreeView`カテゴリ。 ツリー ビューのすべての項目に背景色とテキスト色があります。 入れ子にされた子要素がある項目には、項目が展開されているか折りたたまれているかを示すグリフもあります。  

![ツリー ビュー (の赤線)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303 147_TreeViewRedline")<br />ツリー ビュー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... どこでも階層組織ビューを実装する必要があります。 | ... for されていないツリー ビューのようなものです。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**ツリー ビュー アイテム: 既定の状態**

![既定のツリー ビュー アイテム](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303 148_TreeView")<br />既定のツリー ビュー アイテム

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |
| 前景 (テキスト) | `TreeView.Background` |
| 前景 (グリフ) | `TreeView.Glyph` |
| 境界線 | なし |

**ツリー ビュー アイテム: 状態をホバー**

![ポインターを合わせると、ツリー ビュー アイテム](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303 149_TreeViewHover")<br />ポインターを合わせると、ツリー ビュー項目

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.Background` |  
| 前景 (テキスト) | `TreeView.Background` |
| 前景 (グリフ) | `TreeView.GlyphMouseOver` |
| 境界線 | なし |

**ツリー ビュー アイテム: 状態の上にドラッグします**

![ツリー ビュー項目のドラッグの経由で](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303 150_TreeViewDragOver")<br />ツリー ビュー アイテムをドラッグします。  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.DragOverItem` |
| 前景 (テキスト) | `TreeView.DragOverItem` |
| 前景 (グリフ) | `TreeView.DragOverItemGlyph` |
| 境界線 | なし |

**ツリー ビュー項目: 選択されている場合、状態の重点を置いています。**

![選択されているし、ツリー ビュー アイテムに重点を置いた](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303 151_TreeViewFocused")<br />選択されていると、フォーカスされたツリー ビュー項目

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (テキスト) | `TreeView.SelectedItemActive` |
| 前景 (グリフ) | `TreeView.SelectedItemActiveGlyph` |
| 境界線 | `TreeView.FocusVisualBorder` |

**ツリー ビュー項目: 選択された状態でフォーカスされていない状態**  

![選択されていると、フォーカスされていないツリー ビュー アイテム](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303 152_TreeViewUnfocused")<br />選択されていると、フォーカスされていないツリー ビュー項目

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (テキスト) | `TreeView.SelectedItemInactive` |
| 前景 (グリフ) | `TreeView.SelectedItemInactiveGlyph` |
| 境界線 | なし |

**ツリー ビュー アイテム: 置かれている、選択すると、および状態の重点を置いています。**

![選択されているし、ツリー ビュー アイテムをポイントしたときに重点を置いて](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303 153_TreeViewFocusedHover")<br />ポインターを合わせると選択され、フォーカスされたツリー ビュー アイテム  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive` |
| 前景 (テキスト) | `TreeView.SelectedItemActive` |
| 前景 (グリフ) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 境界線 | `TreeView.FocusVisualBorder` |

**ツリー ビュー アイテム: フォーカスされていない、選択した場合は、マウスでポイントされた状態**

![ポインターを合わせると選択され、フォーカスされていないツリー ビュー アイテム](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303 154_TreeViewUnfocusedHover")<br />ポインターを合わせると選択され、フォーカスされていないツリー ビュー項目  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive` |
| 前景 (テキスト) | `TreeView.SelectedItemInactive` |
| 前景 (グリフ) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| 境界線 | なし |

## <a name="shell-appearance"></a>シェルの外観

### <a name="background"></a>背景  
環境の背景色は、2 つのレイヤーで構成されます。 下部レイヤーは、IDE 全体にわたる単色です。 上部レイヤーは、コマンド シェルフの下、および IDE の左端と右端のツール ウィンドウ自動非表示チャネルの間に収まります。 上部と下部の背景レイヤーは、ライト テーマとダーク テーマで同じ色に設定されます。  

![Visual Studio シェル バック グラウンド (の赤線)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303 187_ShellBackgroundRedline")<br />Visual Studio シェル バック グラウンド (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for Visual Studio 環境の背景を一致する場所。 | 背景サーフェイスではない場所の塗りつぶしとして.。 |
| | ... as 前景要素上に配置する背景。 |

**下部レイヤー シェルの外観**

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Environment.EnvironmentBackground` |

**最上位のレイヤーのシェルの外観**

> グラデーション境界は、Visual Studio 2013 のライト テーマとダーク テーマで同じ色の値に設定されます。

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |  

### <a name="command-shelf"></a>コマンド シェルフ  
コマンド シェルフの背景には 2 セットのトークン名が使用されます。1 セットはメニュー バーが位置する場所、もう 1 セットはコマンド バーが位置する場所に使用されます。 個々のコマンド バー グループには、独自の背景色値があります。これについては「コマンド バー」セクションで詳しく説明しています。 メニュー バーとコマンド バーのテキストについては、それぞれメニューとコマンド バーのセクションで説明しています。  

![Visual Studio コマンド シェルフ (の赤線)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303 188_CommandShelfRedline")<br />Visual Studio コマンド シェルフ (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for メニューまたはツールバーを配置する領域。 | ... の領域をいないコマンド シェルフに似ています。 |
|... with 適切な背景と前景トークン名の組み合わせ。 | |

**コマンド シェルフのメニュー バー**

> グラデーション境界は、Visual Studio 2013 のライト テーマとダーク テーマで同じ色の値に設定されます。

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

* * コマンド シェルフ コマンド バー * *

> グラデーション境界は、Visual Studio 2013 のライト テーマとダーク テーマで同じ色の値に設定されます。

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>マニフェスト デザイナー  
マニフェスト デザイナーは、Windows 8 および Windows Phone 8 プロジェクトのマニフェスト ファイルを編集しやすくするための手段として設計されています。 使用可能な共有フレームワークはありませんが、向き/ナビゲーション タブと全体的な構造のデザイン レイアウトおよび色を一致させることが適切な場合があります。 レイアウトの詳細については、「 [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)」を参照してください。  

![マニフェスト デザイナー (の赤線)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303 175_ManifestDesignerRedline")<br />マニフェスト デザイナー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... の設計者、マニフェスト デザイナーに似ています。 | ... 最大 6 つのタブがある場合。 |
| ... の代わりに、ドキュメント内のエディターの上部でコモン タブ コントロールを使用する次のようにもです。 | マニフェスト デザイナーのように構造化されていない任意の UI の. |

**マニフェスト デザイナーの選択 タブ: 既定の状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.TabActive` |
| 境界線 | なし |

**マニフェスト デザイナーの選択した説明ペイン: 既定の状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.DescriptionPane` |

**マニフェスト デザイナーの選択したコンテンツ ページ: 既定の状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Background` |
| ダイアログ ヘルパー テキスト | `ManifestDesigner.WatermarkText`<br />(このトークンの名前は、その関数を一致しない) |

**マニフェスト デザイナー タブ: 状態の選択を解除**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Inactive` |

**マニフェスト デザイナー タブ: ホバー状態**

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>コマンドの構造  

###  <a name="BKMK_CommandMenus"></a> メニュー  
メニューに Visual Studio 内で複数の場所で発生することができます。 埋め込みドキュメントまたはツールのウィンドウまたは IDE 全体のさまざまな場所で右クリックして、メイン メニュー バー。 他の UI 要素に関連付けられたメニューの実装については、それぞれの要素のセクションで説明します。 Visual Studio 環境で提供される標準のメニュー実装を常に使用してください。 ただし、まれに、標準の Visual Studio メニューにアクセスできないことがあります。 このような場合は、次のトークン名を使用して、UI が Visual Studio の他のメニューと一貫性を保つようにします。  

![Visual Studio のメニュー (の赤線)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303 000_MenuRedline")<br />Visual Studio のメニュー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム メニューを作成する必要がある場合。| ... のみの背景色。 常に指定された背景と前景の組み合わせを使用します。 |
| ... Visual Studio のメニューと一致する新しい UI コンポーネントがある場合。| |

#### <a name="menu-titles"></a>メニュー タイトル  
メニュー タイトルは、背景、境界線、タイトル テキスト、および通常、メニューがコマンド バーにあるときは、オプションのグリフで構成されます。  

![メニュー タイトル (の赤線)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303 001_MenuTitleRedline")<br />メニュー タイトル (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム メニュー タイトルを作成するたびにします。 | ... のすべてのメニュー タイトルは常に一致するもの。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**メニュー タイトル: 既定の状態**

![既定のメニュー タイトル](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303 002_MenuTitleDefault")<br />既定のメニュー タイトル

![既定のグリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303 003_MenuTitleWithGlyphDefault")<br />グリフの既定のメニュー タイトル

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 前景 (グリフ) | `Environment.CommandBarMenuGlyph` |
| 境界線 | なし |

**メニュー タイトル: 状態をホバー**  

![ホバー メニュー タイトル](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303 004_MenuTitleHover")<br />ホバー時のメニュー タイトル  

![ポインターを合わせるとグリフのメニュー タイトル](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303 005_MenuTitleWithGlyphHover")<br />ホバー時のグリフのメニュー タイトル

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextHover` |
| 前景 (グリフ) | `Environment.CommandBarMenuMouseOverGlyph` |  
| 境界線 | `Environment.CommandBarBorder` |

**メニュー タイトル: 状態の押されました。**  

![メニュー タイトルが押された](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303 006_MenuTitlePressed")<br />押されたメニュー タイトル

![グリフのメニュー タイトルが押された](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303 007_MenuTitleWithGlyphPressed")<br />グリフのメニュー タイトルを押す

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 前景 (グリフ) | `Environment.CommandBarMenuMouseDownGlyph` |
| 境界線 | `Environment.CommandBarMenuBorder`<br />(だけ左、上で、右辺。) |  

**メニュー タイトル: 無効の状態**  

![グリフのメニュー タイトルを無効になっている](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303 008_MenuTitleWithGlyphDisabled")<br />グリフの無効化されたメニュー タイトル

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (テキスト) | `Environment.CommandBarTextInactive` |
| 前景 (グリフ) | `Environment.CommandBarTextInactive` |
| 境界線 | なし |

#### <a name="menu-items"></a>メニュー項目
個々のメニュー項目は、メニュー テキストとオプションのアイコン、チェック ボックス、またはサブメニュー グリフで構成されます。 その背景色とテキストの色はホバー時に変化します。 この色トークンは、背景と前景のペアです。  

![メニュー項目の赤線](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303 009_MenuItemRedline")  

| 使用してください. | 使用しないでください. |
|---|---|
| . 任意のドロップダウン リストのメニュー バーまたはコマンド バーから起動されます。 | ... for 別のコンテキストで、ボックスの一覧。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**メニュー項目: 既定の状態**

![既定のメニュー項目](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303 010_MenuDefault")<br />既定のメニュー項目  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 前景 (サブメニュー グリフ) | `Environment.CommandBarMenuSubmenuGlyph` |
| 境界線 | `Environment.CommandBarMenuBorder` |
| アイコン チャネルの背景 | `Environment.CommandBarMenuIconBackground` |
| 区切り記号 | `Environment.CommandBarMenuSeparator` |
| 影 | `Environment.DropShadowBackground` |

**メニュー項目: チェックされ、状態の選択**  

![チェックされたメニュー](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303 011_MenuChecked")<br />チェックされたメニュー項目

![選択したメニュー](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303 012_MenuSelected")<br />選択されたメニュー項目    

| 要素 | トークン名:Category.color |
| --- | --- |
| チェック マーク | `Environment.CommandBarCheckBox` |  
| チェック マークの背景 | `Environment.CommandBarSelectedIcon` |  
| アイコンの背景 | `Environment.CommandBarSelected` |
| アイコンの境界線 | `Environment.CommandBarSelectedBorder` |

**メニュー項目: 状態をホバー**  

![メニュー ホバー](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303 013_MenuHover")<br />ホバー メニュー項目

![チェックされたメニュー ホバー](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303 014_MenuHoverChecked")<br />ホバー メニュー項目のチェック

![選択されたメニュー ホバー](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303 015_MenuHoverSelected")<br />ポインターを合わせると、選択されたメニュー項目

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (テキスト) | `Environment.CommandBarMenuItemMouseOver` |
| 前景 (サブメニュー グリフ) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| チェック マーク | `Environment.CommandBarCheckBoxMouseOver` |
| チェック マークの背景 | `Environment.CommandBarHoverOverSelectedIcon` |
| アイコンの背景 | `Environment.CommandBarHoverOverSelected` |
| アイコンの境界線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

**メニュー項目: 無効の状態**  

![メニューの無効化](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303 016_MenuDisabled")<br />無効なメニュー項目

![メニューの無効化チェック](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303 017_MenuDisabledChecked")<br />チェック マークを無効になっているメニュー項目

| 要素 | トークン名:Category.color |
| --- | --- |
| 前景 (テキスト) | `Environment.CommandBarTextInactive` |
| 前景 (サブメニュー グリフ) | `Environment.CommandBarMenuSubmenuGlyph` |
| チェック マーク | `Environment.CommandBarCheckBoxDisabled` |
| チェック マークの背景 | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>コマンド バー  
コマンド バーは、特にコマンド シェルフとに埋め込まれたツールまたはドキュメント ウィンドウの Visual Studio IDE 内で複数の場所に表示できます。  

通常は、Visual Studio 環境で提供される標準のコマンド バー実装を常に使用してください。 標準メカニズムを使用すると、すべての表示の詳細が正しく表示され、対話型要素が他の Visual Studio のコマンド バーのコントロールと一貫して動作するようになります。 ただし、独自のコマンド バーを作成する必要がある場合は、次のトークン名を使用してスタイルを正しく設定してください。  

![コマンド バーの赤線](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303 018_CommandBarRedline")<br />コマンド バー (の赤線)  

![オーバーフロー ボタンの赤線](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303 019_OverflowButtonRedline")<br />オーバーフロー ボタン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| … 必要がある、埋め込みコマンド バーの位置で、ことはできません、標準の Visual Studio のコマンド バー実装を使用します。 | ... for は、コマンド バーのような UI 要素。 |
| | ... for トークン名が指定されているもの以外のコマンド バー コンポーネント。 |

#### <a name="command-bar-groups"></a>コマンド バー グループ  
コマンド バー グループは、関連する一連のコマンド バー コントロールで構成され、任意の数のボタン、分割ボタン、ドロップダウン メニュー、コンボ ボックス、またはメニューを含めることができます。 これらのコントロールの色は別々のトークン名によって制御され、このガイドの他の場所で個別に説明されています。 区切り線を使用して、コマンド バー グループを関連するサブグループに分割します。  

![コマンド バー グループの赤線](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303 020_CommandBarGroupRedline")<br />コマンド バー グループ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |  
| … 必要がある、埋め込みコマンド バーの位置で、ことはできません、標準の Visual Studio のコマンド バー実装を使用します。 | ... for は、コマンド バーのような UI 要素。 |
| | ... for トークン名が指定されているもの以外のコマンド バー コンポーネント。 |

**コマンド バー グループ: 既定の状態**  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 境界線 | `Environment.CommandBarToolBarBorder` |
| ドラッグ ハンドル | `Environment.CommandBarDragHandle` |
| 区切り記号 | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>コマンド アイコン  
![コマンド アイコンの赤線](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303 021_CommandIconRedline1")<br />コマンド アイコン (の赤線)  

![テキスト コマンド アイコンの赤線](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303 022_CommandIconRedline2")<br />テキスト コマンド アイコン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for コマンド バー上に配置されるボタン。 | ... for を独自のトークン名を持つコントロール。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**コマンド アイコン: 既定の状態**  

![アイコンの既定値をコマンド](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303 023_CommandIconDefault")<br />コマンドの既定のアイコン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | 該当なし (コマンド バーの背景から継承) |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 境界線 | N/A |

**コマンド アイコン: 既定の選択された状態**

![既定では、選択されたコマンド アイコン](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303 024_CommandIconDefaultSelected")<br />既定では、選択されたコマンド アイコン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarSelected` |
| 前景 (テキスト) | `Environment.CommandBarTextSelected` |
| 境界線 | `Environment.CommandBarSelectedBorder` |

**コマンド アイコン: ホバーまたはフォーカスの状態**  

![コマンド アイコン ホバーまたはフォーカスを](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303 025_CommandIconHover")<br />コマンド アイコン ホバーまたはフォーカスを

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextHover` |
| 境界線 | `Environment.CommandBarBorder` |

**コマンド アイコン: ホバーまたはフォーカスの状態、選択されています。**

![コマンド アイコン ホバーまたはフォーカスを選択した](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303 026_CommandIconHoverSelected")<br />選択したコマンド アイコン ホバーまたはフォーカスを

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarHoverOverSelected` |
| 前景 (テキスト) | `Environment.CommandBarTextHoverOverSelected` |
| 境界線 | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **コマンド アイコン: 状態の押されました。**  

![コマンド アイコンが押された](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303 027_CommandIconPressed")<br />押されているコマンド アイコン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextMouseDown` |
| 境界線 | `Environment.CommandBarBorder` |

**コマンド アイコン: 無効の状態**  

![無効になっているコマンド アイコン](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303 028_CommandIconDisabled")<br />無効化されたコマンド アイコン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | 該当なし (コマンド バーの背景から継承) |
| 前景 (テキスト) | `Environment.CommandBarTextInactive` |
| 境界線 | N/A |

####  <a name="BKMK_CommandComboBox"></a> コマンド バー コンボ ボックス

> [!IMPORTANT]
> コンボ ボックスはドロップダウンに似ていますが、編集可能なテキスト領域が含まれます。 ドロップダウンに、編集可能なテキスト領域が含まれていない場合は、色のトークンを使用して[コマンド バーのドロップダウン リスト](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)します。  

![コマンド バーのコンボ ボックスの赤線](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303 029_ComboBoxRedline")<br />コマンド バーのコンボ ボックス (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム コンボ ボックスを作成するときにします。 | ... の何もしない常に、コマンドに一致するようにバー UI。 |
| ... コンボ ボックスに次のようなコマンド バー コントロールを作成するときにします。 | ... をスタイル設定されたコンボ ボックスにアクセス権がある場合。 |

**コマンド バー コンボ ボックスの入力フィールド: 既定の状態**

![コマンド バー コンボ ボックスの入力フィールド](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303 030_ComboBoxInputField")<br />コマンド バー コンボ ボックスの入力フィールド  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxBackground` |
| 前景 (テキスト) | `Environment.ComboBoxText` |
| 境界線 | `Environment.ComboBoxBorder` |
| 区切り記号 | 区切り記号なし |

**コマンド バーのドロップダウン ボタン: 既定の状態**  

![コンボ ボックスのドロップ&#45;下向きの矢印ボタン](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303 031_ComboBoxDropdownButton")<br />コマンド バーのドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | 該当なし (コマンド バーの背景から継承) |
| 前景 (グリフ) | `Environment.ComboBoxGlyph` |

**コマンド バーのドロップダウン リスト: 既定の状態**

![コマンド バーのドロップダウン リスト](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303 032_ComboBoxDropdownList")<br />コマンド バーのドロップダウン リスト

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxPopupBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.ComboBoxItemText` |
| 境界線 | `Environment.ComboBoxPopupBorder` |

**コマンド バー コンボ ボックスの入力フィールド: 状態をホバー**  

![コマンド バー コンボ ボックスの入力フィールドのホバー](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303 033_ComboBoxInputFieldHover")<br />コマンド バー コンボ ボックスの入力フィールドのホバー  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.ComboBoxMouseOverText` |
| 境界線 | `Environment.ComboBoxMouseOverBorder` |
| 区切り記号 | `Environment.ComboBoxMouseOverSeparator` |

 **コマンド バーのドロップダウン ボタン: ホバー状態**  

![ポインターを合わせるとコマンド バーのドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303 034_ComboBoxDropdownButtonHover")<br />ポインターを合わせるとコマンド バーのドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseOverBackground` |
| 前景 (グリフ) | `Environment.ComboBoxMouseOverGlyph` |

**コマンド バーのドロップダウン リスト: 状態をホバー**

 ![コマンド バーのドロップダウン リストのホバー](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303 035_ComboBoxDropdownListHover")<br />ポインターを合わせるとコマンド バーのドロップダウン リスト  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 (メニュー項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (テキスト) | `Environment.ComboBoxItemMouseOverText` |
| 境界線 (メニュー項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **コマンド バー コンボ ボックスの入力フィールド: 状態の重点を置いています。**  

![コマンド バーのコンボ ボックスの入力フィールドに重点を置いた](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303 036_ComboBoxInputFieldFocused")<br />コマンド バー コンボ ボックスの入力フィールドの重点を置いています。

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedBackground` |
| 前景 (テキスト) | `Environment.ComboBoxFocusedText` |
| 境界線 | `Environment.ComboBoxFocusedBorder` |
| 区切り記号 | `Environment.ComboBoxFocusedButtonSeparator` |

**コマンド バーのドロップダウン ボタン: 状態の重点を置いています。**  

![コマンド バーのドロップダウン ボタンに重点を置いた](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303 037_ComboBoxDropdownButtonFocused")<br />フォーカスのあるコマンド バーのドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxFocusedButtonBackground` |
| 前景 (グリフ) | `Environment.ComboBoxFocusedGlyph` |

 **コマンド バー コンボ ボックスの入力フィールド: 状態の押されました。**  

![コマンドを押されたコンボ ボックスの入力フィールド バー](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303 038_ComboBoxInputFieldPressed")<br />コマンド バー コンボ ボックスの入力フィールドを押す

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxMouseDownBackground` |
| 前景 (テキスト) | `Environment.ComboBoxMouseDownText` |
| 境界線 | `Environment.ComboBoxMouseDownBorder` |
| 区切り記号 | `Environment.ComboBoxMouseDownSeparator` |

**コマンド バーのドロップダウン ボタン: 状態の押されました。**

![コマンド バーのドロップダウン ボタンが押された](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303 039_ComboBoxDropdownButtonPressed")<br />コマンド バーのドロップダウン ボタンが押されました。  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxButtonMouseDownBackground` |
| 前景 (グリフ) | `Environment.ComboBoxMouseDownGlyph` |

**コマンド バー コンボ ボックスの入力フィールド: 無効の状態**  

![コマンド バーのコンボ ボックスの入力フィールドを無効になっている](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303 041_ComboBoxInputFieldDisabled")<br />無効なコマンド バーのコンボ ボックスの入力フィールド  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ComboBoxDisabledBackground` |
| 前景 (テキスト) | `Environment.ComboBoxDisabledText` |
| 境界線 | `Environment.ComboBoxDisabledBorder` |
| 区切り記号 | 区切り記号なし |

**コマンド バーのドロップダウン ボタン: 無効の状態**  

![コマンド バーのドロップダウン ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303 040_ComboBoxDropdownButtonDisabled")<br />無効なコマンド バーのドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (グリフ) | `Environment.ComboBoxDisabledGlyph` |

####  <a name="BKMK_CommandDropDown"></a> コマンド バーのドロップダウン リスト

> [!IMPORTANT]
>  ドロップダウンはコンボ ボックスに似ていますが、編集可能なテキスト領域がありません。 ドロップダウンにでは、編集可能なテキスト領域が含まれている場合は、色のトークンを使用して[コマンド バーのコンボ ボックス](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)します。  

![コマンド バーのドロップダウン (の赤線)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303 042_DropdownRedline")<br />コマンド バーのドロップダウン (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ドロップダウン リストのカスタム コントロールを作成する場合。 | ... のないものはすべて、ドロップダウン リストに似ています。 |
| | ... のコンボ ボックスまたは分割ボタン。 |   

**コマンド バーのドロップダウン リストのフィールド: 既定の状態**  

![コマンド バーのドロップダウン リストのフィールドを既定](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303 043_DropdownSelectionField")<br />既定のコマンド バーのドロップダウンの選択フィールド  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownBackground` |
| 前景 (テキスト) | `DropDownText` |
| 境界線 | `DropDownBorder` |
| 区切り記号 | 区切り記号なし |

**コマンド バーのドロップダウン ボタン: 既定の状態**

![既定のコマンド バーのドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303 044_DropdownButton")<br />既定のコマンド バーのドロップダウン ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (グリフ) | `Environment.DropDownGlyph` |

**コマンド バーのドロップダウン リスト: 既定の状態**

![コマンド バーのドロップダウン リストを既定](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303 045_DropdownList")<br />既定のコマンド バーのドロップダウン リスト  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownPopupBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.ComboBoxItemText` |
| 境界線 | `Environment.DropDownPopupBorder` |
| 影 | `Environment.DropShadowBackground` |

**コマンド バーのドロップダウン リストのフィールド: 状態をホバー**  

![ポインターを合わせるとコマンド バーのドロップダウンの選択フィールド](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303 046_DropdownSelectionFieldHover")<br />ポインターを合わせるとコマンド バーのドロップダウンの選択フィールド  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.DropDownMouseOverText` |
| 境界線 | `Environment.DropDownMouseOverBorder` |
| 区切り記号 | `Environment.DropDownButtonMouseOverSeparator` |

**コマンド バーのドロップダウン ボタン: ホバー状態**  

![ポインターを合わせるとコマンド バーのドロップダウン ボタン](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303 047_DropdownButtonHover")<br />ポインターを合わせるとコマンド バーのドロップダウン ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseOverBackground` |
| 前景 (グリフ) | `Environment.DropDownMouseOverGlyph` |

**コマンド バーのドロップダウン リスト: 状態をホバー**  

![コマンド バーのドロップダウン リストのホバー](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303 048_DropdownListHover")<br />ポインターを合わせるとコマンド バーのドロップダウン リスト  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 (メニュー項目) | `Environment.ComboBoxItemMouseOverBackground` |
| 前景 (テキスト) | `Environment.ComboBoxItemMouseOverText` |
| 境界線 (メニュー項目) | `Environment.ComboBoxItemMouseOverBorder` |

 **コマンド バーのドロップダウン リストのフィールド: 状態の押されました。**  

![Drop&#45;押された選択フィールド ダウン](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303 049_DropdownSelectionFieldPressed")<br />コマンドを押されたバーのドロップダウンの選択フィールド

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownMouseDownBackground` |
| 前景 (テキスト) | `Environment.DropDownMouseDownText` |
| 境界線 | `Environment.DropDownMouseDownBorder` |
| 区切り記号 | `Environment.DropDownButtonMouseDownSeparator` |

**コマンド バーのドロップダウン ボタン: 状態の押されました。**

![コマンド バーのドロップダウン ボタンが押された](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303 050_DropdownButtonPressed")<br />コマンド バーのドロップダウン ボタンが押されました。  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownButtonMouseDownBackground` |
| 前景 (グリフ) | `Environment.DropDownMouseDownGlyph` |

**コマンド バーのドロップダウン リストのフィールド: 無効の状態**  

![コマンド バーのドロップダウン リストのフィールドを無効になっている](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303 051_DropdownSelectionFieldDisabled")<br />無効なコマンド バーのドロップダウンの選択フィールド

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DropDownDisabledBackground` |
| 前景 (テキスト) | `Environment.DropDownDisabledText` |
| 境界線 | `Environment.DropDownDisabledBorder` |
| 区切り記号 | 区切り記号なし |

**コマンド バーのドロップダウン ボタン: 無効の状態**

![コマンド バーのドロップダウン ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303 052_DropdownButtonDisabled")<br />無効なコマンド バーのドロップダウン ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (グリフ) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>コマンド バーの分割ボタン
分割ボタンは、ボタン、メニュー、コマンド バー テキストなど、他のコマンド バー コントロールと多くのトークン名を共有します。 ここでは利便性のために、すべての必要なアクション ボタンとドロップダウン ボタンのトークン名を繰り返しています。 分割ボタンのドロップダウン リストが実装の[コマンド バーのメニュー](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)します。  

![分割ボタンの赤線](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303 053_SplitButtonRedline")<br />コマンド バーの分割ボタン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... のカスタム分割ボタンを作成する場合。 | ... for ボタンの他の種類。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**コマンド バー ボタンを分割する: 既定の状態**  

![既定のコマンド バーの分割ボタン](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303 054_SplitButton")<br />コマンド バーの既定の分割ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | なし |
| 前景 (テキスト) | `Environment.CommandBarTextActive` |
| 前景 (グリフ) | `Environment.CommandBarSplitButtonGlyph` |
| 境界線 | N/A |
| 区切り記号 | N/A |

**コマンド バーの分割ボタン: ホバー状態**  

![コマンド バーの分割ボタンをホバー](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303 055_SplitButtonHover")<br />コマンド バーの分割ボタンをホバー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextHover` |
| 前景 (グリフ) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| 境界線 | `Environment.CommandBarBorder` |
| 区切り記号 | `Environment.CommandBarSplitButtonSeparator` |

**コマンド バーの分割ボタン: 状態の押されました。**  

![コマンド バーの分割ボタンが押された](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303 056_SplitButtonPressed")<br />押された状態のコマンド バーの分割ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarMouseDownBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.CommandBarTextMouseDown` |
| 前景 (グリフ) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| 境界線 | `Environment.CommandBarBorder` |
| 区切り記号 | N/A |

**コマンド バーの分割ボタン: 無効の状態**

![コマンド バーの分割ボタンを無効になっている](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303 057_SplitButtonDisabled")<br />分割ボタンを無効になっているコマンド バー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (テキスト) | `Environment.ComboBoxItemTextInactive` |
| 前景 (グリフ) | `Environment.CommandBarTextInactive` |
| 境界線 | N/A |
| 区切り記号 | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>'その他のオプション' と 'Overflow' バーのコマンド ボタン  
[その他のオプション] ボタンは、関連するコマンド バー ボタンを追加または削除して、コマンド バー グループをカスタマイズできる場合に使用します。 [オーバーフロー] ボタンは、横のスペースが不足しているためにコマンド バーが切り詰められた場合に表示され、クリックすると、表示できないコマンド バー ボタンを含むメニューが表示されます。 これら 2 つのボタンの色は、同じトークン名のセットによって制御されます。  

![コマンド バーの [複数のオプション] ボタン (の赤線)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303 058_MoreOptionsRedline")<br />コマンド バーの [複数のオプション] ボタン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for カスタム '詳細オプション または オーバーフロー ボタン。 | ... for 'その他のオプション または オーバーフロー ボタンと同様の機能を持たないボタン。 |

**コマンド バーの 'その他のオプション' と「オーバーフロー」ボタン: 既定の状態**  

![コマンド バーの [複数のオプション] ボタンを既定](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303 059_MoreOptions")<br />既定のコマンド バーの [複数のオプション] ボタン

![既定のコマンド バーのボタンの「オーバーフロー」](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303 060_Overflow")<br />既定のコマンド バーの [オーバーフロー] ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsBackground` |
| 前景 (グリフ) | `Environment.CommandBarOptionsGlyph` |

**コマンド バーの 'その他のオプション' と「オーバーフロー」ボタン: ホバー状態**

![コマンド バーのホバー時 '他のオプション' ボタン](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303 061_MoreOptionsHover")<br />コマンド バー ポインターを合わせると複数オプション ボタン  

![コマンド バー「オーバーフロー」ボタン ホバー](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303 062_OverflowOptions")<br />ポインターを合わせるとコマンド バー「オーバーフロー」ボタン   

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (グリフ) | `Environment.CommandBarOptionsMouseDownGlyph` |

**コマンド バーの 'その他のオプション' と「オーバーフロー」ボタン: 状態の押されました。**  

![コマンド バーの [複数のオプション] ボタンが押された](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303 063_MoreOptionsPressed")<br />コマンド バーの [複数のオプション] ボタンを押す  

![押されたオーバーフロー](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303 064_OverflowPressed")<br />コマンド バーの「オーバーフロー」ボタンが押されました。  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (グリフ) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>ドキュメント ウィンドウ  
Visual Studio 環境で提供しているため、ドキュメント ウィンドウをレプリケートする必要はありません。 ただし、UI が Visual Studio 環境のこの部分と常に一貫性のある状態で表示されるように、ドキュメント ウィンドウで使用する色を活用することができます。  

ドキュメント ウィンドウの色のトークンを使用する場合は、同様の要素に対してのみ、常にペアで使用するように注意します。 行わない場合は、UI に予期しない結果を取得可能性があります。  

### <a name="document-window-frames"></a>ドキュメント ウィンドウ フレーム  
ドキュメント ウィンドウは IDE にドッキングしたり、別のウィンドウとしてフローティングさせたりすることができます。 ドキュメント ウィンドウは IDE の外部のフローティング、ときにいます、ドキュメント ウェル内に存在、背景、境界線、テキスト、およびタブの色を IDE の一部である場合と同じですが。 ただし、ドキュメントは、独自の背景、境界線、テキストの色を持つフレーム内に配置されます。 ツール ウィンドウをドキュメント ウェルにドッキングした場合、ツール ウィンドウはタブの動作と色をドキュメント ウィンドウのトークン名から継承します。  

![ドッキングされたドキュメント ウィンドウ (の赤線)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303 065_DockedDocumentWindowRedline")<br />ドッキングされたドキュメント ウィンドウ (の赤線)  

![フローティング ドキュメント ウィンドウ (の赤線)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303 066_FloatingDocumentWindowRedline")<br />フローティング ドキュメント ウィンドウ (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ドキュメント ウィンドウと一致させる UI を作成しているすべての場所。 | ... ui を自動的に変更しない場合、シェルでは、テーマの更新には。 |

**ドッキングまたはフローティング ドキュメント ウィンドウ: 既定の状態**  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | ドキュメントの種類によって異なります |
| 前景 (テキスト) | ドキュメントの種類によって異なります |
| 境界線 | `Environment.ToolWindowBorder` |

**フォーカスがある、フローティング ドキュメント ウィンドウ フレーム: 既定の状態**

![フローティング ドキュメント ウィンドウ フレームに重点を置いて、既定](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303 067_FrameFocused")<br />既定の重点を置いて、フローティング ドキュメント ウィンドウ フレーム

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrame` |
| 前景 (テキスト) | `Environment.ToolWindowFloatingFrame` |
| 前景 (グリフ) | `Environment.RaftedWindowButtonActiveGlyph` |
| 境界線 | `Environment.MainWindowActiveDefaultBorder` |
| 境界線 (グリフ) | `Environment.RaftedWindowButtonActiveBorder`<br />(透明に設定) |

**フォーカスされていない、フローティング ドキュメント ウィンドウ フレーム: 既定の状態**  

![既定のフォーカスされていない、フローティング ドキュメント ウィンドウ フレーム](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303 068_FrameUnfocused")<br />既定のフォーカスされていない、フローティング ドキュメント ウィンドウ フレーム

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (テキスト) | `Environment.ToolWindowFloatingFrameInactive` |
| 前景 (グリフ) | `Environment.RaftedWindowButtonInactiveGlyph` |
| 境界線 | `Environment.MainWindowInactiveBorder` |
| 境界線 (グリフ) | `Environment.RaftedWindowButtonInactiveBorder`<br />(透明に設定) |

**フォーカスがある、フローティング ドキュメント ウィンドウ フレーム: 状態をホバー**

![フォーカスがある、ポインターを合わせるとドキュメント ウィンドウ フレームを浮動](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303 069_FrameFocusedHover")<br />フォーカスがある、ポインターを合わせるとドキュメント ウィンドウ フレームを浮動小数点  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 (グリフ) | `Environment.RaftedWindowButtonHoverActive` |
| 前景 (グリフ) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| 境界線 (グリフ) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**フォーカスされていない、フローティング ドキュメント ウィンドウ フレーム: 状態をホバー**  

![フォーカスされていない、フローティング ドキュメント ウィンドウのフレーム ポインターを合わせると](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303 070_FrameUnfocusedHover")<br />ポインターを合わせると、フォーカスされていない、フローティング ドキュメント ウィンドウ フレーム

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 (グリフ) | `EnvironmentRaftedWindowButtonHoverInactive` |
| 前景 (グリフ) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| 境界線 (グリフ) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**フォーカスがある、フローティング ドキュメント ウィンドウ フレーム: 状態の押されました。**  

![フォーカスがある、ドキュメント ウィンドウ フレームにキーを押して浮動](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303 071_FrameFocusedPressed")<br />フォーカスがある、ドキュメント ウィンドウ フレームにキーを押して浮動

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 (グリフ) | `Environment.RaftedWindowButtonDown` |
| 前景 (グリフ) | `Environment.RaftedWindowButtonDownGlyph` |
| 境界線 (グリフ) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>ドキュメント タブ  
ドキュメント タブはタブ チャネル内に存在し、現在どのドキュメントが開いているか、およびどのドキュメントが現在選択されているか、またはアクティブなドキュメントであるかを示します。 ツール ウィンドウも、ユーザーが配置した場合、ドキュメント タブ チャネルにドッキングできます。 この場合、ツール ウィンドウではドキュメント ウィンドウと同じタブの色が使用されます。 ドキュメント ウィンドウの色と常に一致する UI を作成する場合は (テーマの更新や、新しいテーマがインストールされた場合を含む)、これらの色のトークンを参照します。  

![ドキュメント タブ (の赤線)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303 072_DocumentTabRedline")<br />ドキュメント タブ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ドキュメント タブと一致し、テーマの更新や新しいテーマの色を自動的に取得する UI を作成しているすべての場所。 | ... for シェルにテーマの更新がある場合に自動的に変更しない UI。 |

#### <a name="open-document-tabs"></a>開いているドキュメントのタブ  
開いている各ドキュメントには、ドキュメント タブ チャネルに名前を表示するタブがあります。 ドキュメントはバックグラウンドで選択したり開いたりすることができ、タブはこれらの状態を反映します。  

-   選択されているタブは、現在ドキュメント ウェルに表示されているドキュメントを表します。 選択されているタブには、ドキュメント ウェルの上端にまたがって拡張するドキュメントの境界線があります。  

-   背景タブは、現在選択されていないドキュメント タブです。クリックすると、それらは選択されたタブになり、トークン名からすべての背景、境界線、テキストの色を取得します。  

![開いているドキュメント タブ (の赤線)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303 073_OpenDocumentTabRedline")<br />開いているドキュメント タブ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... カスタム ドキュメント タブを作成する場合。 | ... for 一時的な (プレビュー) タブで行います。 |
| | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**選択された状態でフォーカスがあるドキュメント タブ**  

![選択されている場合、ドキュメント タブに重点を置いた](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303 074_SelectedTabFocused")<br />選択された状態でフォーカスがあるドキュメント タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabSelectedGradientTop`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.FileTabSelectedText` |
| 境界線 | `Environment.FileTabSelectedBorder`<br />(背景と同じ色に設定します。) |
| ドキュメントの境界線 | `Environment.FileTabDocumentBorderBackground` |

**選択された状態でフォーカスされていないドキュメント タブ**

![選択された状態でフォーカスされていないドキュメント タブ](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303 075_SelectedTabUnfocused")<br />選択された状態でフォーカスされていないドキュメント タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabInactiveGradientTop`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.FileTabInactiveText` |
| 境界線 | `Environment.FileTabInactiveBorder`<br />(背景と同じ色に設定します。) |
| ドキュメントの境界線 | `Environment.FileTabInactiveDocumentBorderBackground` |

**バック グラウンドのドキュメント タブ: 既定の状態**  

![既定の背景のドキュメント タブ](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303 076_BackgroundTab")<br />既定の背景のドキュメント タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabBackground` |
| 前景 (テキスト) | `Environment.FileTabText` |
| 境界線 | `Environment.FileTabBorder`<br />(背景と同じ色に設定します。) |

**バック グラウンドのドキュメント タブ: ホバー状態**  

![ポインターを合わせると、バック グラウンド ドキュメント タブ](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303 077_BackgroundTabHover")<br />ポインターを合わせると、バック グラウンド ドキュメント タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabHotGradientTop`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.FileTabHotText` |
| 境界線 | `Environment.FileTabHotBorder`<br />(背景と同じ色に設定します。) |

#### <a name="preview-tab"></a>プレビュー タブ  
"Provisional"タブとも呼ばれます。プレビュー タブは、ユーザーがソリューション エクスプローラーのツール ウィンドウで項目をクリックすると、ドキュメント タブ チャネルの右側に表示されます。 プレビュー タブはドキュメントのプレビューとして機能し、ユーザーはドキュメント タブ チャネルの左側でドキュメントを開いたままにできます。 プレビュー タブは一度に 1 つのみ開くことができます。 プレビュー タブには、開いているタブと同様に、背景と選択された状態の両方があり、アクティブな状態でフォーカスされている場合とフォーカスされていない場合があります。  

![[プレビュー] タブ (の赤線)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303 078_PreviewTabRedline")<br />[プレビュー] タブ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... provisional を作成する任意の場所をプレビューし、一部の要素を現在のプレビュー タブの色と一致します。 | あらゆる種類のドキュメントまたは一時的なタブの... (プレビュー)。 |
| | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**フォーカスがある、選択した [プレビュー] タブ**  

![フォーカスがある、選択されたプレビュー タブ](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303 079_PreviewTabFocused")<br />フォーカスがある、選択した [プレビュー] タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedActive` |
| 前景 (テキスト) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| 境界線 | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(背景と同じ色に設定します。) |
| ドキュメントの境界線 | `Environment.FileTabProvisionalSelectedActiveBorder` |

**フォーカスされていない、選択した [プレビュー] タブ**  

![フォーカスされていない、選択されたプレビュー タブ](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303 080_PreviewTabUnfocused")<br />フォーカスされていない、選択した [プレビュー] タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalSelectedInactive` |
| 前景 (テキスト) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| 境界線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| ドキュメントの境界線 | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**背景プレビュー タブ: 既定の状態**  

![既定の背景プレビュー タブ](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303 081_PreviewBackgroundTab")<br />既定の背景プレビュー タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalInactive` |
| 前景 (テキスト) | `Environment.FileTabProvisionalInactiveForeground` |
| 境界線 | `Environment.FileTabProvisionalInactiveBorder`<br />(背景と同じ色に設定します。) |

**背景プレビュー タブ: ホバー状態**  

![ポインターを合わせると、背景プレビュー タブ](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303 082_PreviewBackgroundTabHover")<br />ポインターを合わせると、背景プレビュー タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.FileTabProvisionalHover` |
| 前景 (テキスト) | `Environment.FileTabProvisionalHoverForeground` |
| 境界線 | `Environment.FileTabProvisionalHoverBorder`<br />(背景と同じ色に設定します。) |

#### <a name="document-overflow-button"></a>ドキュメント オーバーフロー ボタン  
ドキュメント オーバーフロー ボタンは、すべてのドキュメント タブに適した垂直スペースが現在の構成にあるかどうかに関係なく、1 つ以上のドキュメントが開いている場合に表示されます。 によって制御されるドキュメント オーバーフロー ドロップダウン メニュー、[コマンド バーのメニュー](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)色、表示と非表示の両方の開いているすべてのドキュメントとかどうかは、すべての開いているドキュメントかに応じて、オーバーフロー グリフの変更の一覧を表示します。タブ チャネルに表示されます。  

![ドキュメント オーバーフロー ボタン (の赤線)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303 083_OverflowRedline")<br />ドキュメント オーバーフロー ボタン (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... をカスタム ドキュメント オーバーフロー ボタンを作成する場合。 | ... の UI はオーバーフロー ボタンに似ています。 |
| | ... for コマンド バー オーバーフロー ボタン。 |

**ドキュメント オーバーフロー ボタン: 既定の状態**  

![既定のドキュメント オーバーフロー ボタン](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303 084_Overflow")<br />既定のドキュメント オーバーフロー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonBackground` |
| 前景 (グリフ) | `Environment.DocWellOverflowButtonGlyph` |
| 境界線 | N/A |

**ドキュメント オーバーフロー ボタン: ホバー状態**

![ポインターを合わせると、ドキュメント オーバーフロー ボタン](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303 085_OverflowHover")<br />ホバー時のドキュメント オーバーフロー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseOverBackground` |
| 前景 (グリフ) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| 境界線 | `Environment.DocWellOverflowButtonMouseOverBorder` |

**ドキュメント オーバーフロー ボタン: 状態の押されました。**  

![キーを押してドキュメント オーバーフロー ボタン](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303 086_OverflowPressed")<br />キーを押してドキュメント オーバーフロー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.DocWellOverflowButtonMouseDownBackground` |
| 前景 (グリフ) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| 境界線 | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>タグ付け  
Visual Studio は、タグ付けをサポートしています。タグ付けにより、ユーザーは追跡のために検索可能なキーワードを宣言できます。 たとえば、プロジェクト マネージャーと開発者は、Team Foundation Server (TFS) を使用して作業項目にタグを付けることができます。 次の表に、タグ自体と、ホバー時および選択済み状態で表示される "アイコンを閉じる" グリフの両方の色の名前を示します。  

![Visual Studio でのタグ付け (の赤線)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303 176_TaggingRedline")<br />Visual Studio でのタグ付け (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for タグ付けをサポートする UI。 | に対する他の種類の UI。 |

#### <a name="tags"></a>Tags  

**タグ: 既定の状態**

![既定のタグ](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303 177_Tag")<br />既定のタグ

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Tag.Background` |
| 前景 (テキスト) | `Tag.Background` |

**タグ: ホバー状態**  

![ポインターを合わせるとタグ付け](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303 178_TagHover")<br />ホバー時のタグ  

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | `Tag.HoverBackground` |
| 前景 (テキスト) | `Tag.HoverBackgroundText` |

**押された状態のタグ。**

![タグが押された](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303 179_TagPressed")<br />押されたタグ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.PressedBackground` |
| 前景 (テキスト) | `Tag.PressedBackgroundText` |

**タグ: 選択された状態**

![タグを選択した](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303 180_TagSelected")<br />選択されたタグ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.SelectedBackground` |
| 前景 (テキスト) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>閉じる (&times;) のグリフをタグ付け

**閉じる (&times;) タグ グリフ: 既定の状態**

![既定の閉じる (&times;) タグ グリフ](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303 181_TagGlyph")<br />既定の閉じる (&times;) のグリフをタグ付け

| 要素 | トークン名:Category.color |
| --- | --- |  
| 背景 | N/A |
| 前景 (グリフ) | `Tag.TagHoverGlyph` |

**閉じる (&times;) タグ グリフ: 状態をホバー**

![閉じる (&times;) ポインターを合わせるとグリフをタグ付け](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303 182_TagGlyphHover")<br />閉じる (&times;) ポインターを合わせるとグリフをタグ付け

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphHoverBackground` |
| 前景 (グリフ) | `Tag.TagHoverGlyphHover` |
| 境界線 | `Tag.TagHoverGlyphHoverBorder` |

**閉じる (&times;) タグ グリフ: 状態の押されました。**

![閉じる押された (&times;) タグ グリフ](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303 183_TagGlyphPressed")<br />閉じる押された (&times;) のグリフをタグ付け

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.TagHoverGlyphPressedBackground` |
| 前景 (グリフ) | `Tag.TagHoverGlyphPressed` |
| 境界線 | `Tag.TagHoverGlyphPressedBorder` |

**終了タグの選択 (&times;) グリフ: 既定の状態**

![既定の選択したタグを閉じる (&times;) グリフ](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303 184_TagSelected")<br />既定の選択したタグを閉じる (&times;) のグリフ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (グリフ) | `Tag.TagSelectedGlyph` |

**終了タグの選択 (&times;) グリフ: 状態をホバー**  

![終了タグの選択 (&times;) ポインターを合わせるとグリフ](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303 185_TagSelectedHover")<br />終了タグの選択 (&times;) グリフ ホバー  


| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphHoverBackground` |
| 前景 (グリフ) | `Tag.TagSelectedGlyphHover` |
| 境界線 | `Tag.TagSelectedGlyphHoverBorder` |

**終了タグの選択 (&times;) グリフ: 状態の押されました。**  

![選択した場合、終了タグが押された (&times;) グリフ](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303 186_TagSelectedPressed")<br />選択した場合、終了タグが押された (&times;) のグリフ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Tag.TagSelectedGlyphPressedBackground` |
| 前景 (グリフ) | `Tag.TagSelectedGlyphPressed` |
| 境界線 | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>ツール ウィンドウ  
Visual Studio 環境で提供しているため、ツール ウィンドウをレプリケートする必要はありません。 ただし、UI が Visual Studio 環境のこの部分と常に一貫性のある状態で表示されるように、ツール ウィンドウで使用する色を活用することができます。  

![ツール ウィンドウ (の赤線)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303 087_ToolWindowRedline")<br />ツール ウィンドウ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ツール ウィンドウを一致させる UI を作成しているすべての場所。 | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

### <a name="tool-window-frame"></a>ツール ウィンドウ フレーム  
Visual Studio のツール ウィンドウはさまざまなタスクに使用され、いくつかの異なる状態の 1 つで配置できます。 ツール ウィンドウが開いている場合、ドキュメント領域の 4 辺のいずれかに割り当てることができます。 ツール ウィンドウは IDE の外部でフローティングさせることもでき、ユーザーの画面内の任意の場所に再配置できます。 フローティング ウィンドウは、常に IDE の一番上に配置されます。 最後に、ツール ウィンドウはドキュメント ウィンドウとしてドッキングし、ドキュメント ウェルのタブとして表示できます。 ドキュメント ウィンドウとしてドッキングされたツール ウィンドウは、ドキュメント ウィンドウのトークン名を使用して一部の色が付けられます。  

![ツール ウィンドウ フレーム (の赤線)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303 088_ToolWindowFrameRedline")<br />ツール ウィンドウ フレーム (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ツール ウィンドウを一致させる UI を作成しているすべての場所。 | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**ドッキングされたツール ウィンドウ**  

![ドッキングされたツール ウィンドウ](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303 089_ToolWindowDocked")<br />ドッキングされたツール ウィンドウ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 境界線 | `Environment.ToolWindowBorder` |

**フォーカスされたツール ウィンドウをフローティング、**

![フォーカスされたツール ウィンドウをフローティング、](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303 090_ToolWindowFocused")<br />フォーカスされたツール ウィンドウをフローティング、

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 境界線 | `Environment.MainWindowActiveDefaultBorder` |

**フローティング、フォーカスされていないツール ウィンドウ**  

![ツール ウィンドウのフローティング、フォーカスされていない](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303 091_ToolWindowUnfocused")<br />フローティング、フォーカスされていないツール ウィンドウ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowBackground` |
| 境界線 | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>ツールボックスのようなウィンドウ
ツールボックスでは、Visual Studio で最もよく使用される一般的なツール ウィンドウの 1 つです。 特別なテーマとスタイルが適用されたツリー コントロールでは本質的にすることをお勧めします。  

![ツールボックスのようなウィンドウ (の赤線)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303 189_ToolboxRedline")<br />ツールボックスのようなウィンドウ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... は常にシェル ツールボックスと一致するツール ウィンドウを設計している場合。 | ... for されていないツールボックス UI のようなものかわからないかどうか、UI に問題が、シェル ツールボックスの色を変更する場合。 |

**ツールボックスのノード: 既定の状態**

![既定のツールボックスの親ノード](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303 190_ToolboxParentNode")<br />既定のツールボックスの親ノード

![既定のツールボックスの子ノード](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303 191_ToolboxChildNode")<br />既定のツールボックスの子ノード

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContent`<br />(見出し) |
| 背景 | `Environment.ToolWindowBackground`<br />(個々 の項目、または場合いない利用可能なコントロールはウィンドウ全体) |
| 境界線 | なし |
| 前景 (グリフ) | `Environment.ToolboxContent` |
| 前景 (テキスト) | `Environment.ToolboxContent` |

**ツールボックスの子ノード: 状態をホバー**

![ツールボックスの子ノードのホバー](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303 192_ToolboxChildNodeHover")<br />ホバー時のツールボックスの子ノード  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolboxContentMouseOver`<br />(個々 の項目のみ) |
| 境界線 | なし |
| 前景 (テキスト) | `Environment.ToolboxContentMouseOver`<br />(個々 の項目のみ) |

**選択したツールボックス ノード: 状態の重点を置いています。**

![フォーカスがある、選択したツールボックスの親ノード](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303 193_ToolboxParentNodeFocused")<br />フォーカスがある、選択したツールボックスの親ノード  

![フォーカスがある、選択したツールボックスの子ノード](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303 194_ToolboxChildNodeFocused")<br />フォーカスがある、選択したツールボックスの子ノード

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |
| 境界線 | `TreeView.FocusVisualBorder`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |
| 前景 (グリフ) | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |
| 前景 (テキスト) | `TreeView.SelectedItemActive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |

**選択したツールボックス ノード: フォーカスされていない状態**

![選択された状態でフォーカスされていないツールボックスの親ノード](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303 195_ToolboxParentNodeUnfocused")<br />選択された状態でフォーカスされていないツールボックスの親ノード  

![選択された状態でフォーカスされていないツールボックスの子ノード](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303 196_ToolboxChildNodeUnfocused")<br />選択された状態でフォーカスされていないツールボックスの子ノード  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |
| 境界線 | なし |
| 前景 (グリフ) | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |
| 前景 (テキスト) | `TreeView.SelectedItemInactive`<br />[Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) カテゴリから |

### <a name="tool-window-title-bar"></a>ツール ウィンドウのタイトル バー  
タイトル バーの境界線のない実際の境界線、タイトル バーの上部には太い線。 フォーカスされていない状態のトークン名は必要はありません。  

![ツール ウィンドウのタイトル バー (の赤線)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303 092_ToolWindowTitleBarRedline")<br />ツール ウィンドウのタイトル バー (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ツール ウィンドウを一致させる UI を作成しているすべての場所。 | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**フォーカスされたタイトル バー**

![フォーカスされたタイトル バー](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303 093_TitleBarFocused")<br />フォーカスされたタイトル バー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarActiveGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.TitleBarActiveText` |
| 境界線 | `Environment.TitleBarActiveBorder`<br />(背景と同じ色に設定します。) |
| ドラッグ ハンドル | `Environment.TitleBarDragHandleActive` |

**フォーカスされていないタイトル バー**  

![フォーカスされていないタイトル バー](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303 094_TitleBarUnfocused")<br />フォーカスされていないタイトル バー

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.TitleBarInactiveGradientBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.TitleBarInactiveText` |
| 境界線 | N/A |
| ドラッグ ハンドル | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>ツール ウィンドウのタイトル バー ボタン  
![タイトル バー ボタン (の赤線)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303 095_TitleBarButtonRedline")<br />タイトル バー ボタン (の赤線)  

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... for ツール ウィンドウのタイトル バーからの色のトークンを使用する UI に表示されるボタン。 | に対する他の場所に表示されるボタン。 |
| | 背景と前景の組み合わせが指定した以外すべて。 |

**タイトル バー ボタンの重点を置いています既定の状態。**

![既定値、タイトル バー ボタンに重点を置いた](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303 096_TitleBarButtonFocused")<br />既定では、フォーカスされたタイトル バー ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (グリフ) | `Environment.ToolWindowButtonActiveGlyph` |
| 境界線 | N/A |

**フォーカスされていないタイトル バー ボタン: 既定の状態**

![既定では、フォーカスされていないタイトル バー ボタン](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303 097_TitleBarButtonUnfocused")<br />既定では、フォーカスされていないタイトル バー ボタン    

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | N/A |
| 前景 (グリフ) | `Environment.ToolWindowButtonInactiveGlyph` |
| 境界線 | N/A |

**タイトル バー ボタンの重点を置いています状態をホバー。**  

![タイトル バー ボタンをポイントしたときに重点を置いて](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303 098_TitleBarButtonFocusedHover")<br />ポインターを合わせると、フォーカスされたタイトル バー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverActive` |
| 前景 (グリフ) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| 境界線 | `Environment.ToolWindowButtonHoverActiveBorder` |

**フォーカスされていないタイトル バー ボタン: ホバー状態**  

![フォーカスされていないタイトル バーのボタンをホバー](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303 099_TitleBarButtonUnfocusedHover")<br />ポインターを合わせると、フォーカスされていないタイトル バー ボタン

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonHoverInactive` |
| 前景 (グリフ) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| 境界線 | `Environment.ToolWindowButtonHoverInactiveBorder` |

**タイトル バー ボタンに重点を置いた: 状態の押されました。**

![タイトル バー ボタンを押してに重点を置いて](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303 100_TitleBarButtonFocusedPressed")<br />フォーカスされたタイトル バーのボタンを押す

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (グリフ) | `Environment.ToolWindowButtonDownActiveGlyph` |
| 境界線 | `Environment.ToolWindowButtonDownBorder` |

**フォーカスされていないタイトル バー ボタン: 状態の押されました。**

![フォーカスされていないタイトル バーのボタンでキーを押して](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303 101_TitleBarButtonUnfocusedPressed")<br />キーを押してフォーカスされていないタイトル バー ボタン  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowButtonDown` |
| 前景 (グリフ) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| 境界線 | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>ツール ウィンドウ タブ  
![ツール ウィンドウ タブ (の赤線)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303 102_ToolWindowTabRedline")<br />ツール ウィンドウ タブ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... ツール ウィンドウを一致させる UI を作成しているすべての場所。 | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**選択された状態でフォーカスのあるツール ウィンドウ タブ**

![選択されている場合、ツール ウィンドウ タブに重点を置いた](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303 103_ToolWindowTabFocused")<br />選択され、フォーカスされたツール ウィンドウ タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (テキスト) | `Environment.ToolWindowTabSelectedActiveText` |
| 境界線 | `Environment.ToolWindowTabSelectedBorder`<br />(背景と同じ色に設定します。) |

**選択された状態でフォーカスされていないツール ウィンドウ タブ**  

![選択された状態でフォーカスされていないツール ウィンドウ タブ](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303 104_ToolWindowTabUnfocused")<br />選択され、フォーカスされていないツール ウィンドウ タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabSelectedTab` |
| 前景 (テキスト) | `Environment.ToolWindowTabSelectedText` |
| 境界線 | `Environment.ToolWindowTabSelectedBorder`<br />(背景と同じ色に設定します。) |

**背景ツール ウィンドウ タブ: 既定の状態**

![既定の背景ツール ウィンドウ タブ](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303 105_ToolWindowBackgroundTab")<br />既定の背景ツール ウィンドウ タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(グラデーションは、Visual Studio 2013 で同じ色の値に設定を停止します)。 |
| 前景 (テキスト) | `Environment.ToolWindowTabText` |
| 境界線 | `Environment.ToolWindowTabBorder` |

**背景ツール ウィンドウ タブ: ホバー状態**

![ポインターを合わせると、背景ツール ウィンドウ タブ](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303 106_ToolWindowBackgroundTabHover")<br />ホバー時の背景ツール ウィンドウ タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(グラデーションは、Visual Studio 2013 で同じ色の値に設定を停止します)。 |
| 前景 (テキスト) | `Environment.ToolWindowTabMouseOverText` |
| 境界線 | `Environment.ToolWindowTabMouseOverBorder`<br />(背景と同じ色に設定します。) |  

### <a name="auto-hide-tabs"></a>自動非表示タブ  

![自動非表示タブ (の赤線)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303 107_AutoHideRedline")自動非表示タブ (の赤線)

| 使用してください. | 使用しないでください. |
| --- | --- |
| ... 自動非表示ツール ウィンドウ タブと一致させる UI を作成しているすべての場所。 | ... 場合に自動的に変更しない ui シェルにテーマの更新。 |

**自動非表示タブ: 既定の状態**  

![既定の自動非表示タブ](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303 108_AutoHideTab")<br />既定の自動非表示タブ

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.AutoHideTabText` |
| 境界線 | `Environment.AutoHideTabBorder` |

**自動非表示タブ: ホバー状態**

![ポインターを合わせると、自動的に隠す タブ](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303 109_AutoHideTabHover")<br />ホバー時の [自動非表示] タブ  

| 要素 | トークン名:Category.color |
| --- | --- |
| 背景 | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(グラデーション境界は、このトークンのテーマの UI で使用されないのはされます)。 |
| 前景 (テキスト) | `Environment.AutoHideTabMouseOverText` |
| 境界線 | `Environment.AutoHideTabMouseOverBorder` |
