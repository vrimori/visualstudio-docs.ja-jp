---
title: Visual Studio のレイアウト |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9ffd8fa53b42092678075a68dbe655b8e7c653
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930844"
---
# <a name="layout-for-visual-studio"></a>Visual Studio のレイアウト
Visual Studio のダイアログ ボックスの大半は[ユーティリティ ダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout)、そのに従って標準のダイアログ ボックスは、unthemed [Windows デスクトップ ダイアログのレイアウトの原則](/windows/desktop/uxguide/win-dialog-box)します。 Visual Studio の UI の更新を移動するとき、目立つのダイアログ ボックスの一部に製品を定義するとエクスペリエンスを確立する新しい設計になっています。 これら[テーマが適用されたダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout)テーマの外観を与えます。  
  
##  <a name="BKMK_UtilityDialogLayout"></a> ユーティリティのダイアログのレイアウト  
  
-   ユーティリティ ダイアログ内のすべてのコントロールは、上/左に起動し、下方向にフローする必要があります。  
  
-   決して center 上のコントロール広い領域を入力するためのダイアログ。  
  
-   ダイアログのすべてのテキストを環境フォントを使用します。 ビジュアルの仕様を記述する場合は、特定のフォントとサイズを選択する代わりに、環境フォントを指定します。 参照してください[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)します。  
  
-   職人気質の品質の目標をサポートするために、一貫した制御間隔と配置を使用します。  
  
-   ダイアログ ボックスは、多数のコントロールと、コントロールの一意の juxtaposition のどちらか一方または両方からより複雑ななることができます。 これらの複雑な状況で論理的な流れを解析するために、コントロールのグループ化の間の十分な領域を許可します。  
  
### <a name="utility-dialog-layout-examples"></a>ユーティリティのダイアログのレイアウトの例  
 すべてのディメンションは、ピクセルとして表現されます。  
  
 ![コントロール上のラベルのダイアログの間隔](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801 a_UtilitySpacingAbove")  
  
 **図 a 08.01:コントロールの上のラベルが付いたユーティリティに関するダイアログ ボックスの間隔のガイドライン**  
  
 ![コントロールの左のラベルのダイアログの間隔](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801 b_UtilitySpacingLeft")  
  
 **図の 08.01 b:コントロールの左にラベルが付いたユーティリティに関するダイアログ ボックスの間隔のガイドライン**  
  
### <a name="layout-details"></a>レイアウトの詳細  
  
#### <a name="margins"></a>余白  
  
-   すべてのダイアログ ボックスでは、すべての端に 12 ピクセルの境界線が必要です。  
  
-   グループのフレーム内の余白が 9 ピクセル フレームの端からあります。  
  
-   タブ コントロール内の余白は、タブ コントロールの端から 6 ピクセルである必要があります。  
  
#### <a name="command-buttons"></a>コマンド ボタン  
  
- コマンド ボタンは、コンテンツではなく、ダイアログ枠に対して動作します。 右下に配置され、設定、ボタンが互いに分離する上記変数十分な領域があります。  
  
- ダイアログ ボックス内で動作する、横並びのボタンがある場合は、代替のコマンド ボタンの構成は、右上にある垂直スタックです。 参照してください[内部コマンド ボタン](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)以下。  
  
- (低い左/センター ダイアログ ボックスの) コマンド ボタンの左側の領域は、ダイアログの操作のコントロールの「域外」の一部と見なされます。 唯一の領域を侵害する必要がありますは、タスク全体またはダイアログに関連するヘルプ リンクです。  
  
- コマンド ボタンは、75 x 23 ピクセルである必要があります。  
  
- 6 ピクセル離れたコマンド ボタンがあります。  
  
  ![基本的なボタンの配置](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801 c_ButtonAlign")  
  
  **図 08.01-c:基本的なボタンの配置**  
  
#### <a name="labels"></a>ラベル  
  
-   左揃えにすべてのラベル。  
  
-   コントロール上に位置するラベルでは、これらが左揃えに下にあるコントロールを正確とラベルの下部にあるが、その他のコントロール (コンボ ボックスなど) の 5 ピクセルにする必要があります。  
  
-   コントロールの左側に配置されているラベルの場合は、ラベルと入力コントロールの幅の最小値は、10 ピクセルです。 テキスト ボックス、コンボ ボックス、またはその他のコントロールを整列させるため、暗黙の 2 番目の列が確立されます。  
  
-   ラベルは、文のケースし、後にコロンです。 参照してください[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)します。  
  
#### <a name="distance-between-controls"></a>コントロール間の距離  
 コントロールをある程度スタックします。 積み上げコントロール間の間隔の絶対ガイドラインはありません。 コントロール間こわばったりは、ダイアログ ボックスの間で若干異なります。 推奨される間隔は 20 ピクセル垂直コントロールのラベルの組、水平コントロールのラベルのペアの 9 ピクセルです。 水平方向のペアのコントロールの最小間隔は、6 ピクセルです。  
  
 ![コントロール間の距離をお勧めします](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801 d_ControlDistance")  
  
 **図 08.01-d:コントロール間の距離に関する推奨事項**  
  
#### <a name="control-indentation"></a>コントロールのインデント  
 コントロールは入れ子になったときに、ラベルは、通常、コントロールを上記の左端と水平方向に内部のコントロールを配置します。  
  
 ![コントロールの配置を入れ子になった](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801 e_ControlAlign")  
  
 **図 08.01-e:入れ子になったコントロールの配置**  
  
#### <a name="control-width"></a>コントロールの幅  
 テキスト ボックスまたは他の同様のコントロールの幅は、フィールドの平均入力より長くする必要があります。 平均の英語版の word には、5 つの文字です。 たとえば、長いパス名を必要とするテキスト ボックスを水平方向のレイアウトが許可されている限りにするプラットフォームの名前は長最長を入力できますが、必ずのドロップダウン リストを中にします。  
  
#### <a name="helper-text"></a>ヘルパー テキスト  
  
-   ダイアログ ボックスでは、ダイアログ ボックスの目的に関する情報を提供するヘルパー テキストを表示できます。 これは通常、最上位にされ、1 ~ 2 文を指定できます。  
  
-   行の長さを解析し、読み取りユーザー向けに快適な幅があります。 中規模のダイアログ幅個 550 ピクセルがあります。  
  
####  <a name="BKMK_InteriorCommandButtons"></a> 内部コマンド ボタン  
 複雑なダイアログは、内部のコントロールは独自関連なボタンは、ダイアログのコミット ボタンがある場所に影響する可能性があります。  
  
- 内部の垂直方向の配置 (列) ボタンを使用して **[ok]**/**キャンセル**は右下隅で水平方向に並びます。  
  
- 内部の水平方向の配置 (行) ボタンを使用して **[ok]**/**キャンセル**は右上隅にある垂直方向に並びます。 このような状況はまれです。  
  
- 内部のボタンのサイズのサイズと一致する 75 x 23 ピクセルの標準ボタンのサイズをターゲットする必要があります**OK**/**キャンセル**ボタンの可能な場合。 ボタンのラベル、ボタンの標準ボタンのサイズを超える場合は、そのセット内の他のボタンはその幅のサイズと一致します。  
  
  ![水平方向の [ok] と [キャンセル] ボタン](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801 f_HorizOKCan")  
  
  **図の 08.01 f:垂直内部水平方向の [ok]/[キャンセル] ボタン**  
  
  ![垂直方向の [ok] と [キャンセル] ボタン](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801 g_VertOKCan")  
  
  **図の 08.01 g:垂直方向の [ok]/[キャンセル] で内部横並びのボタン**  
  
#### <a name="browse-button"></a>[参照...]ボタン  
 **[参照...]** ボタンのテキスト ボックスに続く必要があります「参照…」省略記号を含む、完全に現れます。 容量が厳しいかが複数ある **[参照...]** 画面で、ボタンのボタンは、省略記号を削減できます。  
  
##  <a name="BKMK_ThemedDialogLayout"></a> テーマが適用されたダイアログのレイアウト  
 Visual Studio のテーマが適用されたダイアログでは、軽量の外観を与えるし、複数の空白を提供します。 詳細の強調しより多くの行間隔とフォント サイズや重量のバリエーションを提供する目的の文字体裁を提供します。 可能であれば、chrome とタイトル バーを削減または削除されています。 これらのダイアログ ボックスのレイアウトは、この基本パターンに従う必要があります。  
  
1.  ダイアログ ボックスの背景は白です。  
  
2.  中間値灰色でルールの 1 ピクセルの枠線があります。  
  
3.  ダイアログのタイトルを不要になったは、タイトル バーに配置が、視覚的な効果とより大きなポイント サイズの強調を提供します。 (フォント サイズ」セクションを参照してください[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)。)。  
  
4.  ラベルは、説明など、追加のテキストと組み合わせると**環境フォント + 太字**します。  
  
5.  内部の列はグレー表示に 1 ピクセルのルールで区切られます。  
  
6.  既定のリンクには、アンダー スコアはあるありません。 ホバーと押された状態の色の変更とアンダー スコアがあります。  
  
7.  コミット ボタン (など **[ok]**/**キャンセル**) 部分の右下隅に配置します。  
  
### <a name="themed-dialog-layout-examples"></a>テーマが適用されたダイアログのレイアウトの例  
 ![テーマが適用されたダイアログのレイアウト](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801 h_ThemedDialog")  
  
 **図の 08.01 h:テーマが適用されたダイアログ**  
  
 ![テーマが適用されたダイアログのディメンション](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801 i_ThemedDialogDimensions")  
  
 **図の 08.01 i:テーマが適用されたダイアログのディメンション**  
  
 ![テーマが適用されたダイアログのフォント](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801 j_ThemedDialogFonts")  
  
 **図の 08.01 j:テーマが適用されたダイアログのフォント**  
  
 ![テーマが適用されたダイアログの色](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801 k_ThemedDialogColors")  
  
 **図の 08.01 k:テーマが適用されたダイアログの色**  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [コントロール (Windows)](/windows/desktop/uxguide/controls)   
 [ダイアログ ボックス (Windows)](/windows/desktop/uxguide/win-dialog-box)