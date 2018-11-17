---
title: Visual Studio のコモン コントロール パターン |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 111323a416f8388fe553824e83edd5f48b3201d4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817530"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio のコモン コントロール パターン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> コモン コントロール  
  
### <a name="overview"></a>概要  
 一般的なコントロールは、Visual Studio でのユーザー インターフェイスの大部分を構成します。 Visual Studio インターフェイスで使用される最も一般的なコントロールが従う必要があります、 [Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)します。 このドキュメントは、Visual Studio に固有の特殊な状況やその Windows ガイドラインの強化の詳細について説明します。  
  
#### <a name="common-controls-in-this-topic"></a>このトピックの「一般的なコントロール  
  
-   [スクロール バー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [入力フィールド](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [コンボ ボックスとドロップダウン リスト](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [チェック ボックス](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [オプション ボタン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [グループのフレーム](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [ボタンやハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [ツリー ビュー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Visual スタイル  
 最初にコントロールのスタイルを設定するときに考慮することは、テーマの UI でコントロールを使用するかどうか。 標準的な ui コントロールのないテーマの UI、従う必要があります[標準の Windows デスクトップ スタイル](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)、re テンプレートでないと既定のコントロールの外観で表示する必要があります。  
  
-   **標準 (ユーティリティ) ダイアログ ボックス:** ないテーマが適用されました。 Re テンプレートはしないでください。 基本的なコントロールのスタイルの既定値を使用します。  
  
-   **ツール ウィンドウ、ドキュメント エディター、デザイン サーフェイスおよびテーマが適用されたダイアログ ボックス:** 色サービスを使用して特殊化されたテーマの表示を使用します。  
  
###  <a name="BKMK_Scrollbars"></a> スクロール バー  
 スクロール バーが従う必要があります[Windows のスクロール バーの一般的な相互作用パターン](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx)それらによって増幅コンテンツについてなど、コード エディターでしない限り、します。  
  
###  <a name="BKMK_InputFields"></a> 入力フィールド  
 一般的な操作の動作に従って、[テキスト ボックスについては、Windows デスクトップ](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   入力フィールドは、ユーティリティのダイアログ ボックスでないスタイルを設定する必要があります。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマが適用された入力フィールドは、テーマが適用されたダイアログとツール ウィンドウでのみ使用する必要があります。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   読み取り専用フィールド (アクティブ) の既定の前景は灰色 (無効) バック グラウンドになります。  
  
-   フィールドが必要に必要な**\<必要 >** 内にウォーターマークとして。 まれな状況では、以外の背景の色を変更する必要がありますできません。  
  
-   エラーの検証: を参照してください[通知と Visual Studio の進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   入力フィールドは、順番に表示されます、ウィンドウの幅に合わせてしないにも、任意のパスなどの長いフィールドの長さと一致には、コンテンツに合わせてサイズに設定する必要があります。 長さ フィールドに文字数が許可されているかの制限事項のユーザーを示す値があります。  
  
     ![正しくない入力フィールド コントロールの幅](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")   
     **正しくない入力フィールドの長さ: 名前はこれだけの時間になります可能性はほとんどありません。**  
  
     ![入力フィールド コントロールの幅を修正](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")   
     **入力フィールドの長さを修正: 入力フィールドは、必要なコンテンツの妥当な幅。**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> コンボ ボックスとドロップダウン リスト  
 一般的な操作の動作に従って、[ドロップダウン リストとコンボ ボックスの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ、re テンプレートは、コントロールの操作を行います。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマの UI でコンボ ボックスとドロップダウン リスト コントロールの標準的なテーマに従います。  
  
#### <a name="layout"></a>レイアウト  
 コンボ ボックスとドロップダウン リストは、順番に表示されます、ウィンドウの幅に合わせてしないにも、任意のパスなどの長いフィールドの長さと一致には、コンテンツに合わせてサイズにする必要があります。  
  
 ![不適切なドロップ&#45;レイアウト ダウン](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")  
  
 **ドロップダウン コントロールの不適切なフィールドの長さ**  
  
 ![適切なドロップ&#45;レイアウト ダウン](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707 04_CorrectDropDownLayout")  
  
 **ドロップダウン コントロールの適切なフィールド長**  
  
###  <a name="BKMK_CheckBoxes"></a> チェック ボックス  
 一般的な操作の動作に従って、[チェック ボックスについては、Windows デスクトップ](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ、re テンプレートは、コントロールの操作を行います。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマの UI では、チェック ボックスは、コントロールの標準的なテーマに従います。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   チェック ボックスとの対話は、ダイアログを表示または別の領域に移動する必要がありますしないでください。  
  
-   チェック ボックスをテキストの最初の行のベースラインに揃えます。  
  
     ![正しくないチェック ボックスの配置](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")   
     **正しくないチェック ボックスの配置: チェック ボックスが、テキストの中央に配置します。**  
  
     ![チェック ボックスの配置を修正](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")   
     **チェック ボックスの配置を修正: チェック ボックスは、テキストの最初の行のベースラインに揃えられます。**  
  
###  <a name="BKMK_RadioButtons"></a> オプション ボタン  
 一般的な操作の動作に従って、[ラジオ ボタンの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
 ユーティリティ、ダイアログのないラジオ ボタンをスタイルの操作を行います。 基本のスタイルを組み込みコントロールを使用します。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
 オプションの選択肢を囲むグループ フレームを使用する必要はありません。  
  
###  <a name="BKMK_GroupFrames"></a> グループのフレーム  
 一般的な操作の動作に従って、[グループ フレームの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
 ユーティリティのダイアログ ボックスでスタイル グループ フレームいない操作を行います。 基本のスタイルを組み込みコントロールを使用します。  
  
#### <a name="layout"></a>レイアウト  
  
-   緊密なレイアウトでのグループの区別を維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
-   1 つのコントロールのグループのフレームを使用しないでください。  
  
-   グループのフレームのコンテナーではなく水平方向の規則を使用できる場合があります。  
  
##  <a name="BKMK_TextControls"></a> テキスト コントロール  
  
### <a name="labels"></a>ラベル  
  
#### <a name="active-label-state"></a>アクティブなラベルの状態  
  
##### <a name="utility-standard-dialogs"></a>ユーティリティ (標準) ダイアログ ボックス)  
  
-   一般に、コントロールのラベルの Windows デスクトップのガイダンスに従ってください。  
  
-   ユーティリティのダイアログ ボックスで太字でない、標準的な環境のフォントとテキストの色のラベルが表示されます。 参照してください[Visual Studio のフォントと書式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)します。  
  
-   省略記号は、ラベルを常に従う必要があります。  
  
##### <a name="signature-themed-dialogs"></a>署名 (テーマが適用された) ダイアログ ボックス)  
 ラベル コントロールには、太字やライト グレー可能性があります。  
  
#### <a name="disabled-label-state"></a>ラベルを無効になっている状態  
 ラベルは、関連付けられているコントロールの外観を反映する必要があります。 たとえば、関連付けられたコントロールが無効になっている場合ラベルが表示される灰色、無効になります。 これは、通常、OS によって処理され、特別な処理は必要ありません。  
  
#### <a name="dynamic-labels"></a>動的ラベル  
 現在の選択に基づく動的ラベル変更します。 可能であれば、マスター/詳細レイアウトで動的ラベルのユーザー情報が表示されますが、具体的な選択とされません一般的な情報に関連することを理解するために使用します。  
  
 ![動的なコンテンツで使用される動的ラベル](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702 01_DynamicLabel")  
  
 **動的コンテンツと共に使用される動的ラベルの例**  
  
#### <a name="instructional-text"></a>説明のテキスト  
 一部のインターフェイス要素またはを実行するには、どのアクションを示すために UI の目的を理解するユーザーを支援する指示テキストを享受できます。  
  
-   説明のテキストは、ダイアログの上部にある最も一般的な複雑なコントロールのグループ化する命令を提供する他の領域に表示できます。  
  
-   説明のテキストでは、非対話型ですが、ヘルプ トピックへのハイパーリンクを含めることができます。  
  
-   説明のテキストを使用して、慎重に行いのみ必要なときにします。  
  
##### <a name="formatting"></a>書式設定  
 説明のテキストには、環境フォント、(テーマではない) 標準のコントロールのテキスト必要があります。 参照してください[Visual Studio のフォントと書式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)します。  
  
 説明のテキストの記述について詳しくは、次を参照してください。 [UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)します。  
  
 ![説明のテキストの書式設定](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702 02_InstructionalTextFormatting")  
  
 **Visual Studio ダイアログでの説明テキスト**  
  
#### <a name="informational-text"></a>情報テキスト  
 情報テキストは、ユーザーの追加情報が表示されるテキストです。 静的または動的、または通知として使用される可能性があります。 読み取り専用では常に、動的なテキストが読み取り専用のテキスト フィールドなどのコントロールのコンテナーで配置されて、ユーザーが情報をコピーする機能の便利な場合は、します。  
  
##### <a name="dynamic-context-specific-text"></a>動的な (コンテキストに固有) テキスト  
 動的な情報のテキストは、ユーザーがフォーカスを切り替える場合など、状況に応じて変わります。 常にではありませんが、多くの場合、動的なコンテンツは動的ラベルと組み合わせて使用します。  
  
 ![動的な情報テキスト](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702 03_InformationalDynamicText")  
  
 **動的な情報テキストをコンテキストに応じて変更します。**  
  
##### <a name="formatting"></a>書式設定  
 読み取り専用のテキスト フィールドを表示する 2 つの方法があります。 画面 (上記参照) またはグループのフレームまたはテキスト ボックスなどの別のコントロール内に含まれるか、UI に直接します。 いずれかが、状況に応じて正しいです。 読み取り専用情報を表示する方法を決定するフィーチャー デザイナーの責任です。  
  
 テキストは、読み取り専用テキスト ボックス内で使用できます。 これは、一般を示します、コンテンツを選択し、コピーした編集することはできません。  
  
 ![読み取り用に書式設定情報テキスト&#45;フィールドのみ](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702 04_InformationalFormatting")  
  
 **情報テキストの読み取り専用フィールドの書式設定**  
  
#### <a name="watermarks"></a>透かし  
 表現は同じである可能性があります、透かしと説明のテキスト間の差はコントロールまたはウィンドウが空でないし、常に表示される説明テキストは、コンテンツを含む透かしが置き換えられます。  
  
 ウィンドウまたはコントロールが空の場合、透かしを使用する必要があります。 これらの領域を設定するために必要があると指定され、ドラッグ ソースなどの関連するウィンドウを開くアクション リンクを含めることができます。  
  
##### <a name="visual-style"></a>Visual スタイル  
  
- 透かしは、ウィンドウ内で水平方向に中央揃えにする必要があります。  
  
- 透かしは、左揃えではない中央揃えする必要があります。  
  
- ウォーターマークが垂直方向に中央揃えまたは領域の上部近くに配置されました。 領域の上部にある場合は、必要があります十分な領域の上、レベルのウォーターマークが目立つように。  
  
- 使用して、`Environment.GrayText`トークンと標準環境フォントの色。 ハイパーリンクは共有の標準のハイパーリンクのトークンを使用する必要があります: `Environment.PanelHyperlink`、 `Environment.PanelHyperlinkHover`、 `Environment.PanelHyperlinkPressed`、および`Environment.PanelHyperlinkDisabled`します。  
  
- バック グラウンドで透かしを選択することはできません。  
  
- 可能であれば、開始するユーザーを支援するウォーターマークのリンクを含めます。  
  
  ![デザイナー ウィンドウ内のテキストの透かし](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702 05_Watermark1")  
  
  ![ツール ウィンドウ内のテキストの透かし](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702 06_Watermark2")  
  
  **Visual Studio でのウォーターマーク テキストの例**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> ボタンやハイパーリンク  
  
### <a name="overview"></a>概要  
 ボタンやリンクのコントロール (ハイパーリンク) に従う必要があります[ハイパーリンクの基本的な Windows デスクトップ ガイダンス](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx)wording、サイズ変更、および間隔は、使用するためです。  
  
### <a name="choosing-between-buttons-and-links"></a>ボタンまたはリンクの選択  
 これまでは、アクションのボタンを使用して、ナビゲーション用に予約されたハイパーリンク。 すべてのケースでボタンを使用することが、ボタンやリンクがいくつかの条件でより交換されることになるよう Visual Studio でのリンクのロールが拡張されました。  
  
 コマンド ボタンを使用する場合。  
  
- 主要なコマンド  
  
- 入力を収集するために使用するウィンドウを表示するか、セカンダリ コマンドにある場合でも、選択を行う  
  
- 破壊的なまたは元に戻せない操作  
  
- ウィザードとページ フロー内のコミットメントのボタン  
  
  ツール ウィンドウ、コマンド ボタンを避けるため、ラベルの 2 つ以上の単語が必要な場合またはします。 リンクは、長いラベルを持つことができます。  
  
  リンクを使用する場合。  
  
- 別のウィンドウ、ドキュメント、または web ページへの移動  
  
- 長いラベルまたは操作の目的を説明する短い文を必要とする状況  
  
- アクションには、破壊的または元に戻せないことに、ボタンで、UI に過は緊密なスペース  
  
- 除外を強調しての状況でセカンダリ コマンドが多数のコマンド  
  
#### <a name="examples"></a>使用例  
 ![ステータス メッセージに続く情報バー コマンド リンク](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703 01_CommandLinkInfobar")  
  
 **ステータス メッセージに続く情報バーで使用されるコマンドへのリンク**  
  
 ![CodeLens ポップアップで使用されているリンク](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703 02_LinksInCodeLens")  
  
 **CodeLens ポップアップで使用されているリンク**  
  
 ![セカンダリ コマンドとして使用されているリンク](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")  
  
 **リンク ボタンがあまり注意を引き付けるようセカンダリ コマンドの使用**  
  
### <a name="common-buttons"></a>一般的なボタン  
  
#### <a name="text"></a>テキスト  
 書き込みのガイドラインに従って[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
##### <a name="standard-dialogs"></a>標準ダイアログ  
 Visual Studio でのほとんどのボタンは、標準ダイアログで表示され、スタイル設定しない必要があります。 オペレーティング システムによって決定される、標準のボタンの外観が反映されます。  
  
##### <a name="themed"></a>テーマが適用されました。  
 場合によっては、ボタンをスタイル設定された UI 内で使用可能性があり、これらのボタンは適切にスタイル設定する必要があります。 参照してください[ダイアログ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)テーマが適用されたコントロールについて。  
  
### <a name="special-buttons"></a>特殊なボタン  
  
#### <a name="browse-buttons"></a>参照してください. ボタン  
 **[参照...]** ボタンは、グリッド、ダイアログ、およびツール ウィンドウおよびその他のモードレスの UI 要素で使用されます。 コントロールに値を入力することで、ユーザーを支援するピッカーが表示されます。 このボタンは、長短の 2 つのバリエーションがあります。  
  
 ![長い&#91;を参照しています.&#93;ボタン](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703 04_BrowseLong")  
  
 **長い [参照...] ボタン**  
  
 ![省略記号を短い&#45;のみ&#91;を参照しています.&#93;ボタン](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703 05_BrowseShort")  
  
 **省略記号のみの短い [...] ボタン**  
  
 省略記号のみの短い ボタンを使用するとき。  
  
- 1 つ以上の時間を使用する必要がある場合 **[参照...]** など、いくつかのフィールドの参照を許可するときに、ダイアログにボタンをクリックします。 使用して、短い **[...]** 混乱にこのような状況によって作成されたアクセス キーを回避するために各ボタン (**& 参照**と**B (& r)** と同じダイアログ ボックスで)。  
  
- 密 ダイアログ ボックスで、または長い ボタンを配置する適切な場所がありません。  
  
- 場合は、ボタンは、グリッド コントロールに表示されます。  
  
  ボタンの使用に関するガイドライン:  
  
- アクセス キーを使用しません。 キーボードを使用してアクセスするには、ユーザーは、隣接するコントロールからタブする必要があります。 タブ オーダーがいっぱいに表示されるフィールドの直後に、[参照] ボタンがあることなどであることを確認します。 最初の期間の下にアンダー スコアを使用しないでください。  
  
- Microsoft Active Accessibility (MSAA) を設定**名前**プロパティを**を参照しています.** (省略記号) を含む画面を読者は、「ドット ドット ドット」や「期間の期間の期間」はなく"Browse"として。 つまり、設定の管理対象のコントロール、 **AccessibleName**プロパティ。  
  
- 省略記号を使用しないでください **[...]** 参照アクション以外のすべてのボタンをクリックします。 たとえば、必要がある場合、 **[新規作成]** ボタンしますが、ダイアログ ボックスが再設計する必要があります、テキストのための十分なスペースはありません。  
  
##### <a name="sizing-and-spacing"></a>サイズ変更との間隔  
 ![サイズ変更&#91;を参照しています.&#93;ボタン](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703 06_BrowseSizing")  
  
 **[参照...] ボタンのサイズ変更**  
  
 ![間隔&#91;を参照しています.&#93;ボタン](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703 07_BrowseSpacing")  
  
 **間隔 [参照...] ボタン**  
  
#### <a name="graphical-buttons"></a>グラフィカルなボタン  
 いくつかのボタンを常にグラフィカル イメージを使用し、領域を節約し、ローカライズの問題を回避するテキストを含めることはありません。 フィールドの選択およびその他の並べ替え可能なリストでよく使用されます。  
  
> [!NOTE]
>  ユーザーは、これらのボタン (アクセス キーはありません) にタブで、そのため、適切な順序で配置する必要があります。 スクリーン リーダーは、ボタンの操作を正しく解釈するために必要なアクションには、ボタンの name プロパティをマップします。  
  
|||  
|-|-|  
|追加|![グラフィカルな [追加] ボタン](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703 08_ButtonAdd")|  
|削除|![「削除」ボタンがグラフィカル](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703 09_ButtonRemove")|  
|すべて追加します。|![グラフィカルな [すべて追加] ボタン](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703 10_ButtonAddAll")|  
|すべて削除します。|![グラフィカルな すべて削除"ボタン](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703 11_ButtonRemoveAll")|  
|上へ|![グラフィカルな 上へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703 12_ButtonMoveUp")|  
|下へ移動|![グラフィカルな 下へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703 13_ButtonMoveDown")|  
|削除|![グラフィカルな「削除」ボタン](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703 14_ButtonDelete")|  
  
##### <a name="sizing-and-spacing"></a>サイズ変更との間隔  
 グラフィカルなボタンは短いバージョンの場合と同じですサイズ変更、 **[参照...]。** ボタン (26 x 23 ピクセル単位)。  
  
 ![ボタンの透明色が表示されずに](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")  
  
 **ボタンの透明色が表示されずにグラフィック イメージの外観**  
  
### <a name="hyperlinks"></a>ハイパーリンク  
 ハイパーリンクは、ヘルプ トピック、モーダル ダイアログ ボックスで、またはウィザードを開くなどのナビゲーション ベースの操作にも適しています。 コマンドのハイパーリンクを使用する場合、UI に表示され、顕著な変更が常に表示されます。 一般に、アクション (保存、Cancel、および削除など) へのコミット操作より伝達されますボタンを使用します。  
  
#### <a name="writing-style"></a>文書のスタイル  
 に従って、[ユーザー インターフェイスのテキストについては、Windows デスクトップ](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)します。 「について詳細について、」を使用しない「指示 me 機能の詳細について、」または「このヘルプを表示する」言い回しです。 代わりに、質問をしてヘルプ コンテンツに応答する主要な質問の観点からのヘルプ リンク テキスト。 たとえば、"**サーバー エクスプ ローラーにサーバーを追加する方法でしょうか**"。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ハイパーリンクは常に使用する必要があります[The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)します。 ハイパーリンクが正しく書式設定されていない、する場合はアクティブな際の赤で点滅またはアクセスした後に別の色が表示されます。  
  
-   リンクは、完全な文章内文のフラグメントをなど、ウォーターマークがない限り、状態を置くコントロールに下線を含めないでください。  
  
-   ポインターを合わせると下線は表示されません。 代わりに、リンクがアクティブであるユーザーにフィードバックは、わずかな色の変更と適切なリンクのカーソルは。  
  
##  <a name="BKMK_TreeViews"></a> ツリー ビュー  
  
### <a name="overview"></a>概要  
 ツリー ビューでは、親と子グループに複雑な整理する方法の一覧を提供します。 ユーザーは、展開したり、表示、または基になる子アイテムを非表示に親グループを折りたたんだりできます。 さらにアクションを提供する、ツリー ビュー内の各項目を選択できます。  
  
 このトピックでは、許容される使用方法、適切に設計、およびツリー ビューの機能について説明します。  
  
#### <a name="in-this-topic"></a>このトピックの内容  
  
-   [Visual スタイル](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [相互作用](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Visual スタイル  
  
#### <a name="expanders"></a>展開コントロール  
 ツリー ビュー コントロールは、Windows と Visual Studio で使用される expander のデザインに準拠する必要があります。 各ノードは、表示、または基になるアイテムを非表示に expander コントロールを使用します。 Expander コントロールを使用して、Windows と Visual Studio 内の別のツリー ビューを発生する可能性があるユーザーに一貫性が提供します。  
  
 ![ツリー ビュー コントロールを修正](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")  
  
 **Expander コントロールを使用して、ツリー ビュー ノードの適切なスタイルが正しい。**  
  
 ![正しくない ツリー ビュー ノード](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705 2_TreeViewIncorrect1")  
  
 **ツリー ビュー ノードの不適切なスタイルの正しくない:**  
  
#### <a name="selection"></a>選択ツール  
 ツリー ビュー内のノードを選択すると、強調表示がツリー ビュー コントロールの幅いっぱいに展開する必要があります。 これにより、ユーザーが選択した項目を明確に識別できます。 選択範囲の色は、現在の Visual Studio のテーマを反映します。  
  
 ![ツリー ビュー コントロールを修正](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705 1_TreeViewCorrect")  
  
 **正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。**  
  
 ![正しくない ツリー ビューの強調表示](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705 3_TreeViewIncorrect2")  
  
 **正しくない: 選択したノードの強調表示では、ツリー ビュー コントロールの幅全体は適合しません。**  
  
#### <a name="icons"></a>アイコン  
 項目間の相違点を特定する視覚的に支援している場合、ツリー ビュー コントロールのアイコンを使用のみする必要があります。 一般に、アイコンは、アイコンが要素の種類を区別するために情報を保持する異種のリストでのみ使用する必要があります。 同種のリストのアイコンを使用してノイズとして頻繁に表示できるし、避ける必要があります。 その場合はグループのアイコン (親) には、その中の項目の種類を伝達できます。 この規則の例外は、アイコンは動的でありの状態を示すために使用がかどうかになります。  
  
#### <a name="scroll-bars"></a>スクロール バー  
 コンテンツがツリー ビュー コントロール内に収まる場合、スクロール バーを非表示常にする必要があります。 スクロール可能なウィンドウを非表示、または半透明にして、フォーカスのあるウィンドウのツリー ビューを格納しているときに表示またはツリーのホバー時にそれ自体を表示するスクロール バーとして受け入れ可能です。  
  
 ![ツリー ビューをスクロール バーのある](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705 4_Scrollbars")  
  
 **内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平スクロール バーが表示されます。**  
  
###  <a name="BKMK_TreeViewInteractions"></a> 相互作用  
  
#### <a name="context-menus"></a>コンテキスト メニュー  
 ツリー ビュー ノードには、コンテキスト メニューのサブメニューで開くオプションを表示できます。 通常、これは、ユーザーが項目を右クリックしてまたは選択された項目を持つ Windows キーボードでメニュー キーを押したときに発生します。 ノードがフォーカスでが選択されていることは重要です。 これにより、ユーザーに属しているサブメニュー項目を識別できます。  
  
 ![選択されているツリー ノードとコンテキスト メニュー](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705 5_ContextMenu")  
  
 **項目をユーザーに通知するコンテキスト メニューの向上のフォーカスの生成がどの項目が選択されています。**  
  
#### <a name="keyboard"></a>キーボード  
 ツリー ビュー アイテムを選択し、キーボードを使用してノードの展開/折りたたみ機能が提供する必要があります。 これにより、ナビゲーションが、当社のアクセシビリティ要件を満たしていること。  
  
##### <a name="tree-view-control"></a>ツリー ビュー コントロール  
 Visual Studio のツリー コントロールでは、共通のキーボード ナビゲーションを従う必要があります。  
  
-   **上矢印:** ツリーを移動することで項目を選択します。  
  
-   **下矢印:** ツリーの下位に移動して項目を選択します。  
  
-   **右矢印:** ツリー内のノードを展開します。  
  
-   **左矢印:** ツリー ノードを折りたたみます  
  
-   **キーを入力:** を開始する負荷は、選択した項目の実行  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (ツリー ビューおよびグリッド ビュー)  
 Trid コントロールは、グリッド内のツリー ビューを含む複雑なコントロールです。 展開、折りたたみ、およびツリー内で移動加え、次のツリー ビューと同じキーボード コマンドを尊重する必要があります。  
  
- **右矢印:** ノードを展開します。 ノードが展開された後、右側の最も近い列への移動を続行する必要があります。 ナビゲーションは、行の最後に停止する必要があります。  
  
- **タブ:** 右側の近くのセルに移動します。  行の末尾には、ナビゲーションは、次の行を続けます。  
  
- **Shift + Tab:** 左側に最も近いセルに移動します。  行の先頭には、ナビゲーションは、前の行の右端のセルを続けます。  
  
  ![Visual Studio での Trid コントロール](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705 6_Trid")  
  
  **Visual Studio での trid コントロール**

