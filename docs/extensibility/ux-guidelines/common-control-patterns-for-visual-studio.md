---
title: "Visual Studio のコントロール パターンが一般的な |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3e06a3e89b69b2b69a97c4deb2d68d98913f6e03
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio の共通のコントロール パターン
##  <a name="BKMK_CommonControls"></a>コモン コントロール  
  
### <a name="overview"></a>概要  
コモン コントロールは、Visual Studio でのユーザー インターフェイスの大部分を構成します。 Visual Studio インターフェイスで使用する最も一般的なコントロールが従う必要があります、 [Windows デスクトップ ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)です。 このトピックは Visual Studio に固有であり、特別な状況や、Windows のガイドラインを補強の詳細について説明します。  
  
#### <a name="common-controls-in-this-topic"></a>このトピックのコモン コントロール  
  
-   [スクロール バー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [入力フィールド](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [コンボ ボックスとドロップダウン リスト](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [チェック ボックス](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [オプション ボタン](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [グループ フレーム](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [テキスト コントロール](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [ボタンとハイパーリンク](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [ツリー ビュー](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### <a name="visual-style"></a>Visual スタイル  
最初にコントロールのスタイルを設定するときに考慮することは、テーマの UI でのコントロールを使用するかどうかです。 標準 UI でのコントロールで非テーマの UI、従う必要があります[標準の Windows デスクトップ スタイル](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)、つまり、re テンプレートではありませんが、既定の外観の制御に表示されます。  
  
-   **標準 (ユーティリティ) ダイアログ ボックス:**テーマが適用されません。 再テンプレートは使用しません。 基本コントロール スタイルの既定値を使用します。  
  
-   **ツール ウィンドウ、ドキュメント エディター、デザイン サーフェイスとテーマが適用されたダイアログ:**色サービスを使用して特別なテーマの表示を使用します。  
  
###  <a name="BKMK_Scrollbars"></a>スクロール バー  
 スクロール バーが従う必要があります[のスクロール バーの Windows の一般的な相互作用のパターン](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx)コード エディターでなどのコンテンツ情報で補強するしている、しない限り、します。  
  
###  <a name="BKMK_InputFields"></a>入力フィールド  
 一般的な相互作用動作に従って、[テキスト ボックスの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   入力フィールド ユーティリティのダイアログ ボックスのスタイルを設定しないでください。 コントロールに固有の基本的なスタイルを使用します。  
  
-   テーマは、入力フィールドは、テーマが適用されたダイアログおよびツール ウィンドウでのみ使用する必要があります。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   読み取り専用フィールドには、既定の (アクティブ) の前景色が灰色 (無効) のバック グラウンドがあります。  
  
-   フィールドが必要に必要な**\<必要 >**内にウォーターマークとして。 まれな状況では、以外の背景色を変更する必要がありません。  
  
-   検証のエラー: 参照[通知および Visual Studio の進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   入力フィールドは、任意のパスと同様に、長いフィールドの長さと一致することや、順番に表示されます、ウィンドウの幅に合わせていないは、コンテンツに合わせてサイズに設定する必要があります。 長さには、ユーザーに、フィールドの文字数は許可されてに制限を示す可能性があります。  
  
     ![正しくない入力フィールドの長さ: 名前がこの長いなる可能性はほとんどありません。] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707 01_IncorrectInputFieldControl")<br />正しくない入力フィールドの長さ: 名前がこの長いなる可能性はほとんどありません。
  
     ![入力フィールドの長さを修正: 入力フィールドが必要なコンテンツの適切な幅です。] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707 02_CorrectInputFieldControl")<br />入力フィールドの長さを修正: 入力フィールドが必要なコンテンツの適切な幅です。
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>コンボ ボックスとドロップダウン リスト  
一般的な相互作用動作に従って、[ドロップダウン リストとコンボ ボックスの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ ボックスで、再テンプレート コントロールとしません。 コントロールに固有の基本的なスタイルを使用します。  
  
-   テーマの UI でコンボ ボックスやドロップダウン コントロールの標準的なテーマに従います。  
  
#### <a name="layout"></a>レイアウト  
コンボ ボックスとドロップダウン リストは、任意のパスと同様に、長いフィールドの長さと一致することや、順番に表示されます、ウィンドウの幅に合わせていないは、コンテンツに合わせてサイズ必要があります。  
  
![: 正しくないドロップダウン幅では、表示されるコンテンツには長すぎます。] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707 03_IncorrectDropDownLayout")<br />: 正しくないドロップダウン幅では、表示されるコンテンツには長すぎます。
  
![正しい: ドロップダウン リストにサイズが調整の翻訳の増加を許可するが、不必要に長時間かかる場合。] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707 04_CorrectDropDownLayout")<br />正しい: ドロップダウン リストにサイズが調整の翻訳の増加を許可するが、不必要に長時間かかる場合。 
  
###  <a name="BKMK_CheckBoxes"></a>チェック ボックス  
一般的な相互作用動作に従って、[チェック ボックスの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   ユーティリティのダイアログ ボックスで、再テンプレート コントロールとしません。 コントロールに固有の基本的なスタイルを使用します。  
  
-   テーマの UI では、チェック ボックスは、コントロールの標準のテーマに従います。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
  
-   チェック ボックスとの対話は、ダイアログ ボックスを表示したり、別の領域に移動する必要がありますしないでください。  
  
-   チェック ボックスのテキストの最初の行のベースラインに揃えます。  
  
     ![正しくありません: チェック ボックスの中心は、テキスト。] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707 05_IncorrectCheckBoxAlign")<br />正しくありません: チェック ボックスの中心は、テキスト。
  
     ![正しい: チェック ボックスは、テキストの最初の行に配置されます。] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707 06_CorrectCheckBoxAlign")<br />正しい: チェック ボックスは、テキストの最初の行に配置されます。
  
###  <a name="BKMK_RadioButtons"></a>オプション ボタン  
一般的な相互作用動作に従って、[のオプション ボタンの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
ユーティリティのダイアログ ボックスでスタイル オプション ボタンではない操作を行います。 コントロールに固有の基本的なスタイルを使用します。  
  
#### <a name="specialized-interactions"></a>特殊な相互作用  
緊密なレイアウトでのグループの違いを維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
###  <a name="BKMK_GroupFrames"></a>グループ フレーム  
一般的な相互作用動作に従って、[グループ フレームの Windows デスクトップ ガイドライン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
ユーティリティのダイアログ ボックスでないグループ フレームをスタイルします。 コントロールに固有の基本的なスタイルを使用します。  
  
#### <a name="layout"></a>レイアウト  
  
-   緊密なレイアウトでのグループの違いを維持するために必要でない限り、オプションの選択を囲むグループ フレームを使用する必要はありません。  
  
-   1 つのコントロールのグループのフレームを使用しないでください。  
  
-   グループのフレームのコンテナーではなく、水平線を使用できる場合があります。  
  
##  <a name="BKMK_TextControls"></a>テキスト コントロール

### <a name="static-text-fields"></a>静的なテキスト フィールド

静的なテキスト フィールドは読み取り専用の情報を表示し、ユーザーが選択することはできません。 ユーザーがクリップボードにコピーすることも任意のテキストを使用しないでください。 ただし、読み取り専用の静的なテキストは、状態の変更を反映するように変更できます。 次の例で、ルート Namespace 上にテキスト ボックスに加えられた変更を反映するために情報のグループの変更 出力の名前の静的なテキスト。

静的なテキストの情報を表示する 2 つの方法ができます。

静的なテキストは、ときに、独自の抑制なし ダイアログ ボックスでグループ化の競合が起こらないを指定できます。 ボックスの余分な行が本当に必要なかどうかを決定します。 例は、次に示すように、グループ行によって作成されたセクションの下のディレクトリ パスの表示を示します。  

![テキスト コントロールに静的なテキスト情報](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />テキスト コントロールに静的なテキストの情報

その他のグループ化された領域が存在し、読みやすさ、役立つ情報の包含するダイアログ ボックスでセクションが非表示または表示することができ、(ように、**プロパティ ウィンドウ**説明ペイン) または類似の UI と一貫性がある場合ボックス内には、静的テキストを配置します。 このグループ ボックスの 1 つの規則をする必要があり、色付きの`ButtonShadow`:

![[プロパティ] ウィンドウで静的なテキスト](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />[プロパティ] ウィンドウで静的なテキスト

### <a name="read-only-text-box"></a>読み取り専用のテキスト ボックス

これにより、ユーザーがフィールド内のテキストの選択が、編集できません。 これらのテキスト ボックスに通常の 3-D 切り取ったによって囲まれた、`ButtonShadow`塗りつぶし。

テキスト ボックスがアクティブになることができます (編集)、ユーザーがチェック/オフにする チェック ボックスまたはラジオ ボタンを選択する/選択解除するなど、関連付けられたコントロールを変更します。 たとえば、**ツール&gt;オプション**以下に示すページ、**ホーム ページ**テキスト ボックスがアクティブになったときに、**デフォルトを使用** チェック ボックスがオフになってです。

![読み取り専用テキスト ボックスで、アクティブと非アクティブの状態を示す](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />読み取り専用テキスト ボックスで、アクティブと非アクティブの状態を表示

### <a name="using-text-in-dialogs"></a>ダイアログ ボックスでテキストを使用します。

ダイアログ ボックス内のテキストの主要なガイドライン:

-   テキスト ボックス、リスト ボックス、および unthemed ダイアログ内のフレームのラベル動詞を使用して開始、初期資金の最初の単語のみを持ち、コロンで終わる。

    > テーマが適用されたダイアログ ボックス内のテキスト コントロールに従う[Windows デスクトップのユーザー エクスペリエンス ガイドライン](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx)し、ヘルプ リンクに疑問符 (?) を除く、末尾の区切り記号はなりません。

-   チェック ボックスやオプション ボタンのラベルは、最初の単語のみ、初期の大文字、動詞を使用して開始され、終わりに句読点はありません。

-   ボタン、メニューのメニュー項目とタブのラベルでは、各単語 (大文字) 大文字があります。

-   ラベルの用語は、その他のダイアログでの同様のラベルと一致する必要があります。

-   可能であれば、書き込み、または実装するため、開発者に移動する前に、テキストを承認ライター/エディターがあります。

-   すべてのコントロールでは、特別な状況でラベルを除くが必要するタブで十分です。
該当する場合、ヘルパー テキストを使用します。

### <a name="helper-text"></a>ヘルパー テキスト

ダイアログ ボックスの目的を理解するユーザーを支援する、またはを実行するには、どのアクションを示すダイアログ ボックスに含まれます。 ヘルパー テキストは、単純なダイアログ ボックスの混乱を避けるために必要な場合にのみ、使用する必要があります。 ヘルパー テキストの 2 つのバリエーションは、ダイアログ、およびウォーターマークです。

ヘルパー テキストの一般的な場所に従うし、新しい領域の概要を選択します。 ヘルパー テキストの一般的なシナリオは次のとおりです。

-   複雑なダイアログと対話する方法に関するその他の方向を指定する、ダイアログ ヘルパー テキストです。

-   空のツール ウィンドウまたはダイアログ ボックスで、なぜコンテンツが表示されていないことを説明するテキストの透かしです。

-   説明ペインの下部にあるなど、**プロパティ ウィンドウ**します。

-   作業を開始するユーザーが実行するアクションを説明する、空エディター内のテキストの透かしです。
  
### <a name="dialog-helper-text"></a>ダイアログ ヘルパー テキスト

ユーザー エクスペリエンスのデザイナーはヘルパー テキストが適切なタイミングを判断に役立ちます。 デザイナーでは、その全般的な内容だけでなくヘルパー テキストが表示される場所を定義できます。 ユーザー支援できる書き込み/編集実際のテキスト。

### <a name="watermarks"></a>透かし

ダイアログ ボックスは、若干異なるレベルのウォーターマーク ガイドラインによって享受できます。 ダイアログ出現するための多数の UI 要素 (ラベル、ヒントのテキスト、ボタンとテキストを含む他のコンテナー コントロール) を処理して特に黒で表示されるときに透かし目立つ濃い灰色で (VSColor: `ButtonShadow`)。 通常、背景が白リスト ボックス コントロールの内部透かしが表示されます (VSColor: `Window`)。

-   濃い灰色のテキストの表示 (VSColor: `ButtonShadow`)。 ただし、レベルのウォーターマークがグレーまたはその他の色で表示された場合 (VSColor: `ButtonFace`) 背景し、読みやすさの関係に黒のテキストがある (VSColor: `WindowText`)。

-   透かしを中央揃えまたは左揃えことができます。 配置の意思決定を行うときに、標準的なデザイン規則を適用します。 バック グラウンドでは、レベルのウォーターマークを選択することはできません。

![ウォーターマーク テキストの例](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />ウォーターマーク テキストの例

### <a name="context-specific-dynamic-text"></a>コンテキスト固有の (動的) テキスト

動的テキストとして使用できるは、ダイアログやモードレス UI 内の 2 つの方法の 1 つを使用します。 動的ラベルとして、または動的なコンテンツとして。

-   動的ラベル: 動的テキストの一般的な用途がわかりやすいパネルなど要素と、右側のグリッドに表示されるこれらの要素のプロパティのリストを含むダイアログ ボックスで、選んだ項目の詳細を提供します。 左側の項目を選択すると、右側のグリッドはその特定の項目の情報が表示できるように、プロパティ グリッドのラベルが動的な可能性があります。

-   動的なテキスト。 これにより、特定の情報と一般的な情報を表示する必要がある注意が必要ないを過剰に使用するインスタンスに役に立ちます。

ユーザー情報をコピーする機能を許可する場合は、動的なテキストが読み取り専用のテキスト フィールドにする必要があります。
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>ボタンとハイパーリンク  
  
### <a name="overview"></a>概要  
ボタンとリンクのコントロール (ハイパーリンク) に従う必要があります[ハイパーリンクの基本的な Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx)表現、サイズ変更、および間隔で使用するためです。  
  
### <a name="choosing-between-buttons-and-links"></a>ボタンまたはリンクの選択  
従来、ボタンは、アクションを使用しているし、ナビゲーションの予約済みのハイパーリンクです。 ボタンを使用すると、すべてのケースでは、リンクの役割はボタンとのリンクを一部の条件より交換できるように、Visual Studio で展開されています。  
  
コマンド ボタンを使用する場合。  
  
-   主要なコマンド  
  
-   入力を収集するために使用するウィンドウを表示するか、コマンドがセカンダリにある場合でも、選択を行う  
  
-   破壊的なまたは元に戻せない操作  
  
-   ウィザードとページのフロー内のコミットメント ボタン  
  
ツール ウィンドウでコマンド ボタンを避けるため、ラベルの 3 つ以上の単語が必要になった場合。 リンクは、長いラベルを持つことができます。  
  
 リンクを使用するとき。  
  
-   別のウィンドウ、ドキュメント、または web ページへの移動  
  
-   長いラベルまたは操作の目的を説明する短い文を必要とする状況  
  
-   アクションが破壊または元に戻すことがないことに、ボタンで、UI に圧倒は緊密なスペース  
  
-   除外強調の種類の状況でセカンダリ コマンドがある多くのコマンド  
  
#### <a name="examples"></a>例  
![コマンドのステータス メッセージに続く情報バーに使用されているリンク](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703 01_CommandLinkInfobar")<br />ステータス メッセージに続く情報バーに使用されているコマンドのリンク
  
![CodeLens ポップアップで使用されているリンク](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703 02_LinksInCodeLens")<br />CodeLens ポップアップで使用されているリンク
  
![セカンダリ コマンドのボタンが多すぎる注意を引くが使用されているリンク](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703 03_LinksAsSecondaryCommands")<br />セカンダリ コマンドのボタンが多すぎる注意を引くが使用されているリンク
  
### <a name="common-buttons"></a>一般的なボタン  
  
#### <a name="text"></a>テキスト  
書き込みのガイドラインに従って[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)です。  
  
#### <a name="visual-style"></a>Visual スタイル  
  
##### <a name="standard-unthemed"></a>標準 (unthemed)  
Visual Studio でのほとんどのボタンは、ユーティリティのダイアログ ボックスで表示され、スタイルいない必要があります。 オペレーティング システムで使用される標準ボタンの外観が反映されます。  
  
##### <a name="themed"></a>テーマ  
場合によっては、スタイルを指定した UI 内でのボタンを使用することがあり、これらのボタンは適切にスタイル設定する必要があります。 参照してください[ダイアログ](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)コントロールにテーマについてはします。  
  
### <a name="special-buttons"></a>特殊なボタン  
  
#### <a name="browse-buttons"></a>参照... のボタン  
**[参照...]**ボタンはグリッド、ダイアログ、およびツール ウィンドウおよび他のモードレスの UI 要素で使用します。 コントロールに値を満たすためにユーザーを支援するピッカーが表示されます。 このボタンは、長い形式と短いの 2 つのバリエーションがあります。  
  
![長い [参照...] ボタン](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703 04_BrowseLong")<br />長い [参照...] ボタン
  
![省略記号のみの短い [...] ボタン](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703 05_BrowseShort")<br />省略記号のみの短い [...] ボタン
  
省略記号のみの短い ボタンを使用する場合。  
  
-   1 つ以上長を使用する必要がある場合**[参照...]**を参照するためのいくつかのフィールドの許容場合と同様に、ダイアログ ボックスでボタンをクリックします。 使用して、短い**[...]**を複雑になる場合にこのような状況によって作成されるアクセス キーを回避するのにはそれぞれのボタン (**& 参照**と**B & rowse**同じダイアログ ボックスで)。  
  
-   厳しい ダイアログ ボックスで、または長い ボタンを配置する適切な場所がありません。  
  
-   場合は、ボタンは、グリッド コントロールに表示されます。  
  
ボタンの使用に関するガイドライン:  
  
-   アクセス キーを使用しないでください。 キーボードを使用してそれにアクセスするに、ユーザーは、隣接するコントロールからタブする必要があります。 タブ オーダーは入力フィールドの直後に、[参照] ボタンがあるようににことを確認します。 最初の期間の下にアンダー スコアを使用しないでください。  
  
-   Microsoft Active Accessibility (MSAA) を設定**名前**プロパティを**を参照しています.** (省略記号) を含むため、画面を読者は、「ドット ドット ドット」や「期間前期」はなく"参照"として。 つまり、設定、マネージ コントロールを**AccessibleName**プロパティです。  
  
-   省略記号を使用しないで**[...]**参照アクション以外のボタンをクリックします。 たとえば、必要がある場合、 **[新規作成 ...>]**ボタンしますが、ダイアログ ボックスが再設計する必要があるしのテキスト、十分な空き領域を持っていません。  
  
##### <a name="sizing-and-spacing"></a>サイズ変更と間隔  
![[参照...] のサイズのボタン: 標準のバージョンは 75 x 23 ピクセル、短い形式は 26 x 23 ピクセル](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703 06_BrowseSizing")<br />サイズ変更の [参照...] ボタン
  
![間隔 [参照...] ボタン: 関連するコントロールと標準の [参照] ボタン 7 ピクセルの間のスペース、関連するコントロールと参照の短い間隔ボタン 5 ピクセル](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703 07_BrowseSpacing")<br />行間の [参照...] ボタン
  
#### <a name="graphical-buttons"></a>グラフィカルなボタン  
いくつかのボタンは、常に、グラフィカル イメージを使用して、領域を節約し、ローカリゼーションの問題を避けるためにテキストを含めることはありませんください。 フィールドの選択と並べ替え可能な他のリストでよく使用されます。  
  
> **注:** (アクセス キーはありません)、これらのボタンにタブで、そのため、適切な順序で配置する必要があるユーザー。 マップ、`name`スクリーン リーダーは、ボタンの動作を正しく解釈されるように実行されるアクションをボタンのプロパティです。  
  
| 関数 | ボタン |  
| --- | --- |  
| 追加 | ![グラフィカルな「追加」ボタン](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703 08_ButtonAdd") |
| 削除 | ![グラフィカルな [削除] ボタン](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703 09_ButtonRemove") |
| すべてを追加します。 | ![グラフィカルな すべて追加"ボタン](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703 10_ButtonAddAll") |
| すべてを削除します。 | ![グラフィカルな [すべて削除] ボタン](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703 11_ButtonRemoveAll") |
| 上へ | ![グラフィカルな 上へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703 12_ButtonMoveUp") |
| 下へ移動 | ![グラフィカルな 下へ移動"ボタン](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703 13_ButtonMoveDown") |
| 削除 | ![グラフィカルな"Delete"ボタン](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703 14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>サイズ変更と間隔  
グラフィカルなボタンは、同じの短いバージョンのサイズ変更、 **[参照...]**ボタン (26 x 23 ピクセル単位)。  
  
![ボタン、および透明色の表示を使用せずにグラフィック イメージの外観](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703 15_GraphicalButtonSpacing")<br />ボタン、および透明色の表示を使用せずにグラフィック イメージの外観
  
### <a name="hyperlinks"></a>ハイパーリンク  
ハイパーリンクは、ヘルプ トピック、モーダル ダイアログまたはウィザードを開くように、ナビゲーション ベースのアクションにも適しています。 コマンドのハイパーリンクを使用する場合、UI に表示と変更が常に表示されます。 一般に、アクション (保存、キャンセル、および削除) などの操作へのコミットをより適切に伝達されますボタンを使用しています。  
  
#### <a name="writing-style"></a>書き方  
以下の[ユーザー インターフェイスのテキストの Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)です。 「について詳細は、」を使用しない「指示 me 詳細は、」または「このヘルプを表示する」フレージングです。 代わりに、質問をしてヘルプ コンテンツに応答主質問の観点からヘルプ リンク テキスト。 たとえば、"**サーバー エクスプ ローラーにサーバーを追加する方法ですか?**"  
  
#### <a name="visual-style"></a>Visual スタイル  
  
-   常にハイパーリンクを使用する必要があります[VSColor サービス](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)です。 ハイパーリンクが正しく書式設定されていない場合、アクティブなときに、赤を点滅したり、アクセスした後に別の色を示します。  
  
-   リンクは、完全な文章内文のフラグメントのように透かしにしない限り、状態が置かれてコントロールに下線を含めないでください。  
  
-   ホバー時の下線通常表示されません。 代わりに、リンクがアクティブであるユーザーにフィードバックは、わずかな色の変更と適切なリンクのカーソルです。  
  
##  <a name="BKMK_TreeViews"></a>ツリー ビュー  
  
ツリー ビューでは、親と子グループに、複雑な編成するための一覧を提供します。 ユーザーは、展開したり、親グループを表示または基になる子項目を非表示を折りたたんだりできます。 さらにアクションを提供するツリー ビュー内の各項目を選択できます。  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>ツリー ビューの表示スタイル  
  
#### <a name="expanders"></a>展開コントロール  
ツリー ビュー コントロールは、Windows および Visual Studio で使用される expander デザインに従っている必要があります。 各ノードは、基になるアイテムを表示したり閉じたりする expander コントロールを使用します。 Expander コントロールを使用して、Windows および Visual Studio 内の別のツリー ビューを発生する可能性があるユーザーの整合性を提供します。  
  
![正しい: expander コントロールを使用して、ツリー ビュー ノードの適切なスタイル](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />Expander コントロールを使用して、ツリー ビュー ノードの正しい: 適切なスタイル
  
![正しくない: ツリー ビュー ノードの不適切なスタイル](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705 2_TreeViewIncorrect1")<br />ツリー ビュー ノードの不適切なスタイルの正しくない:
  
#### <a name="selection"></a>選択ツール  
ツリー ビュー内でノードを選択すると、強調表示をツリー ビュー コントロールの幅全体に展開する必要があります。 ユーザーは、選択した項目を明確に識別できます。 選択範囲の色は、現在の Visual Studio のテーマを反映します。  
  
![正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705 1_TreeViewCorrect")<br />正しい: 選択したノードの強調表示には、ツリー ビュー コントロールの幅全体が収まるようにします。
  
![正しくない: 選択したノードの強調表示は、ツリー ビュー コントロールの幅全体に収まっていません。] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705 3_TreeViewIncorrect2")<br />正しくない: 選択したノードの強調表示は、ツリー ビュー コントロールの幅全体に収まっていません。
  
#### <a name="icons"></a>アイコン  
場合は、特定の支援に視覚的に項目間の相違点、ツリー ビュー コントロール内のアイコンを使用のみしてください。 一般に、アイコンは、アイコンが要素の種類を区別するために情報を伝達する異種のリストでのみ使用する必要があります。 同種のリストでアイコンを使用して頻繁にノイズと考えることができ、避ける必要があります。 その場合はグループのアイコン (親) には、その中の項目の種類を伝えることができます。 この規則の例外は、アイコンが動的し、状態を示すために使用されるかどうかになります。  
  
#### <a name="scroll-bars"></a>スクロール バー  
コンテンツがツリー ビュー コントロール内に収まる場合、スクロール バーを非表示常にする必要があります。 隠しファイル、または半透明スクロール可能なウィンドウで、ツリー ビューを含むウィンドウにフォーカスがあるときに表示またはツリーのホバー時にそれ自体を表示がスクロール バーもかまわない。  
  
![内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平方向のスクロール バーが表示されます。] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705 4_Scrollbars")<br />内容がツリー ビュー コントロールの制限を超えたために、両方の垂直および水平方向のスクロール バーが表示されます。
  
###  <a name="BKMK_TreeViewInteractions"></a>ツリー ビューの相互作用  
  
#### <a name="context-menus"></a>コンテキスト メニュー  
ツリー ビュー ノードには、コンテキスト メニューのサブメニューのオプションを表示できます。 通常、ユーザーが項目を右クリックしてまたは選択した項目を持つ Windows キーボードでメニュー キーを押したときに発生します。 ノードがフォーカスを取得しが選択されていることは重要です。 これにより、ユーザーに属しているサブメニュー項目を識別します。  
  
![コンテキスト メニューの向上にフォーカスをユーザーに通知するどの項目を生成しますが、項目が選択されています。] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705 5_ContextMenu")<br />コンテキスト メニューの向上にフォーカスをユーザーに通知するどの項目を生成しますが、項目が選択されています。
  
#### <a name="keyboard"></a>キーボード  
ツリー ビューでは、アイテムを選択し、キーボードを使用して、ノードの展開/折りたたみする機能を提供する必要があります。 これにより、ナビゲーションが、ユーザー補助に関する要件を満たしています。  
  
##### <a name="tree-view-control"></a>ツリー ビュー コントロール  
Visual Studio のツリーのコントロールには、共通のキーボード ナビゲーションを従う必要があります。  
  
-   **上矢印:**ツリーを移動して項目を選択  
  
-   **下向きの矢印:**ツリーの下層に移動して項目を選択  
  
-   **右矢印:**ツリーでノードを展開  
  
-   **左矢印:**ツリーでノードの折りたたみ  
  
-   **キーを入力:**を開始するロードは、選択した項目を実行  
  
##### <a name="trid-tree-view-and-grid-view"></a>Trid (ツリー ビューおよびグリッド ビュー)  
Trid コントロールは、グリッド内のツリー ビューを含む複雑なコントロールです。 展開、縮小、およびツリーを移動するには、次の項目を追加のツリー ビューと同じキーボード コマンドを遵守する必要があります。  
  
-   **右矢印:**ノードを展開します。 ノードを展開すると後、右側の最も近い列への移動を続行する必要があります。 行の終わりでナビゲーションは停止する必要があります。  
  
-   **タブ:**右側の最も近いセルに移動します。  行の最後に、ナビゲーションは、次の行を続行します。  
  
-   **Shift + Tab:**左側に最も近いセルに移動します。  行の先頭には、ナビゲーションは、前の行の右端にあるセルを続行します。  
  
![Visual Studio での trid コントロール](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705 6_Trid")<br />Visual Studio での trid コントロール