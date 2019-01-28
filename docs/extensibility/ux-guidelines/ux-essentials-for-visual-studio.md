---
title: Visual Studio 用の UX Essentials |Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac8fdabc54965d521df2552ad4f152b53a7be70a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997183"
---
# <a name="ux-essentials-for-visual-studio"></a>UX Essentials for Visual Studio
## <a name="best-practices"></a>ベスト プラクティス  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.Visual Studio 環境内で一貫しています。  
  
-   次の既存の[対話パターン](interaction-patterns-for-visual-studio.md)シェル内で。  
  
-   シェルのビジュアル言語と一致するように機能を設計および[職人気質要件](evaluation-tools-for-visual-studio.md)します。  
  
-   存在する場合は、共有のコマンドとコントロールを使用します。  
  
-   Visual Studio の階層とコンテキストを確立して、UI のドライブの方法を理解します。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.フォントと色の環境のサービスを使用します。  
  
-   UI は現在を尊重する必要があります[環境フォント](fonts-and-formatting-for-visual-studio.md)オプション ダイアログ ボックスで [フォントおよび色] ページでカスタマイズには、公開される場合を除きを設定します。  
  
-   UI 要素を使用する必要があります、 [VSColor Service](colors-and-styling-for-visual-studio.md)環境のトークンまたは機能固有のトークンを使用して共有します。  
  
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
 - Visual Studio Dev14 の最小解像度は**1280 x 720**します。 つまり、ある*可能*ユーザー エクスペリエンスが最適化ができない可能性がありますが、この解像度では、Visual Studio を使用します。 すべての側面は 1280 x 720 より低い解像度で使用できることの保証はありません。  
  
 - Visual Studio のターゲットの解決は**1366 x 768**します。 これはお約束が最も低い解像度、*良い*ユーザー エクスペリエンス。

 - 最初のダイアログの高さをする必要があります**700 ピクセルより小さい**、96 dpi で IDE のフレームの最小解像度内に収まるようにします。
  
### <a name="high-density-displays"></a>高密度が表示されます。  
 Visual Studio の UI は、Windows の状態でサポートされるすべての DPI スケール ファクターに適しています機能する必要があります。150%、200%、250% の場合は。  
  
## <a name="anti-patterns"></a>アンチ パターン  
 Visual Studio には、以下のガイドラインとベスト プラクティスは、UI の多くの例が含まれています。 一貫性を保つために、開発者は、多くの場合、製品 UI の設計パターンが構築していることに似ていますから借用します。 これは、リリースするという私たちのドライブのユーザーとの対話およびビジュアル デザインの一貫性を利用するは場合によっては優先順位付けの参加を解除またはスケジュールの制約のためのガイドラインに準拠しないいくつかの詳細と機能の有効なアプローチです。 このような場合は、たくないチームがこれらの「アンチ パターン」のいずれかのコピーを Visual Studio 環境内で不適切なまたは非整合な UI が急増するためです。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>必要なフィールド/設定の既定のエラー状態の表示  
  
#### <a name="feature-team-goals"></a>機能チームの目標  
  
-   構成する必要がある要素を追加することをユーザーに警告します。  
  
-   入力を必要とする領域に、ユーザーの注意を促します。  
  
#### <a name="anti-pattern-solution"></a>ソリューションのアンチ パターン  
 ユーザーがアクションを開始するとすぐに、およびタスクが完了する前に、構成が必要な領域の横に重大な停止アイコンをすぐに配置します。  
  
#### <a name="example-manifest-designer-declarations"></a>例:マニフェスト デザイナーの宣言  
 一覧に宣言を追加すると、すぐには、ユーザーが必要なプロパティを設定するまで引き続き発生するエラー状態で配置します。  
  
 この場合、アラートに使用されるアイコンが含まれているためにその他の問題がありますが、"&times;"アイコンの横にある共通の削除 アイコンを使用することはできませんので。 その結果、UI より不恰好コントロールを削除 ボタンを使用します。  
  
 ![既定では、エラー状態で UI を配置することは、Visual Studio のアンチ パターンです。](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti パターン")<br />既定では、エラー状態で UI を配置することは、Visual Studio のアンチ パターンです。
  
#### <a name="alternatives"></a>代替手段  
 この問題をより良いソリューションは、することです。  
  
-   警告なしの宣言を追加するユーザーを許可して、すぐに移動して、項目のプロパティを設定します。  
  
-   警告アイコン (ゴールド三角形) を追加するときにフォーカスが移動、項目からなど、リストに別の宣言を追加するか、デザイナー内のタブを変更しようとします。  
  
-   ユーザーは、宣言のプロパティを設定する前にタブを変更しようとすると、アプリケーションがビルドされないことを説明するダイアログをポップアップ表示 (または、どのような影響)、警告が解決されるまでです。 場合は、ユーザーがダイアログを閉じるし、タブか、アイコン (重大または警告、必要に応じて) に追加されます宣言 タブ。  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>UI を複数回のクリック  
  
#### <a name="feature-team-goals"></a>機能チームの目標  
 最初に説明テキストを表示することがなく、UI を消去するユーザーを禁止します。  
  
#### <a name="anti-pattern"></a>アンチ パターン  
 VS UI 内でさまざまな場所にビデオへのリンクを挿入するチームの決定の一般的なパターンに対して、"&times;"リンク"次回から表示しない"と閉じるボタンとツールヒントの説明とは、UX で指定され、代わりに、ドロップダウンを実装します。  

#### <a name="example-video-links-in-team-explorer"></a>例: チーム エクスプ ローラーでリンクされたビデオ
Visual Studio 内でのアンチ パターンは、UI を破棄する前に説明文を読み取るユーザーを強制します。 正しくデザインされた、ビデオのリンクをクリックして、ポインターを合わせると追加情報を含むヒントを表示する必要があります、"&times;"さらに操作を必要としないメッセージを無視する必要があります。


 ![説明のテキストを反&#45;パターン&#45;が正しくない](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />ビデオの正しくないリンク パターン
  
#### <a name="result"></a>結果  
 閉じるボタン (1 回のクリック) 単純なのではなく、ユーザーは 2 回のクリックを使用して、ビデオへのリンクが表示されるすべての場所では、UI を単純に無視するように強制します。  
  
#### <a name="alternatives"></a>代替手段  
 このような状況に適切な設計は Internet Explorer、Office、および Visual Studio に共通のパターンに準拠すること: ポインターを合わせると、ユーザーに、ツールヒントの説明を表示し、1 回のクリックには、UI が非表示にします。  
  
 ![説明のテキストを反&#45;パターン&#45;正しい](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti パターン修正")<br />ビデオの適切なリンク パターン
  
### <a name="using-command-bars-for-settings"></a>コマンド バーを使用して、設定  
 **図 A**このアンチ パターンを表します。 コマンドは、単に適用されるコマンド ボタンの下に設定します。 このスケッチの場合は、[デバッグ開始] 以外のコマンドがあります: などのブラウザー、デバッグなしで開始、およびステップ インでビュー-選択した設定を尊重します。  

  ![図 a:コマンド バーのアンチ パターン](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-パターン-FigureA")<br />図 a:コマンド バーのアンチ パターン
  
 ようにが少し向上の望ましくないが、ツールバーでこの種類の設定を配置する**図 B**します。分割ボタン領域が少なくなると改善をドロップダウン リストではそのため、中に両方の設計もを使用しているツールバーがありません。 実際にコマンドを昇格します。  
 
 ![図 b:良い、ですが、コマンド バーのアンチ パターンまだ](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-パターン-FigureB")<br />図 b:良い、でも、コマンド バーのアンチ パターン
 
  示すように、適切なアプローチで**図 C**設定は、一連のコマンドに関連付けられます。 設定されているグローバル設定がないとだけ、4 つのコマンドを切り替えしています。 これは、ツールバーのコマンドの許容可能な場合だけです。 

 ![図 c:Visual Studio のコマンド バーのパターンの使用を修正](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-パターン-FigureC")<br />図 c:Visual Studio のコマンド バーのパターンの正しい使用
   
### <a name="control-anti-patterns"></a>コントロールのアンチ パターン  
 いくつかのアンチ パターンは、単に不適切な使用方法またはコントロールまたはコントロールのグループのプレゼンテーションです。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>下線がハイパーリンクではないグループのラベルとして使用  
 ハイパーリンクのみのテキストに下線を使用する必要があります。  
  
 **正しくありません。**    
 ![ハイパーリンクが下線付きのテキストは、Visual Studio のアンチ パターンです。](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />ハイパーリンクが下線付きのテキストは、Visual Studio のアンチ パターンです。
  
 **よし：**   
 ![スタイルが正しく、ハイパーリンク以外のテキストの表示非環境フォント。](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />スタイルが正しく、ハイパーリンク以外のテキストの表示非環境フォント。
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>クリックすると、ポップアップ ダイアログでチェック ボックスの結果  
 Windows Azure アプリケーションの発行 ウィザードで"すべてのロールに対してリモート デスクトップを有効にする チェック ボックスをクリックすると、すぐに、ポップアップ ダイアログで、Visual Studio のアンチ パターンが表示されます。 さらに、チェック ボックスのフィールドがいっぱいにならないチェック ボックスが選択されている後にもう 1 つの相互作用のアンチ パターンです。  
  
 ![Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後に、ダイアログ ボックスこと。](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後に、ダイアログ ボックスこと。
  
### <a name="hyperlink-anti-patterns"></a>ハイパーリンクのアンチ パターン  
 次の例には、2 つのアンチ パターンが含まれています。  
  
1. ポインターを合わせると赤色にすると、フォア グラウンドでは、フォントのサービスから適切な共有色が使用されていないことを意味します。  
  
2. 「詳細」は、概念説明トピックへのリンクの適切なテキストではありません。 ユーザーの目標は、任意の影響を理解してがについてさらに、ありません。  
  
   ![色のサービスを無視し、「詳細」のハイパーリンクを使用して、Visual Studio のアンチ パターンが。](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />色のサービスを無視し、「詳細」のハイパーリンクを使用して、Visual Studio のアンチ パターンが。  
  
   **優れた解決方法:** リンクをクリックして、ユーザーを求めるは質問をもたらします。  
  
-   Windows Azure サービスのしくみ  
  
-   Windows Azure モバイル サービス プロジェクトを必要な場合  
  
#### <a name="using-click-here-for-links"></a>「ここをクリックしてください」リンクを使用してください。  
 ハイパーリンクを自己記述型にする必要があります。 「ここをクリックして」を使用するアンチ パターンまたは任意のようなバリエーションをお勧めします。  
  
 **正しくありません。** ここをクリックして新しいプロジェクトを作成する方法についてはします。
  
 **よし：**「は作成方法は、新しいプロジェクトをでしょうか。」