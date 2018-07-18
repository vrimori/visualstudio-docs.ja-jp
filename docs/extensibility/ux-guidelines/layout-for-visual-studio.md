---
title: Visual Studio のレイアウト |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e26caa6e47f0f2ee2a20611cf12e166832e007b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31149017"
---
# <a name="layout-for-visual-studio"></a>Visual Studio のレイアウト
Visual Studio のダイアログ ボックスの大半は[ユーティリティ ダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)、ダイアログ ボックスに従ってその標準は、unthemed [Windows デスクトップ ダイアログのレイアウトの基本原則](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)です。 移動に伴い Visual Studio に UI を更新するより高いのダイアログ ボックスのある新しいデザイン エクスペリエンスの製品を定義するように確立します。 これら[テーマが適用されたダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)テーマの外観にする場合します。  
  
##  <a name="BKMK_UtilityDialogLayout"></a> ユーティリティのダイアログのレイアウト  
  
-   ユーティリティ ダイアログ内のすべてのコントロールを左上から開始し、下方向にフローします。  
  
-   決してセンター上のコントロール大きな領域を塗りつぶすためのダイアログ。  
  
-   環境フォントを使用して、すべてのダイアログ テキスト。 ビジュアルの仕様を記述する場合は、特定のフォントとサイズを選択する代わりに、環境フォントを指定します。 参照してください[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)です。  
  
-   職人気質の品質の目標をサポートするために、一貫性のあるコントロールの間隔と配置を使用します。  
  
-   ダイアログ ボックスより多くのコントロールやコントロールの一意の juxtaposition からより複雑になることができます。 これらの複雑な状況では、論理的な流れを解析するためにコントロールのグループ化の間の十分な領域を許可します。  
  
### <a name="utility-dialog-layout-examples"></a>ユーティリティのダイアログのレイアウトの例  
 すべてのディメンションは、ピクセルとして表されます。  
  
 ![コントロールの上にラベルのダイアログの間隔](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **図 a 08.01: コントロールの上にラベルを持つユーティリティ ダイアログに関するガイドラインの間隔**  
  
 ![コントロールの左のラベルのダイアログの間隔](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **コントロールの左にラベルが付いたユーティリティ ダイアログ図 08.01-b: 間隔のガイドライン**  
  
### <a name="layout-details"></a>レイアウトの詳細  
  
#### <a name="margins"></a>余白  
  
-   すべてのダイアログ ボックスでは、すべてのエッジを囲む 12 ピクセルの境界線が必要です。  
  
-   グループ フレーム内の余白は、フレームの端から 9 ピクセルにする必要があります。  
  
-   タブ コントロール内の余白は、タブ コントロールの左端から 6 のピクセルにする必要があります。  
  
#### <a name="command-buttons"></a>コマンド ボタン  
  
-   コマンド ボタンは、コンテンツではなく、ダイアログ フレームを操作します。 右側下部に配置し、ボタンは互いに分離の設定は、上の変数十分な領域が必要があります。  
  
-   ダイアログ ボックス内で動作する水平方向のボタンがある場合は、代替コマンド ボタンの構成は、右上にある垂直スタックです。 参照してください[内部コマンド ボタン](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)以下です。  
  
-   コマンド ボタン (低い左/ダイアログの中央) の左側の領域は、操作のダイアログ コントロールの「バンド」の一部と見なされます。 その領域を妨害することだけは、タスク全体またはダイアログに関連するヘルプ リンクです。  
  
-   コマンド ボタンは、75 x 23 ピクセルである必要があります。  
  
-   コマンド ボタンは、分解 6 ピクセルにする必要があります。  
  
 ![基本的なボタンの配置](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
 **図 08.01-c: 基本的なボタンの配置**  
  
#### <a name="labels"></a>ラベル  
  
-   左揃えにするすべてのラベル。  
  
-   ラベル コントロールの上に配置の場合を左揃え下にあるコントロールを正確とラベルの下部にあるが、その他のコントロール (コンボ ボックスなど) の 5 ピクセルにする必要があります。  
  
-   コントロールの左側にあるラベル、ラベルと入力コントロールの幅の最小値は 10 ピクセルです。 テキスト ボックス、コンボ ボックス、またはその他のコントロールを配置、暗黙の 2 番目の列を確立する必要があります。  
  
-   ラベルは、文の場合し、後にコロンがします。 参照してください[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)です。  
  
#### <a name="distance-between-controls"></a>コントロール間の距離  
 コントロールをある程度スタックします。 積み上げコントロール間の間隔の絶対ガイドラインはありません。 コントロール間テンションは、ダイアログ ボックスの間で若干異なります。 推奨される間隔は 20 ピクセル垂直コントロールのラベルのペアの水平/コントロールのラベルのペアの 9 ピクセルです。 水平方向のペアのコントロールの最小間隔は、6 ピクセルです。  
  
 ![コントロール間の距離をお勧め](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **コントロール間の距離に関する推奨事項を図 08.01-d:**  
  
#### <a name="control-indentation"></a>コントロールのインデント  
 コントロールが入れ子になっていると、水平方向のラベルでは通常、コントロールを上記の左端に内部のコントロールを整列します。  
  
 ![コントロールの配置を入れ子になった](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **図 08.01-e: 入れ子になったコントロールの配置**  
  
#### <a name="control-width"></a>コントロールの幅  
 テキスト ボックス、またはその他の同様のコントロールの幅は、フィールドの平均入力以内にする必要があります。 平均の英語のワードは、5 つの文字です。 たとえば、テキスト ボックスが長いパス名が必要ですが、水平方向のレイアウトが許可されている限りにする必要がありますプラットフォーム名では、最も長いデータの長さだけのドロップダウン リストを中にします。  
  
#### <a name="helper-text"></a>ヘルパー テキスト  
  
-   ダイアログ ボックスでは、ダイアログ ボックスの目的に関する詳細を提供するヘルパー テキストを表示できます。 これは通常、最上位にあり、1 ~ 2 文にします。  
  
-   行の長さは、解析を読み取るユーザー向けに快適な幅にする必要があります。 中規模のダイアログは、個 550 ピクセルにする必要があります。  
  
####  <a name="BKMK_InteriorCommandButtons"></a> 内部コマンド ボタン  
 複雑なダイアログは、内部のコントロールはダイアログのコミットのボタンがある場所に影響を与える可能性があります独自関連のボタンがあります。  
  
-   使用するときに内部の垂直方向の配置 (列) の各ボタン **[ok]**/**キャンセル**右下隅の水平方向に並びます。  
  
-   使用するときに内部の水平方向の配置 (行) の各ボタン **[ok]**/**キャンセル**は右上隅の垂直方向します。 このような状況はあまり一般的です。  
  
-   内部のボタンのサイズが、標準のボタンのサイズのサイズと一致する、75 x 23 ピクセルの対象と **[ok]**/**キャンセル**可能な場合はボタンをクリックします。 ボタンのラベル、ボタンの標準のボタンのサイズを超える場合、そのセット内の他のボタンの位置より広いと、そのサイズに合わせます。  
  
 ![水平方向の [ok] と [キャンセル] ボタン](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
 **図 08.01-f: 垂直方向の内部プロパティを持つ水平方向の [ok]/[キャンセル] ボタン**  
  
 ![垂直方向の [ok] と [キャンセル] ボタン](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
 **図の 08.01 g: 水平内部プロパティを持つボタン垂直方向の [ok]/[キャンセル]**  
  
#### <a name="browse-button"></a>[参照...]ボタン  
 **[参照...]** ボタンのテキスト ボックスに続く必要があります「参照...」省略記号を含む、完全に略さずです。 容量が厳しいかが複数ある場合 **[参照...]** ボタン、画面上のボタンは、省略記号に短縮できます。  
  
##  <a name="BKMK_ThemedDialogLayout"></a> テーマが適用されたダイアログのレイアウト  
 Visual Studio でテーマが適用されたダイアログでは、外観が明るいと、複数の空白を提供します。 文字体裁エンファシスとより多くの行間隔やフォント サイズ、および重みのバリエーションが提供して、目的の詳細を提供します。 可能であれば、chrome とタイトル バー削減されたり削除します。 これらのダイアログ ボックスのレイアウトは、この基本的なパターンに従う必要があります。  
  
1.  ダイアログ ボックスの背景が白いです。  
  
2.  中間値灰色で 1 ピクセル ルール枠線があります。  
  
3.  不要になったダイアログのタイトルは、タイトル バーに置かれたが、視覚的な効果やエンファシスでポイントのサイズを大きくを提供します。 (セクションを参照して、フォント サイズで[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle))。  
  
4.  ラベル、説明など、追加のテキストと組み合わせる必要があります**環境フォント + 太字**です。  
  
5.  内部の列は明るい灰色で 1 ピクセル ルールで区切られます。  
  
6.  既定のリンクがあるアンダー スコアなし。 ホバー時および押された状態の色の変更とアンダー スコアがあります。  
  
7.  ボタンをコミット (と同様に**OK**/**キャンセル**) 右下隅に配置します。  
  
### <a name="themed-dialog-layout-examples"></a>テーマが適用されたダイアログのレイアウトの例  
 ![テーマが適用されたダイアログのレイアウト](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **図の 08.01 h: テーマが適用されたダイアログ**  
  
 ![テーマが適用されたダイアログのディメンション](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **図の 08.01 i: テーマが適用されたダイアログのディメンション**  
  
 ![テーマが適用されたダイアログのフォント](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **図の 08.01 j: テーマが適用されたダイアログのフォント**  
  
 ![テーマが適用されたダイアログの色](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **図の 08.01 k: テーマが適用されたダイアログの色**  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [コントロール (Windows)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [ダイアログ ボックス (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)