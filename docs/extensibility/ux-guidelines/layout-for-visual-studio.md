---
title: "Visual Studio のレイアウト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
caps.latest.revision: 2
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 2
---
# Visual Studio のレイアウト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio のダイアログ ボックスの大半は [ユーティリティのダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), 、ダイアログ ボックスに従って規格は、unthemed [Windows デスクトップ\] ダイアログのレイアウトの原則](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)します。 Visual Studio を移動するときに UI を更新するの目立つダイアログで、ある新しいデザイン エクスペリエンスの製品を定義するように確立します。 これら [テーマが適用されたダイアログのレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) テーマが適用された外観にする場合します。  
  
##  <a name="BKMK_UtilityDialogLayout"></a> ユーティリティのダイアログのレイアウト  
  
-   ユーティリティのダイアログ ボックスですべてのコントロールは、左上から開始され、下方向にフローする必要があります。  
  
-   決して center 上のコントロール広い領域を入力するためのダイアログ。  
  
-   ダイアログのすべてのテキストの環境フォントを使用します。 ビジュアルの仕様を記述する場合は、特定のフォントとサイズを選択する代わりに、環境フォントを指定します。 「[環境フォント](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont)」を参照してください。  
  
-   職人気質の品質の目標をサポートするために、一貫したコントロールの間隔と配置を使用します。  
  
-   ダイアログ ボックスより多くのコントロールやコントロールの一意の並置からより複雑になります。 これらの複雑な状況では、論理的な流れを解析するためにコントロールのグループ化の間の十分な領域を許可します。  
  
### ユーティリティのダイアログのレイアウトの例  
 すべてのディメンションは、ピクセル単位で表されます。  
  
 ![Dialog spacing for labels above controls](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801\-a\_UtilitySpacingAbove")  
  
 **図 a 08.01: 間隔ユーティリティ ダイアログ コントロールの上にラベルをするためのガイドライン**  
  
 ![Dialog spacing for labels to the left of controls](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801\-b\_UtilitySpacingLeft")  
  
 **コントロールの左にラベルが付いたユーティリティに関するダイアログ ボックスの図の 08.01 b: 間隔のガイドライン**  
  
### レイアウトの詳細  
  
#### 余白  
  
-   すべてのダイアログ ボックスでは、すべての端に 12 ピクセルの境界線が必要です。  
  
-   グループ フレーム内の余白は、フレームの端から 9 ピクセルをする必要があります。  
  
-   タブ コントロール内の余白は、タブ コントロールの左端から 6 のピクセルにする必要があります。  
  
#### コマンド ボタン  
  
-   コマンド ボタンは、コンテンツではなく、ダイアログ フレームを操作します。 右側下部に配置し、設定ボタンが互いに分離するための十分な変数領域を持つ必要があります。  
  
-   ダイアログ ボックス内で動作する水平方向のボタンがある場合は、代替のコマンド ボタンの構成は、右上にある垂直スタックです。 参照してください [内部コマンド ボタン](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) 以下です。  
  
-   コマンド ボタン \(下部左\/ダイアログの中央\) の左側の領域は、操作のダイアログ コントロールの「バンド」の一部と見なされます。 唯一の領域を侵害する必要がありますが、タスク全体またはダイアログに関連付けられたヘルプ リンクします。  
  
-   コマンド ボタンには、75 x 23 ピクセルを指定する必要があります。  
  
-   コマンド ボタンは、6 ピクセルの間隔にする必要があります。  
  
 ![Basic button alignment](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801\-c\_ButtonAlign")  
  
 **図 08.01\-c: 基本的なボタンの配置**  
  
#### ラベル  
  
-   左揃えにすべてのラベル。  
  
-   ラベル コントロールの上に配置の場合は、これらが左揃えに下にあるコントロールを正確に使用し、ラベルの下部にあるが、その他のコントロール \(コンボ ボックスなど\) の 5 ピクセルにする必要があります。  
  
-   コントロールの左側にあるラベルの場合は、ラベルと入力コントロールの幅の最小値は、10 ピクセルです。 暗黙の 2 番目の列は、テキスト ボックス、コンボ ボックス、またはその他のコントロールを揃えるため確立する必要があります。  
  
-   ラベルは、文の場合し、後にコロンです。 「[テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle)」を参照してください。  
  
#### コントロール間の間隔  
 コントロールをある程度スタックです。 積み上のコントロールの間隔の絶対ガイドラインはありません。 コントロール間の精度は、ダイアログ ボックスの間で若干異なります。 推奨される間隔は、垂直コントロールのラベルの組、20 ピクセルと水平コントロールのラベルのペアに 9 ピクセルです。 水平方向のペアの最小のコントロールの間隔は、6 ピクセルです。  
  
 ![Recommended distance between controls](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801\-d\_ControlDistance")  
  
 **コントロール間の距離に関する推奨事項を図 08.01\-d:**  
  
#### コントロールのインデント  
 コントロールが入れ子になっていると、水平方向のラベルでは通常、コントロールを上記の左端に内部のコントロールを整列します。  
  
 ![Nested control alignment](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801\-e\_ControlAlign")  
  
 **図 08.01\-e: 入れ子になったコントロールの配置**  
  
#### コントロールの幅  
 テキスト ボックスまたはその他の類似するコントロールの幅は、フィールドの平均入力よりも短いにする必要があります。 平均の英語のワードは、5 つの文字です。 たとえば、長いパス名を必要とするテキスト ボックスを水平方向のレイアウトが許可されている限りにするプラットフォーム名では、最も長いデータの長さだけのドロップダウン リストを中です。  
  
#### ヘルパー テキスト  
  
-   ダイアログ ボックスでは、ダイアログ ボックスの目的に関する詳細を提供するヘルパー テキストを表示できます。 これは通常、上部にある位置し、1 ~ 2 文を指定できます。  
  
-   行の長さを解析し、読み取りユーザー向けに快適な幅にする必要があります。 中規模のダイアログは、以内 550 ピクセルにする必要があります。  
  
####  <a name="BKMK_InteriorCommandButtons"></a> 内部コマンド ボタン  
 さらに複雑なダイアログは、内部コントロール独自関連のボタン、ダイアログのコミット ボタンが含まれているを与える可能性があるがあります。  
  
-   内部の垂直方向の配置 \(列\) ボタンの場合に使用する **\[ok\]**\/**キャンセル** は右下隅では水平方向です。  
  
-   内部の水平方向の配置 \(行\) ボタンの場合に使用する **\[ok\]**\/**キャンセル** は、画面の右上隅の垂直方向です。 このような状況はまれです。  
  
-   内部のボタンのサイズのサイズと一致する 75 x 23 ピクセルの標準ボタンのサイズのターゲットとなる **OK**\/**キャンセル** ボタンの可能な場合です。 ボタンのラベル、ボタンの標準のボタンのサイズを超える場合は、そのセットの他のボタンは、その幅広いサイズに沿っていなければなりません。  
  
 ![Horizontal OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801\-f\_HorizOKCan")  
  
 **図の 08.01 f: 垂直方向の内部プロパティを持つ水平方向の \[ok\]\/\[キャンセル\] ボタン**  
  
 ![Vertical OK and Cancel buttons](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801\-g\_VertOKCan")  
  
 **垂直方向の \[ok\]\/\[キャンセル\] 持つ水平内部ボタンの図の 08.01 g:**  
  
#### \[参照...\] ボタン  
 **\[参照...\]** 次のテキスト ボックスのボタンは、\[参照を詳しく必要があります 完全に省略記号を含みます。 容量が厳しいかが複数ある **\[参照...\]** 、ボタン、画面上のボタンは、省略記号に短縮できます。  
  
##  <a name="BKMK_ThemedDialogLayout"></a> テーマが適用されたダイアログのレイアウト  
 Visual Studio でテーマが適用されたダイアログでは、外観が明るいと、複数の空白を提供します。 文字体裁では、強調とより多くの行間隔やフォント サイズおよび重みのバリエーションの 1 つを提供する、目的の詳細を提供します。 可能であれば、chrome とタイトル バー削減されたり、削除します。 これらのダイアログ ボックスのレイアウトは、この基本的なパターンに従う必要があります。  
  
1.  ダイアログ ボックスの背景は白です。  
  
2.  中間値グレー表示に 1 ピクセル ルール枠線があります。  
  
3.  ダイアログのタイトルを不要になったでは、タイトル バーの位置しますが、視覚的な効果をより大きなポイント サイズでを提供します。 \(フォント サイズのセクションを参照して [テキストのスタイル](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).\)  
  
4.  ラベル、説明など、追加のテキストと組み合わせると **環境フォント \+ 太字**します。  
  
5.  内側の列はグレー表示になって 1 ピクセルのルールで区切られます。  
  
6.  既定のリンクがあるアンダー スコアなし。 ホバーと押された状態、色の変更とアンダー スコアがあります。  
  
7.  コミット ボタン \(のような **\[ok\]**\/**キャンセル**\) 右下隅に配置します。  
  
### テーマが適用されたダイアログのレイアウトの例  
 ![Themed dialog layout](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801\-h\_ThemedDialog")  
  
 **テーマが適用されたダイアログの図の 08.01 h:**  
  
 ![Themed dialog dimensions](~/extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801\-i\_ThemedDialogDimensions")  
  
 **図の 08.01 i: テーマが適用されたダイアログ – ディメンション**  
  
 ![Themed dialog fonts](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801\-j\_ThemedDialogFonts")  
  
 **図の 08.01 j: テーマが適用されたダイアログ ボックス フォント**  
  
 ![Themed dialog colors](~/extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801\-k\_ThemedDialogColors")  
  
 **図の 08.01 k: テーマが適用されたダイアログ ボックスの色**  
  
## 参照  
 [Visual Studio のアプリケーション パターン](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)   
 [コントロール \(Windows\)](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)   
 [ダイアログ ボックス \(Windows\)](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742499\(v=vs.85\).aspx)