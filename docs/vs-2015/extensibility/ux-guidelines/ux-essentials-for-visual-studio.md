---
title: Visual Studio 用の UX Essentials |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7c9c2fe1c076a8851b1b95a9957cd721c61ae21
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799497"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio の UX の基本情報
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>ベスト プラクティス  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.Visual Studio 環境内で一貫しています。  
  
-   シェル内で既存の相互作用パターンに従います。  
  
-   シェルのビジュアル言語と職人気質の要件に一致するように機能を設計します。  
  
-   存在する場合は、共有のコマンドとコントロールを使用します。  
  
-   Visual Studio の階層とコンテキストを確立して、UI のドライブの方法を理解します。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.フォントと色の環境のサービスを使用します。  
  
-   UI は、カスタマイズ オプション ダイアログ ボックスで フォントおよび色 ページでは、公開される場合を除き、現在の環境フォントの設定を遵守する必要があります。  
  
-   UI 要素には、共有環境トークンまたは機能固有のトークンを使用して、VSColor Service を使用する必要があります。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.新しい VS スタイルで一貫性のあるすべての画像を作成します。  
  
-   アイコン、グリフ、およびその他のグラフィックスの Visual Studio のデザインの原則に従います。  
  
-   グラフィック要素のテキストを配置しないでください。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.ユーザー中心の観点から設計します。  
  
-   内の個々 の機能の前にタスク フローを作成します。  
  
-   ユーザーに精通することし、仕様にその知識を明示します。  
  
-   UI を確認する際に、包括的なエクスペリエンスと、詳細情報を評価します。  
  
-   UI の設計機能でのロケールまたは言語に関係なく魅力的な残るようにします。  
  
## <a name="screen-resolution"></a>画面の解像度  
  
### <a name="minimum-resolution"></a>最小解像度  
 Visual Studio Dev14 の最小解像度は、1280 x 1024 です。 つまり、ある*可能*ユーザー エクスペリエンスが最適化ができない可能性がありますが、この解像度では、Visual Studio を使用します。 すべての側面は 1,280 x 1,024 より低い解像度で使用できることの保証はありません。  
  
 最初のダイアログ サイズでは、96 dpi でこの最小解像度内 IDE のフレーム内に収まるように 1000 ピクセルを超えることはできません。  
  
### <a name="high-density-displays"></a>高密度が表示されます。  
 Visual Studio の UI は、すべての DPI スケール変換、ボックスから Windows をサポートする要素で問題なく動作する必要があります: 150%、200%、250% です。  
  
## <a name="anti-patterns"></a>アンチ パターン  
 Visual Studio には、以下のガイドラインとベスト プラクティスは、UI の多くの例が含まれています。 一貫性を保つために、開発者は、多くの場合、製品 UI の設計パターンが構築していることに似ていますから借用します。 これは、リリースするという私たちのドライブのユーザーとの対話およびビジュアル デザインの一貫性を利用するは場合によっては優先順位付けの参加を解除またはスケジュールの制約のためのガイドラインに準拠しないいくつかの詳細と機能の有効なアプローチです。 このような場合は、たくないチームがこれらの「アンチ パターン」のいずれかのコピーを Visual Studio 環境内で不適切なまたは非整合な UI が急増するためです。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>必要なフィールド/設定の既定のエラー状態の表示  
  
#### <a name="feature-team-goals"></a>機能チームの目標  
  
-   構成する必要がある要素を追加することをユーザーに警告します。  
  
-   入力を必要とする領域に、ユーザーの注意を促します。  
  
#### <a name="anti-pattern-solution"></a>ソリューションのアンチ パターン  
 ユーザーがアクションを開始するとすぐに、およびタスクが完了する前に、構成が必要な領域の横に重大な停止アイコンをすぐに配置します。  
  
#### <a name="example-manifest-designer-declarations"></a>例: マニフェスト デザイナーの宣言  
 一覧に宣言を追加すると、すぐには、ユーザーが必要なプロパティを設定するまで引き続き発生するエラー状態で配置します。  
  
 この場合、アラートに使用されるアイコンには、"x"が含まれているため、追加の懸念がある、横にあるアイコンを使用できないので、一般的なを削除します。 その結果、UI より不恰好コントロールを削除 ボタンを使用します。  
  
 ![マニフェストの反デザイナー エラー宣言&#45;パターン](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti パターン")  
  
 **既定では、エラー状態で UI を配置することは、Visual Studio のアンチ パターンです。**  
  
#### <a name="alternatives"></a>代替手段  
 この問題をより良いソリューションは、することです。  
  
-   警告なしの宣言を追加するユーザーを許可して、すぐに移動して、項目のプロパティを設定します。  
  
-   警告アイコン (ゴールド三角形) を追加するときにフォーカスが移動、項目からなど、リストに別の宣言を追加するか、デザイナー内のタブを変更しようとします。  
  
-   ユーザーは、宣言のプロパティを設定する前にタブを変更しようとすると、アプリケーションがビルドされないことを説明するダイアログをポップアップ表示 (または、どのような影響)、警告が解決されるまでです。 場合は、ユーザーがダイアログを閉じるし、タブか、アイコン (重大または警告、必要に応じて) に追加されます宣言 タブ。  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>UI を破棄する前にテキストを読み取るユーザーの強制  
  
#### <a name="feature-team-goals"></a>機能チームの目標  
 最初に説明テキストを表示することがなく、UI を消去するユーザーを禁止します。  
  
#### <a name="anti-pattern"></a>アンチ パターン  
 X の一般的なパターンを決定する VS UI 内でさまざまな場所にビデオへのリンクを挿入するチームは、UX で指定されたボタンとツールヒントの説明を閉じて代わりに、ドロップダウン リストと"次回から表示しない"リンクを実装します。  
  
 ![説明のテキストを反&#45;パターン&#45;が正しくない](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **正しくありません: Visual Studio 内でのアンチ パターンを UI を破棄する前に説明文を読み取るユーザーを強制です。**  
  
#### <a name="result"></a>結果  
 閉じるボタン (1 回のクリック) 単純なのではなく、ユーザーは 2 回のクリックを使用して、ビデオへのリンクが表示されるすべての場所では、UI を単純に無視するように強制します。  
  
#### <a name="alternatives"></a>代替手段  
 このような状況に適切な設計は Internet Explorer、Office、および Visual Studio に共通のパターンに準拠すること: ポインターを合わせると、ユーザーに、ツールヒントの説明を表示し、1 回のクリックには、UI が非表示にします。  
  
 ![説明のテキストを反&#45;パターン&#45;正しい](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti パターン修正")  
  
 **: 適切な設計どおり、ビデオへのリンクがポインターを合わせると追加情報を含むヒントを表示する必要があり、さらに操作を必要としないメッセージを無視する必要があります"X"をクリックします。**  
  
### <a name="using-command-bars-for-settings"></a>コマンド バーを使用して、設定  
 ![コマンド バー anti&#45;パターン&#45;図 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-パターン-FigureA")  
  
 **図 a: コマンド バーのアンチ パターン**  
  
 **図 A**このアンチ パターンを表します。 コマンドは、単に適用されるコマンド ボタンの下に設定します。 このスケッチの場合は、[デバッグ開始] 以外のコマンドがあります: などのブラウザー、デバッグなしで開始、およびステップ インでビュー-選択した設定を尊重します。  
  
 ![コマンド バー anti&#45;パターン&#45;図 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-パターン-FigureB")  
  
 **図 b: 向上ですが、まだコマンド バーのアンチ パターン**  
  
 ようにが少し向上の望ましくないが、ツールバーでこの種類の設定を配置する**図 B**します。分割ボタン領域が少なくなると改善をドロップダウン リストではそのため、中に両方の設計もを使用しているツールバーがありません。 実際にコマンドを昇格します。  
  
 ![コマンド バー anti&#45;パターン&#45;図 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-パターン-FigureC")  
  
 **Visual Studio のコマンド バーのパターンの図の c: 正しい使用します。**  
  
 **図 C**設定は、一連のコマンドに関連付けられます。 設定されているグローバル設定がないとだけ、4 つのコマンドを切り替えしています。 これは、ツールバーのコマンドの許容可能な場合だけです。  
  
### <a name="control-anti-patterns"></a>コントロールのアンチ パターン  
 いくつかのアンチ パターンは、単に不適切な使用方法またはコントロールまたはコントロールのグループのプレゼンテーションです。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>下線がハイパーリンクではないグループのラベルとして使用  
 ハイパーリンクのみのテキストに下線を使用する必要があります。  
  
 **正しくありません。**  
  
 ![反下線&#45;グループ ラベルのパターン](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **ハイパーリンクが下線付きのテキストは、Visual Studio のアンチ パターンです。**  
  
 **よし：**  
  
 ![反下線&#45;グループ ラベルのパターン&#40;正しい&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **スタイルが正しく、ハイパーリンク以外のテキストの表示非環境フォント。**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>クリックすると、ポップアップ ダイアログでチェック ボックスの結果  
 Windows Azure アプリケーションの発行 ウィザードで"すべてのロールに対してリモート デスクトップを有効にする チェック ボックスをクリックすると、すぐに、ポップアップ ダイアログで、Visual Studio のアンチ パターンが表示されます。 さらに、チェック ボックスのフィールドがいっぱいにならないチェック ボックスが選択されている後にもう 1 つの相互作用のアンチ パターンです。  
  
 ![チェック ボックスをオン pop&#45;をアンチ&#45;パターン](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後に、ダイアログ ボックスこと。**  
  
### <a name="hyperlink-anti-patterns"></a>ハイパーリンクのアンチ パターン  
 次の例には、2 つのアンチ パターンが含まれています。  
  
1. ポインターを合わせると赤色にすると、フォア グラウンドでは、フォントのサービスから適切な共有色が使用されていないことを意味します。  
  
2. 「詳細」は、概念説明トピックへのリンクの適切なテキストではありません。 ユーザーの目標は、任意の影響を理解してがについてさらに、ありません。  
  
   ![ハイパーリンクのアンチ&#45;パターン](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
   **色のサービスを無視し、「詳細」のハイパーリンクを使用して、Visual Studio のアンチ パターンが。**  
  
   **ソリューションの向上:** リンクをクリックして、ユーザーを求めるは質問が発生します。  
  
-   Windows Azure サービスのしくみ  
  
-   Windows Azure モバイル サービス プロジェクトを必要な場合  
  
#### <a name="using-click-here-for-links"></a>「ここをクリックしてください」リンクを使用してください。  
 ハイパーリンクを自己記述型にする必要があります。 「ここをクリックして」を使用するアンチ パターンまたは任意のようなバリエーションをお勧めします。  
  
 **不良:** 「新しいプロジェクトを作成する方法についてはここでクリックして」  
  
 **Good:** 「は作成方法は、新しいプロジェクトをでしょうか」。

