---
title: Visual Studio のコモン コントロール パターン |Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e10fdcea9819c34735f285c78a0e2ebb0650f64a
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512318"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio のコモン コントロール パターン
##  <a name="BKMK_CommonControls"></a> コモン コントロール  
  
### <a name="overview"></a>概要  
一般的なコントロールは、Visual Studio でのユーザー インターフェイスの大部分を構成します。 Visual Studio インターフェイスで使用される最も一般的なコントロールが従う必要があります、 [Windows デスクトップ ガイドライン](/windows/desktop/uxguide/controls)します。 このトピックは Visual Studio に固有であり、特殊な状況やその Windows ガイドラインの強化の詳細について説明します。  
  
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
最初にコントロールのスタイルを設定するときに考慮することは、テーマの UI でコントロールを使用するかどうか。 標準的な ui コントロールのないテーマの UI、従う必要があります[標準の Windows デスクトップ スタイル](/windows/desktop/uxguide/controls)、re テンプレートでないと既定のコントロールの外観で表示する必要があります。  
  
-   **標準 (ユーティリティ) ダイアログ ボックス:** ないテーマが適用されました。 Re テンプレートはありません。 基本的なコントロールのスタイルの既定値を使用します。  
  
-   **ツール ウィンドウ、ドキュメント エディター、デザイン サーフェイスおよびテーマが適用されたダイアログ ボックス:** 色サービスを使用して特殊化されたテーマの表示を使用します。  
  
###  <a name="BKMK_Scrollbars"></a> スクロール バー  
 スクロール バーが従う必要があります[のスクロール バーの Windows の一般的な相互作用パターン](/windows/desktop/Controls/about-scroll-bars)しない限り、これらは、コンテンツ情報で補強しているなどのコード エディターにします。  
  
###  <a name="BKMK_InputFields"></a> 入力フィールド  
 一般的な操作の動作に従って、[テキスト ボックスについては、Windows デスクトップ](/windows/desktop/uxguide/ctrl-text-boxes)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   入力フィールド ユーティリティ ダイアログのスタイルを設定しないでください。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマが適用された入力フィールドは、テーマが適用されたダイアログとツール ウィンドウでのみ使用する必要があります。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   読み取り専用フィールド (アクティブ) の既定の前景は灰色 (無効) バック グラウンドになります。  
  
-   フィールドが必要に必要な**\<必要 >** 内にウォーターマークとして。 まれな状況では、以外の背景の色を変更する必要がありますできません。  
  
-   エラーの検証: を参照してください[通知と Visual Studio の進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   入力フィールドは、順番に表示されます、ウィンドウの幅に合わせてしないにも、任意のパスのような長いフィールドの長さと一致には、コンテンツに合わせてサイズに設定する必要があります。 長さ フィールドに文字数が許可されているかの制限事項のユーザーを示す値があります。  
  
     ![正しくない入力フィールドの長さ: 名前はこれだけの時間になります可能性はほとんどありません。](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />正しくない入力フィールドの長さ: 名前はこれだけの時間になります可能性はほとんどありません。
  
     ![入力フィールドの長さを修正: 入力フィールドは、必要なコンテンツの妥当な幅。](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />入力フィールドの長さを修正: 入力フィールドは、必要なコンテンツの妥当な幅。
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> コンボ ボックスとドロップダウン リスト  
一般的な操作の動作に従って、[ドロップダウン リストとコンボ ボックスの Windows デスクトップ ガイドライン](/windows/desktop/uxguide/ctrl-drop)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ ボックスで re テンプレート コントロールはありません。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマの UI でコンボ ボックスとドロップダウン リスト コントロールの標準的なテーマに従います。  
  
#### <a name="layout"></a>レイアウト  
コンボ ボックスとドロップダウン リストは、順番に表示されます、ウィンドウの幅に合わせてしないにも、任意のパスのような長いフィールドの長さと一致には、コンテンツに合わせてサイズにする必要があります。  
  
![: 正しくないドロップダウン幅では、表示されるコンテンツには長すぎます。](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />: 正しくないドロップダウン幅では、表示されるコンテンツには長すぎます。
  
![: 適切なドロップダウン リストのサイズ、翻訳の増加を許可するが、不必要に長い。](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />: 適切なドロップダウン リストのサイズ、翻訳の増加を許可するが、不必要に長い。 
  
###  <a name="BKMK_CheckBoxes"></a> チェック ボックス  
一般的な操作の動作に従って、[チェック ボックスについては、Windows デスクトップ](/windows/desktop/uxguide/ctrl-check-boxes)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ ボックスで re テンプレート コントロールはありません。 基本のスタイルを組み込みコントロールを使用します。  
  
-   テーマの UI では、チェック ボックスは、コントロールの標準的なテーマに従います。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   チェック ボックスとの対話は、ダイアログを表示または別の領域に移動する必要がありますしないでください。  
  
-   チェック ボックスをテキストの最初の行のベースラインに揃えます。  
  
     ![: 正しくないチェック ボックスは、テキストの中心します。](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />: 正しくないチェック ボックスは、テキストの中心します。
  
     ![: 正しいチェック ボックスは、テキストの最初の行に配置します。](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />: 正しいチェック ボックスは、テキストの最初の行に配置します。
  
###  <a name="BKMK_RadioButtons"></a> オプション ボタン  
一般的な操作の動作に従って、[ラジオ ボタンの Windows デスクトップ ガイドライン](/windows/desktop/uxguide/ctrl-radio-buttons)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
ユーティリティ、ダイアログのないラジオ ボタンをスタイルの操作を行います。 基本のスタイルを組み込みコントロールを使用します。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
緊密なレイアウトでのグループの区別を維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
###  <a name="BKMK_GroupFrames"></a> グループのフレーム  
一般的な操作の動作に従って、[グループ フレームの Windows デスクトップ ガイドライン](/windows/desktop/uxguide/ctrl-group-boxes)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
ユーティリティで、ダイアログのグループのフレームのスタイル設定はありません。 基本のスタイルを組み込みコントロールを使用します。  
  
#### <a name="layout"></a>レイアウト  
  
-   緊密なレイアウトでのグループの区別を維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
-   1 つのコントロールのグループのフレームを使用しないでください。  
  
-   グループのフレームのコンテナーではなく水平方向の規則を使用できる場合があります。  
  
##  <a name="BKMK_TextControls"></a> テキスト コントロール

### <a name="static-text-fields"></a>静的なテキスト フィールド

静的なテキスト フィールドは読み取り専用の情報を表示し、ユーザーが選択することはできません。 任意のテキストをユーザーは、クリップボードにコピーするのには使用しないでください。 ただし、読み取り専用の静的テキストは、状態の変更を反映するように変更できます。 上にルート Namespace テキスト ボックスに加えられた変更を反映するように、情報グループの変更 出力名の静的なテキストの下の例です。

静的テキスト情報を表示する 2 つの方法はあります。

場合に、独自の包含なし ダイアログ ボックスでグループ化の競合はありません。 静的なテキストができます。 ボックスの余分な行が本当に必要なかどうかを決定します。 例は、次に示すように、グループ行によって作成されたセクションの下のディレクトリ パスの表示を示します。  

![テキスト コントロールに静的テキスト情報](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />テキスト コントロールに静的なテキストの情報

ダイアログ ボックスの他のグループ化された領域が存在し、読みやすさ、役立つ情報の包含するセクションを非表示または表示すると、(同様、**プロパティ ウィンドウ**説明ペイン) または同様の UI と一致します。ボックス内には、静的テキストを配置します。 このグループ ボックスの 1 つの規則をする必要があり、色付きの`ButtonShadow`:

![[プロパティ] ウィンドウで、静的テキスト](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />[プロパティ] ウィンドウで静的なテキスト

### <a name="read-only-text-box"></a>読み取り専用テキスト ボックス

これにより、ユーザーがフィールド内のテキストを選択しますが、編集できません。 これらのテキスト ボックスがの通常の 3-D 切り取ったによって囲まれた、`ButtonShadow`塗りつぶし。

テキスト ボックスがアクティブになることができます (編集) ユーザーがチェック オフのチェック ボックスまたはラジオ ボタンを選択/選択解除など、関連付けられているコントロールを変更します。 たとえば、**ツール&gt;オプション**ページは、次に示す、**ホーム ページ**テキスト ボックスがアクティブになるときに、**既定を使用** チェック ボックスがオフになって。

![読み取り専用テキスト ボックスで、非アクティブとアクティブの状態を示す](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />読み取り専用テキスト ボックスで、非アクティブとアクティブの状態を表示

### <a name="using-text-in-dialogs"></a>ダイアログ ボックスでテキストを使用します。

ダイアログ ボックス内のテキストの主要なガイドライン:

-   テキスト ボックス、リスト ボックス、および unthemed ダイアログ内のフレームのラベルは、動詞を使用して開始、のみ、最初の単語に初期の資金があるおよび、最後にコロン。

    > 以下のテーマが適用されたダイアログ ボックス内のテキスト コントロール[Windows デスクトップの UX ガイドライン](/windows/desktop/uxguide/top-violations)ヘルプ リンクに疑問符 (?) を除く、句点を取らないとします。

-   チェック ボックスやオプション ボタンのラベルは、動詞、最初の単語だけで、先頭を大文字で開始され、終わりに句読点はありません。

-   ボタン、メニューのメニュー項目、およびタブのラベルでは、各単語 (大文字) 大文字があります。

-   ラベルの用語は、ダイアログの他の同様のラベルと一致する必要があります。

-   可能であれば、書き込みまたは実装するために開発者に移動する前に、テキストを承認ライター/エディターがあります。

-   すべてのコントロールでは、特殊な状況にラベルを除くがありますが tab キーで十分です。
ヘルパー テキストの適切な場合に使用します。

### <a name="helper-text"></a>ヘルパー テキスト

またはを実行するには、どのアクションを示すために、ダイアログの目的を理解するユーザーを支援するダイアログ ボックスに含まれます。 ヘルパー テキストは、単純なダイアログ ボックスの混乱を避けるために必要な場合にのみ、使用する必要があります。 ヘルパー テキストの 2 つのバリエーションは、ダイアログ、および透かしです。

次の一般的な場所でヘルパー テキストと新しい分野の概要を選択します。 ヘルパー テキストの一般的なシナリオは次のとおりです。

-   複雑なダイアログと対話する方法についての他の方向を提供する、ダイアログ ヘルパー テキスト。

-   空のツール ウィンドウやダイアログ ボックスで、なぜコンテンツが表示されていないことを説明するでのウォーターマーク テキスト。

-   説明ペインの下部にあるように、**プロパティ ウィンドウ**します。

-   ユーザーが最初に実行するアクションを説明する、空のエディターでテキストの透かしです。
  
### <a name="dialog-helper-text"></a>ダイアログ ヘルパー テキスト

ヘルパー テキストが適切なユーザー エクスペリエンス デザイナーに役立ちます。 デザイナーでは、その一般的なコンテンツとヘルパーのテキストが表示される場所を定義できます。 ユーザー支援書き込み/編集できる実際のテキスト。

### <a name="watermarks"></a>透かし

ダイアログ ボックスは、若干異なるレベルのウォーターマーク ガイドラインによって享受できます。 ダイアログ ボックス、現れるため多くの UI 要素 (ラベル、ヒントのテキスト、ボタンおよび他のコンテナー コントロール テキストを含む) でビジー状態特に透かしが濃い灰色でを目立たせるものが黒で表示されたら、(VSColor: `ButtonShadow`)。 通常、背景が白のリスト ボックスなどのコントロールの内部透かしが表示されます (VSColor: `Window`)。

-   濃い灰色のテキストの表示 (VSColor: `ButtonShadow`)。 ただし、中間のグレーまたはその他の色の透かしが表示された場合 (VSColor: `ButtonFace`) バック グラウンドし、読みやすさへの不安は、黒のテキストである (VSColor: `WindowText`)。

-   透かしを中央揃えまたは左揃えことができます。 配置の意思決定を行うときに、標準的な設計規則を適用します。 バック グラウンドでは、透かしを選択できません。

![ウォーターマーク テキストの例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />ウォーターマーク テキストの例

### <a name="context-specific-dynamic-text"></a>コンテキストに固有の (動的) テキスト

動的テキストとして使用できるは、ダイアログまたはモードレスの UI で 2 つの方法の 1 つを使用します。 動的ラベルとして、または動的なコンテンツとして。

-   動的なラベル: 動的なテキストの一般的な用途がわかりやすいパネルなどの要素と、右側のグリッドに表示されるこれらの要素のプロパティのリストを含むダイアログ ボックスで選択した項目の詳細についてを提供します。 プロパティ グリッドのラベルに、右側のグリッドにその特定の項目の情報が表示されます、左側の項目を選択すると、動的なことはあります。

-   動的なテキスト。 これにより、特定の情報とされません一般的な情報を表示する必要がある注意する必要がある、使い過ぎないインスタンスで役に立ちます。

ユーザー情報をコピーする機能を許可する場合は、動的テキストが読み取り専用のテキスト フィールドでなければなりません。
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> ボタンやハイパーリンク  
  
### <a name="overview"></a>概要  
ボタンやリンクのコントロール (ハイパーリンク) に従う必要があります[ハイパーリンクの基本的な Windows デスクトップ ガイダンス](/windows/desktop/uxguide/ctrl-links)wording、サイズ変更、および間隔は、使用するためです。  
  
### <a name="choosing-between-buttons-and-links"></a>ボタンまたはリンクの選択  
これまでは、アクションのボタンを使用して、ナビゲーション用に予約されたハイパーリンク。 すべてのケースでボタンを使用することが、ボタンやリンクがいくつかの条件でより交換されることになるよう Visual Studio でのリンクのロールが拡張されました。  
  
コマンド ボタンを使用する場合。  
  
-   主要なコマンド  
  
-   入力を収集するために使用するウィンドウを表示するか、セカンダリ コマンドにある場合でも、選択を行う  
  
-   破壊的なまたは元に戻せない操作  
  
-   ウィザードとページ フロー内のコミットメントのボタン  
  
ツール ウィンドウ、コマンド ボタンを避けるため、ラベルの 2 つ以上の単語が必要な場合またはします。 リンクは、長いラベルを持つことができます。  
  
 リンクを使用する場合。  
  
-   別のウィンドウ、ドキュメント、または web ページへの移動  
  
-   長いラベルまたは操作の目的を説明する短い文を必要とする状況  
  
-   アクションには、破壊的または元に戻せないことに、ボタンで、UI に過は緊密なスペース  
  
-   除外を強調しての状況でセカンダリ コマンドが多数のコマンド  
  
#### <a name="examples"></a>使用例  
![コマンドのステータス メッセージに続く情報バーで使用されているリンク](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />ステータス メッセージに続く情報バーで使用されるコマンドへのリンク
  
![CodeLens ポップアップで使用されているリンク](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens ポップアップで使用されているリンク
  
![セカンダリ コマンドのボタンがあまり注意を引き付けるよう使用されているリンク](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />リンク ボタンがあまり注意を引き付けるようセカンダリ コマンドの使用
  
### <a name="common-buttons"></a>一般的なボタン  
  
#### <a name="text"></a>テキスト  
書き込みのガイドラインに従って[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)します。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
##### <a name="standard-unthemed"></a>標準 (unthemed)  
Visual Studio でのほとんどのボタンは、ユーティリティのダイアログ ボックスで表示され、いないスタイル設定する必要があります。 オペレーティング システムによって決定される、標準のボタンの外観が反映されます。  
  
##### <a name="themed"></a>テーマが適用されました。  
場合によっては、ボタンをスタイル設定された UI 内で使用可能性があり、これらのボタンは適切にスタイル設定する必要があります。 参照してください[ダイアログ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)テーマが適用されたコントロールについて。  
  
### <a name="special-buttons"></a>特殊なボタン  
  
#### <a name="browse-buttons"></a>参照 のボタン  
**[参照...]** ボタンは、グリッド、ダイアログ、およびツール ウィンドウおよびその他のモードレスの UI 要素で使用されます。 コントロールに値を入力することで、ユーザーを支援するピッカーが表示されます。 このボタンは、長短の 2 つのバリエーションがあります。  
  
![長い [参照...] ボタン](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />長い [参照...] ボタン
  
![省略記号のみの短い [...] ボタン](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />省略記号のみの短い [...] ボタン
  
省略記号のみの短い ボタンを使用するとき。  
  
-   1 つ以上の時間を使用する必要がある場合 **[参照...]** など、いくつかのフィールドの参照を許可するときに、ダイアログにボタンをクリックします。 使用して、短い **[...]** 混乱にこのような状況によって作成されたアクセス キーを回避するために各ボタン (**& 参照**と**B (& r)** と同じダイアログ ボックスで)。  
  
-   密 ダイアログ ボックスで、または長い ボタンを配置する適切な場所がありません。  
  
-   場合は、ボタンは、グリッド コントロールに表示されます。  
  
ボタンの使用に関するガイドライン:  
  
-   アクセス キーを使用しないでください。 キーボードを使用してアクセスするには、ユーザーは、隣接するコントロールからタブする必要があります。 タブ オーダーがいっぱいに表示されるフィールドの直後に、[参照] ボタンがあることなどであることを確認します。 最初の期間の下にアンダー スコアを使用しないでください。  
  
-   Microsoft Active Accessibility (MSAA) を設定**名前**プロパティを**を参照しています.** (省略記号) を含む画面を読者は、「ドット ドット ドット」や「期間の期間の期間」はなく"Browse"として。 つまり、設定の管理対象のコントロール、 **AccessibleName**プロパティ。  
  
-   省略記号を使用しないでください **[...]** 参照アクション以外のすべてのボタンをクリックします。 たとえば、必要がある場合、 **[新規作成]** ボタンしますが、ダイアログ ボックスが再設計する必要があります、テキストのための十分なスペースはありません。  
  
##### <a name="sizing-and-spacing"></a>サイズ変更との間隔  
![ボタンの [参照...] をサイズ変更: 標準のバージョンは 75 x 23 ピクセル、短いバージョンは 26 x 23 ピクセル](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />サイズ変更の [参照...] ボタン
  
![間隔 [参照...] ボタン: 関連するコントロールと短い参照間の間隔 ボタンを関連するコントロールと標準の参照ボタン 7 ピクセルの間の間隔を 5 ピクセル](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />行間の [参照...] ボタン
  
#### <a name="graphical-buttons"></a>グラフィカルなボタン  
いくつかのボタンを常にグラフィカル イメージを使用し、領域を節約し、ローカライズの問題を回避するテキストを含めることはありません。 フィールドの選択およびその他の並べ替え可能なリストでよく使用されます。  
  
> **注:** ユーザーがこれらのボタン (アクセス キーはありません) にタブで、そのため、適切な順序で配置する必要があります。 マップ、`name`スクリーン リーダーは、ボタンの操作を正しく解釈するために必要なアクションをボタンのプロパティ。  
  
| 関数 | ボタン |  
| --- | --- |  
| 追加 | ![グラフィカルな [追加] ボタン](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| 削除 | ![「削除」ボタンがグラフィカル](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| すべて追加します。 | ![グラフィカルな [すべて追加] ボタン](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| すべて削除します。 | ![グラフィカルな すべて削除"ボタン](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| 上へ | ![グラフィカルな 上へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| 下へ移動 | ![グラフィカルな 下へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| 削除 | ![グラフィカルな「削除」ボタン](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>サイズ変更との間隔  
グラフィカルなボタンは短いバージョンの場合と同じですサイズ変更、 **[参照...]。** ボタン (26 x 23 ピクセル単位)。  
  
![ボタンの透明色が表示されずにグラフィック イメージの外観](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />ボタンの透明色が表示されずにグラフィック イメージの外観
  
### <a name="hyperlinks"></a>ハイパーリンク  
ハイパーリンクは、ヘルプ トピック、モーダル ダイアログ ボックスで、またはウィザードを開くように、ナビゲーション ベースのアクションに適してします。 コマンドのハイパーリンクを使用する場合、UI に表示され、顕著な変更が常に表示されます。 一般に、(保存、Cancel、および削除する) などのアクションへのコミット アクションより伝達されますボタンを使用します。  
  
#### <a name="writing-style"></a>文書のスタイル  
に従って、[ユーザー インターフェイスのテキストについては、Windows デスクトップ](/windows/desktop/uxguide/text-ui)します。 「について詳細について、」を使用しない「指示 me 機能の詳細について、」または「このヘルプを表示する」言い回しです。 代わりに、質問をしてヘルプ コンテンツに応答する主要な質問の観点からのヘルプ リンク テキスト。 たとえば、"**サーバー エクスプ ローラーにサーバーを追加する方法でしょうか**"。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ハイパーリンクは常に使用する必要があります[The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)します。 ハイパーリンクが正しく書式設定されていない、する場合はアクティブな際の赤で点滅またはアクセスした後に別の色が表示されます。  
  
-   配置されている場合を除き、リンク、センテンス内文のフラグメントのように透かし状態コントロールに下線を含めないでください。  
  
-   下線は、ポインターを合わせると表示しないでください。 代わりに、リンクがアクティブであるユーザーにフィードバックは、わずかな色の変更と適切なリンクのカーソルは。  
  
##  <a name="BKMK_TreeViews"></a> ツリー ビュー  
  
ツリー ビューでは、親と子グループに複雑な整理する方法の一覧を提供します。 ユーザーは、展開したり、表示、または基になる子アイテムを非表示に親グループを折りたたんだりできます。 さらにアクションを提供する、ツリー ビュー内の各項目を選択できます。  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> ツリー ビューのビジュアル スタイル  
  
#### <a name="expanders"></a>展開コントロール  
ツリー ビュー コントロールは、Windows と Visual Studio で使用される expander のデザインに準拠する必要があります。 各ノードは、表示、または基になるアイテムを非表示に expander コントロールを使用します。 Expander コントロールを使用して、Windows と Visual Studio 内の別のツリー ビューを発生する可能性があるユーザーに一貫性が提供します。  
  
![正しい: expander コントロールを使用して、ツリー ビュー ノードの適切なスタイル](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Expander コントロールを使用して、ツリー ビュー ノードの適切なスタイルが正しい。
  
![正しくない: ツリー ビュー ノードの不適切なスタイル](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />ツリー ビュー ノードの不適切なスタイルの正しくない:
  
#### <a name="selection"></a>選択ツール  
ツリー ビュー内のノードを選択すると、強調表示がツリー ビュー コントロールの幅いっぱいに展開する必要があります。 これにより、ユーザーが選択した項目を明確に識別できます。 選択範囲の色は、現在の Visual Studio のテーマを反映します。  
  
![正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。
  
![正しくない: 選択したノードの強調表示は、ツリー ビュー コントロールの幅全体に収まりません。](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />正しくない: 選択したノードの強調表示は、ツリー ビュー コントロールの幅全体に収まりません。
  
#### <a name="icons"></a>アイコン  
項目間の相違点を特定する視覚的に支援している場合、ツリー ビュー コントロールのアイコンを使用のみする必要があります。 一般に、アイコンは、アイコンが要素の種類を区別するために情報を保持する異種のリストでのみ使用する必要があります。 同種のリストのアイコンを使用してノイズとして頻繁に表示できるし、避ける必要があります。 その場合はグループのアイコン (親) には、その中の項目の種類を伝達できます。 この規則の例外は、アイコンは動的でありの状態を示すために使用がかどうかになります。  
  
#### <a name="scroll-bars"></a>スクロール バー  
コンテンツがツリー ビュー コントロール内に収まる場合、スクロール バーを非表示常にする必要があります。 スクロール可能なウィンドウを非表示、または半透明にして、フォーカスのあるウィンドウのツリー ビューを格納しているときに表示またはツリーのホバー時にそれ自体を表示するスクロール バーとして受け入れ可能です。  
  
![内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平スクロール バーが表示されます。](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平スクロール バーが表示されます。
  
###  <a name="BKMK_TreeViewInteractions"></a> ツリー ビューの相互作用  
  
#### <a name="context-menus"></a>コンテキスト メニュー  
ツリー ビュー ノードには、コンテキスト メニューのサブメニューで開くオプションを表示できます。 通常、これは、ユーザーが項目を右クリックしてまたは選択された項目を持つ Windows キーボードでメニュー キーを押したときに発生します。 ノードがフォーカスでが選択されていることは重要です。 これにより、ユーザーに属しているサブメニュー項目を識別できます。  
  
![項目をユーザーに通知するコンテキスト メニューの向上のフォーカスの生成がどの項目が選択されています。](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />項目をユーザーに通知するコンテキスト メニューの向上のフォーカスの生成がどの項目が選択されています。
  
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
  
-   **右矢印:** ノードを展開します。 ノードが展開された後、右側の最も近い列への移動を続行する必要があります。 ナビゲーションは、行の最後に停止する必要があります。  
  
-   **タブ:** 右側の近くのセルに移動します。  行の末尾には、ナビゲーションは、次の行を続けます。  
  
-   **Shift + Tab:** 左側に最も近いセルに移動します。  行の先頭には、ナビゲーションは、前の行の右端のセルを続けます。  
  
![Visual Studio での trid コントロール](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Visual Studio での trid コントロール