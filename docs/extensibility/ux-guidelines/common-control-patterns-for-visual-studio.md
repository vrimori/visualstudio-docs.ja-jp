---
title: "Visual Studio の一般的なコントロール パターン | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Visual Studio の一般的なコントロール パターン
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> コモン コントロール  
  
### 概要  
 コモン コントロールは、Visual Studio のユーザー インターフェイスの大部分を構成します。 Visual Studio インターフェイスで使用される最も一般的なコントロールが従う必要があります、 [Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)します。 このドキュメントでは、Visual Studio に固有ですし、特別な状況やこのような Windows ガイドラインの強化の詳細について説明。  
  
#### このトピックでのコモン コントロール  
  
-   [スクロール バー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [入力フィールド](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [コンボ ボックスとドロップダウン リスト](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [チェック ボックス](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [オプション ボタン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [グループ フレーム](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [ボタンやハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [ツリー ビュー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### 視覚スタイル  
 まず最初にテーマが適用された UI にコントロールを使用するかどうかが、コントロールのスタイル設定を検討してください。 標準的な UI のコントロールをテーマにした非 UI、従う必要があります [標準の Windows デスクトップ スタイル](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), 、つまり、re テンプレートではありませんが、既定のコントロールの外観で表示されます。  
  
-   **標準 \(ユーティリティ\) ダイアログ ボックス:** テーマが適用されたされません。 いない re テンプレートを実行します。 基本的なコントロールのスタイルの既定値を使用します。  
  
-   **ツールの windows、文書の編集者、デザイン サーフェイスおよびテーマが適用されたダイアログ ボックス:** 色サービスを使用して、特殊なテーマが適用された外観を使用します。  
  
###  <a name="BKMK_Scrollbars"></a> スクロール バー  
 スクロール バーが従う必要があります [Windows のスクロール バーの一般的な相互作用パターン](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) を使用して詳しくコンテンツ情報など、コード エディターでない限りです。  
  
###  <a name="BKMK_InputFields"></a> 入力フィールド  
 一般的な操作の動作に従って、 [テキスト ボックスの Windows デスクトップのガイドラインについて](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx)します。  
  
#### 視覚スタイル  
  
-   入力フィールドをユーティリティのダイアログ ボックスで書式設定されていない必要があります。 コントロールに組み込みの基本的なスタイルを使用します。  
  
-   テーマが適用された入力フィールドは、テーマが適用されたダイアログおよびツール ウィンドウでのみ使用する必要があります。  
  
#### 特殊な相互作用  
  
-   読み取り専用フィールドは、\(アクティブ\) の既定の前景がグレー \(無効\) バック グラウンドでがあります。  
  
-   フィールドが必要に必要な **\< 必要 \>** そこに含まれるウォーターマークとして。 まれな状況では、以外の背景の色を変更する必要がありません。  
  
-   エラーの検証: を参照してください [通知と Visual Studio の進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   入力フィールドに任意のパスなどの長いフィールドの長さと一致することや、これらは、表示される、ウィンドウの幅に合わせてが、コンテンツに合わせてサイズを変更する必要があります。 長さがフィールドでは文字数は許可に制限を示す値をユーザーにあります。  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **正しくない入力フィールドの長さ: 名前をこの長さになることが可能性は高くありません。**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **入力フィールドの長さを修正します。 入力フィールドが予期されるコンテンツの適切な幅。**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> コンボ ボックスとドロップダウン リスト  
 一般的な操作の動作に従って、 [ドロップ ダウン リストやコンボ ボックスの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx)します。  
  
#### 視覚スタイル  
  
-   ユーティリティのダイアログ ボックスでは、コントロールしない re テンプレートを処理します。 コントロールに組み込みの基本的なスタイルを使用します。  
  
-   テーマが適用された UI は、コンボ ボックスとドロップダウンに、コントロールの標準的なテーマに従います。  
  
#### レイアウト  
 コンボ ボックスとドロップダウンは、任意のパスなどの長いフィールドの長さと一致することや、これらは、表示される、ウィンドウの幅に合わせてが、コンテンツに合わせてサイズ必要があります。  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **ドロップダウン コントロールの正しくないフィールドの長さ**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **ドロップダウン コントロールの適切なフィールドの長さ**  
  
###  <a name="BKMK_CheckBoxes"></a> チェック ボックス  
 一般的な操作の動作に従って、 [のチェック ボックスについては、Windows デスクトップ](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx)します。  
  
#### 視覚スタイル  
  
-   ユーティリティのダイアログ ボックスでは、コントロールしない re テンプレートを処理します。 コントロールに組み込みの基本的なスタイルを使用します。  
  
-   テーマが適用された UI は、チェック ボックスは、コントロールの標準的なテーマに従います。  
  
#### 特殊な相互作用  
  
-   チェック ボックスとの対話は、ダイアログをポップアップ表示したり、別の領域に移動する必要がありますしないでください。  
  
-   テキストの最初の行の基準を持つチェック ボックスを配置します。  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **正しくないチェック ボックスの配置: チェック ボックスが、テキストの中央に配置します。**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **チェック ボックスの配置を修正します。\] チェック ボックスは、テキストの最初の行のベースラインに揃えられます。**  
  
###  <a name="BKMK_RadioButtons"></a> オプション ボタン  
 一般的な操作の動作に従って、 [のオプション ボタンの Windows デスクトップのガイドラインについて](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx)します。  
  
#### 視覚スタイル  
 ユーティリティのダイアログ ボックスでスタイル オプション ボタンではない操作を行います。 コントロールに組み込みの基本的なスタイルを使用します。  
  
#### 特殊な相互作用  
 オプションの選択肢を囲むグループ フレームを使用する必要はありません。  
  
###  <a name="BKMK_GroupFrames"></a> グループ フレーム  
 一般的な操作の動作に従って、 [グループ フレームの Windows デスクトップのガイドラインについて](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx)します。  
  
#### 視覚スタイル  
 ユーティリティのダイアログ ボックスでスタイル グループ フレームをしていない操作を行います。 コントロールに組み込みの基本的なスタイルを使用します。  
  
#### レイアウト  
  
-   緊密なレイアウトでのグループの区別を維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
-   1 つのコントロールのグループのフレームを使用しないでください。  
  
-   グループのフレームのコンテナーではなく水平方向の規則を使用できる場合があります。  
  
##  <a name="BKMK_TextControls"></a> テキスト コントロール  
  
### ラベル  
  
#### アクティブなラベルの状態  
  
##### ユーティリティ \(標準\) ダイアログ ボックス\)  
  
-   一般のコントロールのラベルの Windows デスクトップの指示に従います。  
  
-   ユーティリティのダイアログ ボックスで、通常、標準的な環境のフォントとテキストの色のラベルが表示されます。 「[フォントおよび Visual Studio の書式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)」を参照してください。  
  
-   省略記号は、ラベルを常に従う必要があります。  
  
##### 署名 \(テーマが適用された\) ダイアログ ボックス\)  
 Label コントロールには、太字や明るい灰色可能性があります。  
  
#### 無効になっているラベルの状態  
 ラベルは、関連付けられているコントロールの外観を反映する必要があります。 たとえば、関連付けられたコントロールが無効になっている場合、ラベルが表示されます灰色\] と \[無効。 これは、通常は、OS によって処理され、特別な処理は必要ありません。  
  
#### 動的ラベル  
 現在の選択に基づく動的ラベル変更します。 可能であればは、マスター\/詳細レイアウトで動的ラベルを使用して、ユーザーが表示される情報は、特定の選択と一般的な情報に関連するを理解するのに役立ちます。  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **動的コンテンツと共に使用される動的ラベルの例**  
  
#### 説明のテキスト  
 一部のインターフェイス要素の恩恵説明テキストのユーザーが UI の目的を理解するために、または実行する操作が示されます。  
  
-   説明のテキストは、ダイアログ ボックスの上部にある最も一般的な複雑なコントロールのグループ化する命令を与えるには、他の領域で表示されることができます。  
  
-   説明のテキストが非対話型ヘルプ トピックへのハイパーリンクを含めることができます。  
  
-   限り注意して、説明のテキストを使用して必要な場合です。  
  
##### 書式設定  
 説明のテキストは、環境フォント、標準的な \(非をテーマにした\) コントロールのテキストにする必要があります。 「[フォントおよび Visual Studio の書式設定](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)」を参照してください。  
  
 説明テキストを書き込む方法の詳細については、「 [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)します。  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Visual Studio\] ダイアログでの説明テキスト**  
  
#### 情報テキスト  
 情報テキストは、ユーザーの追加情報が表示されるテキストです。 静的または動的、または通知として使用されていることがあります。 読み取り専用では常に、動的テキストを読み取り専用のテキスト フィールドなどのコントロール コンテナーに配置する必要がありますをユーザーに情報をコピーする機能を与えるに便利である場合。  
  
##### 動的な \(コンテキスト固有\) テキスト  
 動的な情報テキストをユーザーがフォーカスを切り替える場合など、状況に応じて変更します。 必ずではありませんが多くの場合、動的なコンテンツは動的なラベルと組み合わせて使用します。  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **動的な情報テキストは、コンテキストによって異なります。**  
  
##### 書式設定  
 読み取り専用のテキスト フィールドを表示する 2 つの方法があります。 画面 \(上記参照\)、UI 上で直接いずれか、またはグループのフレームまたはテキスト ボックスなどの別のコントロール内に含まれます。 状況に応じていずれかです。 読み取り専用情報を表示する方法については、フィーチャー デザイナーの責任です。  
  
 テキストは、読み取り専用テキスト ボックス内で使用できます。 これは、通常を示しますコンテンツを選択し、コピーした編集することはできません。  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **読み取り専用フィールド用の情報テキストの書式設定**  
  
#### 透かし  
 契約条項の内容は同じになる場合があります、透かしと説明のテキストの違いは、コントロールまたはウィンドウが空ではないと、常に表示される説明のテキストは、透かしがコンテンツに置き換えられますことです。  
  
 ウィンドウまたはコントロールが空の場合は、透かしを使用してください。 領域を作成するために必要なを示しており、ドラッグ ソースなどの関連するウィンドウを開く操作のリンクを含めることができます。  
  
##### 視覚スタイル  
  
-   ウォーターマークは、ウィンドウ内で水平方向に中央揃えする必要があります。  
  
-   ウォーターマークは、左揃えではない中央に配置する必要があります。  
  
-   ウォーターマークは、可能性があります垂直方向に中央揃えまたは領域の上部付近に配置します。 領域の上部近くにある場合があるのに十分な領域の上透かしが目立つように。  
  
-   使用して、 `Environment.GrayText` トークンと標準環境フォントの色。 ハイパーリンクは、共有の標準のハイパーリンクのトークンを使用する必要があります: `Environment.PanelHyperlink`, 、`Environment.PanelHyperlinkHover`, 、`Environment.PanelHyperlinkPressed`, 、および `Environment.PanelHyperlinkDisabled`です。  
  
-   ページの背景に透かしを選択することはできません。  
  
-   可能であれば、開始ユーザーを支援しますウォーターマークのリンクが含まれてください。  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **Visual Studio でのウォーターマーク テキストの例**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> ボタンやハイパーリンク  
  
### 概要  
 ボタンやリンクのコントロール \(ハイパーリンク\) が従う必要があります [ハイパーリンクの基本的な Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) 語句、サイズ変更、および間隔は、使用するためです。  
  
### ボタンまたはリンクの選択  
 これまでは、アクションのボタンを使用し、ナビゲーション用に予約されたハイパーリンクします。 常に、ボタンを使用することがありますが、ボタンやリンクがいくつかの条件でより交換されることになるように、リンクのロールを Visual Studio で展開されています。  
  
 コマンド ボタンを使用する場合。  
  
-   主要なコマンド  
  
-   入力を収集するために使用するウィンドウを表示するか、セカンダリ コマンドがある場合でも、選択を行う  
  
-   破壊的なまたは回復不可能な操作  
  
-   ウィザードおよびページ フロー内のコミットメント ボタン  
  
 ツール ウィンドウでコマンド ボタンを避けるため、ラベルの 2 つ以上の単語が必要になった場合。 リンク ラベルが長いことができます。  
  
 リンクを使用するとき。  
  
-   別のウィンドウ、ドキュメント、または web ページへの移動  
  
-   長いラベルまたは操作の目的を説明する短い文を必要とする状況  
  
-   アクションが破壊または元に戻すことがないことに、ボタンで、UI に圧倒と緊密なスペース  
  
-   除外を強調してセカンダリ コマンドの状況で多くのコマンドが存在します。  
  
#### 例  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **ステータス メッセージに続く情報バーに使用されているコマンドのリンク**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **CodeLens ポップアップで使用されているリンク**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **セカンダリ コマンドのボタンがあまり注意を引き付けが使用されているリンク**  
  
### 一般的なボタン  
  
#### テキスト  
 書き込みのガイドラインに従って [UI text and terminology](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)します。  
  
#### 視覚スタイル  
  
##### 標準ダイアログ  
 Visual Studio でのほとんどのボタンは、標準的なダイアログ ボックスで表示され、スタイルいない必要があります。 オペレーティング システムによって指定されているとおり、ボタンの標準的な外観を示すもの必要があります。  
  
##### テーマが適用されました。  
 場合によっては、スタイルを指定した UI 内でボタンを使用することがあり、これらのボタンは適切にスタイル指定する必要があります。 参照してください [ダイアログ ボックス](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) テーマが適用されたコントロールについてです。  
  
### 特殊なボタン  
  
#### 参照. ボタン  
 **\[参照...\]** ボタンはグリッド、ダイアログ、およびツール ウィンドウおよび他のモードレスの UI 要素で使用します。 コントロールに値を満たすために、ユーザーを支援するピッカーが表示されます。 このボタンは、長い形式と短いの 2 つのバリエーションがあります。  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **時間の長い \[参照...\] ボタン**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **省略記号のみの短い \[...\] ボタン**  
  
 省略記号のみの短い\] ボタンを使用する場合。  
  
-   1 つ以上長を使用する必要がある場合 **\[参照...\]** など、いくつかのフィールドが参照できるように、ダイアログにボタンをクリックします。 短いを使用して **\[...\]** ごとに、このような状況で作成されたアクセス キーの混乱を避けるためにボタン \(**\(& a\) 参照** と **B および rowse** 同じダイアログ ボックスで\)。  
  
-   緊密な\] ダイアログ ボックスで、または長いボタンを配置する適切な場所はありません。  
  
-   場合は、ボタンは、グリッド コントロールに表示されます。  
  
 ボタンの使用に関するガイドライン:  
  
-   アクセス キーを使用しません。 キーボードを使用してアクセスするには、ユーザー必要があります、隣接するコントロールから表示されるタブ。 タブ オーダーがであるようなことに合わせてフィールドの直後に、\[参照\] ボタンがあることを確認します。 最初の期間の下にアンダー スコアを使用しないでください。  
  
-   Microsoft Active Accessibility \(MSAA\) を設定 **名** プロパティを **\[参照\]** \(省略記号\) を含むため、画面を読者は、「三点リーダー」または「期間前期」はなく「参照」として 設定は、マネージ コントロール、 **AccessibleName** プロパティです。  
  
-   省略記号を使用しないで **\[...\]** 参照アクション以外の目的\] ボタンをクリックします。 たとえば、必要がある場合、 **\[新規作成\]** ボタンしますが、ダイアログ ボックスが再設計する必要がありますし、テキスト、十分なスペースはありません。  
  
##### サイズおよび間隔  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **\[参照...\] のサイズ変更 ボタン**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **\[参照...\] の間隔 ボタン**  
  
#### グラフィカルなボタン  
 いくつかのボタンは、常に、グラフィカル イメージを使用して、容量を節約して、ローカリゼーションの問題を回避するテキストを追加しないでください。 フィールドの選択とその他の並べ替え可能なリストでよく使用されます。  
  
> [!NOTE]
>  ユーザーは、これらのボタン \(アクセス キーはありません\)\] タブをため実用的な順序で配置する必要があります。 ボタンの name プロパティをスクリーン リーダーは、ボタンの操作を正しく解釈されるように行われる操作にマップします。  
  
|||  
|-|-|  
|追加|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|削除|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|すべてを追加します。|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|すべて削除します。|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|上へ移動|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|下へ移動|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|削除|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### サイズおよび間隔  
 グラフィカルなボタンは、短いバージョンの場合と同様にサイズ変更、 **\[参照...\]** \(26 x 23 ピクセル単位\)\] ボタンをクリックします。  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **ボタン、および表示の透明色を使用せずにグラフィカル イメージの表示方法**  
  
### ハイパーリンク  
 ハイパーリンクは、ヘルプ トピック、モーダル ダイアログで、またはウィザードを開くなどのナビゲーション ベースの操作に適しています。 コマンドのハイパーリンクを使用する場合、UI に表示され、顕著な変更が常に表示されます。 一般に、アクション \(保存、キャンセル、および削除など\) へのコミット操作がより伝えられるボタンを使用しています。  
  
#### 文書のスタイル  
 次の [ユーザー インターフェイスのテキストについては、Windows デスクトップ](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)します。 「学習機能の詳細について、」を使用しない「指示 me 機能の詳細について、」または「このにヘルプを表示する」言い回しです。 代わりに、質問を主にヘルプ コンテンツで確認できる質問の観点からヘルプ リンクのテキスト。 たとえば、"**サーバー エクスプ ローラーにサーバーを追加する方法ですか?**"  
  
#### 視覚スタイル  
  
-   常にハイパーリンクを使用する必要があります [VSColor サービス](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)します。 ハイパーリンクが正しく書式設定されていない場合は、アクティブになったときに赤を点滅したり、アクセスした後、別の色を示しています。  
  
-   状態がないと、リンク、センテンス内の文フラグメントなど、透かしが置かれてコントロールに下線を含めないでください。  
  
-   ホバー時の下線は表示されません。 代わりに、リンクがアクティブであるユーザーに提供されるフィードバックは、わずかな色の変更と適切なリンクのカーソルです。  
  
##  <a name="BKMK_TreeViews"></a> ツリー ビュー  
  
### 概要  
 ツリー ビューでは、親と子グループに、複雑な編成するための一覧を提供します。 ユーザーは、展開したり、表示または基になる子項目を非表示の親グループを折りたたんだりできます。 ツリー ビュー内の各項目を選択して、アクションに詳しいことができます。  
  
 このトピックでは、許容される使用方法、適切な設計、およびツリー ビューの機能について説明します。  
  
#### このトピックの内容  
  
-   [視覚スタイル](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [相互作用](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> 視覚スタイル  
  
#### 展開コントロール  
 ツリー ビュー コントロールは、Windows および Visual Studio で使用される expander のデザインに従っている必要があります。 各ノードでは、expander コントロールを使用して、表示または基になるアイテムを非表示にします。 Expander コントロールを使用して Windows および Visual Studio 内の別のツリー ビューがあります。 ユーザーに一貫性を提供します。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Expander コントロールを使用してツリー ビュー ノードの適切なスタイルを正しい:**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **ツリー ビュー ノードの不適切なスタイルの正しくない:**  
  
#### 選択ツール  
 ツリー ビュー内のノードを選択すると、強調表示をツリー ビュー コントロールの幅いっぱいに展開する必要があります。 これにより、ユーザーを選択した項目を明確に識別できます。 選択範囲の色は、現在の Visual Studio のテーマを反映するはずです。  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **正しくない: 選択したノードの強調表示では、ツリー ビュー コントロールの幅全体は適合しません。**  
  
#### アイコン  
 項目間の相違点を視覚的に特定する助けにいる場合、ツリー ビュー コントロール内のアイコンを使用のみください。 一般に、アイコンは、アイコンが要素の種類を区別するために情報を伝達する異種のリストでのみ使用する必要があります。 同種のリストのアイコンを使用するノイズとよく考えることができ、避ける必要があります。 その場合はグループのアイコン \(親\) には、その中の項目の種類を通知できます。 この規則の例外は、アイコンが動的でと状態を示すために使用されるかどうかになります。  
  
#### スクロール バー  
 コンテンツがツリー ビュー コントロール内に収まる場合は常に、スクロール バーを非表示しています。 かまわないスクロール バーに隠しファイル、または半透明をスクロール可能なウィンドウになるとツリー ビューを含むウィンドウにフォーカスがあるときに表示されるか、ツリーのオーバーしたときにそれ自体を表示します。  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平方向のスクロール バーが表示されます。**  
  
###  <a name="BKMK_TreeViewInteractions"></a> 相互作用  
  
#### コンテキスト メニュー  
 ツリー ビュー ノードには、コンテキスト メニューのサブメニュー オプションが表示されます。 通常は、ユーザーがアイテムを右クリックしてまたは選択した項目を持つ Windows キーボードでメニュー キーを押したときに発生します。 ノードがフォーカスを取得しが選択されていることは重要です。 これにより、ユーザーに属しているサブメニュー項目を識別できます。  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **コンテキスト メニューの向上にフォーカスがユーザーに通知する項目を生成しますが、項目が選択されました。**  
  
#### キーボード  
 ツリー ビューでは、項目を選択し、キーボードを使用してノードの展開\/折りたたみ機能を提供する必要があります。 これにより、ナビゲーションが、ユーザー補助に関する要件を満たしていること。  
  
##### ツリー ビュー コントロール  
 Visual Studio のツリー コントロールは、一般的なキーボード ナビゲーションに従う必要があります。  
  
-   **↑:** ツリーを移動して項目を選択  
  
-   **↓:** 、ツリーの下層に移動して項目を選択  
  
-   **→:** ツリーでノードを展開  
  
-   **←:** ツリーでノードを折りたたみます。  
  
-   **Enter キー:** を開始、読み込み、選択した項目の実行  
  
##### Trid \(ツリー ビューおよびグリッド ビュー\)  
 Trid コントロールは、グリッド内のツリー ビューを含む複雑なコントロールです。 展開、折りたたみ、および、ツリー内の移動は、次の項目を追加のツリー ビューと同じキーボード コマンドを遵守する必要があります。  
  
-   **→:** ノードを展開します。 ノードが展開された後、右側の最も近い列への移動を続行する必要があります。 行の末尾では、ナビゲーションが停止する必要があります。  
  
-   **\] タブ:** 右側の最も近いセルに移動します。  行の最後には、ナビゲーションは、次の行に続行します。  
  
-   **Shift \+ タブ:** 左側の最も近いセルに移動します。  行の先頭には、ナビゲーションは、前の行の右端にあるセルを続行します。  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **Visual Studio での trid コントロール**