---
title: "Visual Studio の UX Essentials |Microsoft ドキュメント"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f9d04da421b3b59609269b4f91a487d22adc80e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio の UX Essentials
## <a name="best-practices"></a>ベスト プラクティス  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.Visual Studio 環境内で一貫しています。  
  
-   次の既存の[相互作用のパターン](interaction-patterns-for-visual-studio.md)シェル内で。  
  
-   シェルのビジュアルな言語と一致するように機能を設計および[職人気質要件](evaluation-tools-for-visual-studio.md)です。  
  
-   存在する場合は、共有のコマンドとコントロールを使用します。  
  
-   Visual Studio の階層とコンテキストを確立し、UI のドライブ、方法を理解します。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.フォントと色の環境のサービスを使用します。  
  
-   UI は、現在を考慮する必要があります[環境フォント](fonts-and-formatting-for-visual-studio.md)カスタマイズのオプションダイアログ ボックスに、[フォントおよび色] ページでは、公開される場合を除きを設定します。  
  
-   UI 要素を使用する必要があります、 [VSColor サービス](colors-and-styling-for-visual-studio.md)環境のトークンや機能に固有のトークンを使用して共有します。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.新しい VS スタイルで一貫性のあるすべての画像を確認します。  
  
-   アイコン、記号、およびその他のグラフィックスの Visual Studio デザインの原則に従います。  
  
-   グラフィック要素のテキストを配置しないでください。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.ユーザー中心の観点からデザインします。  
  
-   内の個々 の機能の前にタスク フローを作成します。  
  
-   ユーザーと理解しておくし、仕様にその知識を明示します。  
  
-   UI を表示するときに、完全なエクスペリエンスだけでなく、詳細情報を評価します。  
  
-   機能していて、ロケールや言語に関係なく魅力的なままになるように、UI を設計します。  
  
## <a name="screen-resolution"></a>画面の解像度  
  
### <a name="minimum-resolution"></a>最小解像度  
 - Visual Studio Dev14 の最小解像度が**1280 x 720**です。 つまり、ある*考えられる*ユーザー エクスペリエンスが最適化ができない可能性がありますが、この解像度では、Visual Studio を使用します。 すべての側面が 1280 x 720 より低い解像度で使用できるようになるという保証はありません。  
  
 - Visual Studio のターゲットの解決**1366 x 768**です。 これは、ことをお約束する最も低い解像度、*良い*ユーザー エクスペリエンスです。

 - 最初のダイアログの高さにする必要があります**700 ピクセルより小さい**96 dpi で IDE フレームの最小単位に収まるように、します。
  
### <a name="high-density-displays"></a>高密度が表示されます。  
 Visual Studio では、UI は、スケール係数すぐ Windows でサポートされるすべての DPI で正常に動作する必要があります: 150%、200%、250% です。  
  
## <a name="anti-patterns"></a>アンチ パターン  
 Visual Studio には、当社のガイドラインとベスト プラクティスに従う UI の多くの例が含まれています。 一貫性を保つために、開発者は、多くの場合、製品 UI のデザイン パターンがビルド中に似ています借用します。 これは、us ドライブのユーザーとの対話とビジュアル デ ザインの一貫性を利用するには、おは場合によっては状態で出荷するスケジュールの制約のためのガイドラインを満たしているしないでください。 または優先順位付けの参加を解除するいくつかの詳細と機能を有効なアプローチです。 このような場合は、必要のないチームはこれらの「アンチ パターン」のいずれかのコピーを Visual Studio 環境内で不適切なや一貫性のない UI が急増するためです。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>既定ではエラー状態に表示される必須のフィールド/設定  
  
#### <a name="feature-team-goals"></a>機能チームのゴール  
  
-   構成する必要がある要素を追加したことをユーザーに警告します。  
  
-   入力を必要とする領域に、ユーザーの注目を描画します。  
  
#### <a name="anti-pattern-solution"></a>ソリューションのアンチ パターン  
 ユーザーがアクションを開始するとすぐに、タスクが完了する前に、構成が必要な領域の横にある重大な停止アイコンをすぐに配置します。  
  
#### <a name="example-manifest-designer-declarations"></a>例: マニフェスト デザイナーの宣言  
 一覧に宣言を追加すると、すぐには、ユーザーが必要なプロパティを設定するまで引き続き発生するエラー状態で配置します。  
  
 ここではその他の問題、通知に使用されるアイコンが含まれているため、"&times;"アイコン、ため、その横にある共通の削除 アイコンを使用することはできません。 その結果、UI より扱いコントロール削除 ボタンを使用します。  
  
 ![既定では、エラー状態に UI を配置することは、Visual Studio のアンチ パターンです。] (../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti パターン")<br />既定では、エラー状態に UI を配置することは、Visual Studio のアンチ パターンです。
  
#### <a name="alternatives"></a>代替手段  
 この問題をより良いソリューションになります。  
  
-   警告なしの宣言を追加するユーザーを許可して、すぐに移動して、項目のプロパティを設定します。  
  
-   警告アイコン (ゴールドの三角形) を追加するときにフォーカスが移動、項目からなど、一覧に別の宣言を追加するか、デザイナー内のタブを変更しようとします。  
  
-   ユーザーのすべての宣言でプロパティを設定する前にタブを変更しようとすると、pop、アプリケーションがビルドされませんを説明するダイアログ ボックス (または、どのような影響)、警告が解決されるまでです。 場合は、ユーザーがダイアログを閉じるし、タブか、アイコン (重大または警告、必要に応じて) はタブに追加宣言します。  
  
### <a name="multiple-clicks-to-dismiss-ui"></a>複数回のクリックを UI を閉じます  
  
#### <a name="feature-team-goals"></a>機能チームのゴール  
 ユーザーが最初に説明テキストを表示せずに、UI を閉じますを許可しません。  
  
#### <a name="anti-pattern"></a>アンチ パターン  
 VS UI 内でのさまざまな場所にビデオへのリンクを挿入するチームの一般的なパターンに対してという合意に、"&times;"リンク「を表示しない再度」および閉じるボタンとツールヒントの説明とは、ユーザー エクスペリエンス、によって指定され、ドロップダウン リストを実装します。  

#### <a name="example-video-links-in-team-explorer"></a>例: チーム エクスプ ローラーでリンクされたビデオ
Visual Studio 内でのアンチ パターンは、UI を消去する前に説明文を読み取るユーザーを強制します。 正しくデザインされた、ビデオへのリンクをクリックしてのホバー時追加情報を含むツールヒントを表示する必要があります、"&times;"さらに操作することがなく、メッセージを破棄する必要があります。


 ![説明テキストをアンチ &#45; パターン &#45;正しくない](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />ビデオの正しくないリンク パターン
  
#### <a name="result"></a>結果  
 閉じるボタン (1 回のクリック) 単純なのではなくを 2 回のクリックを使用して、単にビデオへのリンクが表示されるすべての場所に UI を消去する求められます。  
  
#### <a name="alternatives"></a>代替手段  
 このような状況に対応する正しい設計に Internet Explorer、Office、および Visual Studio に共通のパターンに従うになります: ホバー時、ユーザーはツールヒントの説明を確認し、1 回のクリックは、UI を非表示にします。  
  
 ![説明テキストをアンチ &#45; パターン &#45;正しい](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti パターン解決")<br />ビデオの適切なリンクのパターン
  
### <a name="using-command-bars-for-settings"></a>コマンド バーを使用して、設定  
 **図 A**このアンチ パターンを表します。 コマンドは、単に適用されるコマンド ボタンの下に設定します。 このスケッチの場合は、デバッグの開始だけでなくコマンド — などのブラウザーで、デバッグなしで、ステップ イン ビュー-選択した設定を尊重します。  

  ![図 a: がコマンド バーのアンチ パターン](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti パターン-FigureA")<br />図 a: コマンド バーのアンチ パターン
  
 示すように、少し良いそれでもの望ましくないが、ツールバーでこの種類の設定を配置する**図 B**です。分割ボタンは、小さい領域を行い、改善をドロップダウン リストではそのため、中に両方の設計もを使用しているツールバーを実際にコマンドではないを昇格させます。  
 
 ![図 b: より優れたですが、まだコマンド バーのアンチ パターン](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti パターン-FigureB")<br />図 b: 向上ですが、まだコマンド バーのアンチ パターン
 
  示すように適切なアプローチで**図 C**設定が一連のコマンドに関連付けられています。 設定されているグローバル設定はなく、同様、4 つのコマンドを切り替えおしています。 これは、ツールバーのコマンドが許容である場合だけです。 

 ![図 c: Visual Studio のコマンド バーのパターンの使用の解決](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti パターン-FigureC")<br />Visual Studio のコマンド バーのパターンの図 c: の正しい使用します。
   
### <a name="control-anti-patterns"></a>コントロールのアンチ パターン  
 いくつかのアンチ パターンは、単に不適切な使用法またはコントロールまたはコントロールのグループのプレゼンテーションです。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>ハイパーリンクではない、グループ ラベルとして使用する下線  
 のみのハイパーリンクのテキストに下線を使用してください。  
  
 **正しくありません。**    
 ![ハイパーリンクではありません下線付きのテキストは、Visual Studio のアンチ パターンです。] (../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")<br />ハイパーリンクではありません下線付きのテキストは、Visual Studio のアンチ パターンです。
  
 **よし：**   
 ![スタイルを正しく、非ハイパーリンク テキスト非装飾環境のフォントで表示します。] (../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")<br />スタイルを正しく、非ハイパーリンク テキスト非装飾環境のフォントで表示します。
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>ポップアップ ダイアログでチェック ボックスの結果をクリックすると  
 「Windows Azure アプリケーションの公開」ウィザードの"すべてロールのリモート デスクトップを有効にする チェック ボックスをクリックするすぐにポップアップ ダイアログで、Visual Studio のアンチ パターンが表示されます。 さらに、チェック ボックスのフィールドがいっぱいにならないチェック ボックスが選択されている後に別の相互作用のアンチ パターン。  
  
 ![Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後にダイアログ ボックスをことをします。] (../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")<br />Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後にダイアログ ボックスをことをします。
  
### <a name="hyperlink-anti-patterns"></a>ハイパーリンクのアンチ パターン  
 次の例には、次の 2 つのアンチ パターンが含まれています。  
  
1.  ホバー時の赤にすると、フォア グラウンドでは、フォント サービスから、適切な共有色が使用されていないことを意味します。  
  
2.  「詳細」は、概念に関するトピックへのリンクの適切なテキストではありません。 ユーザーの目標は、詳細は、任意の影響を理解していないです。  
  
 ![色のサービスを無視し、「詳細」のハイパーリンクを使用して Visual Studio のアンチ パターンは、します。] (../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")<br />色のサービスを無視し、「詳細」のハイパーリンクを使用して Visual Studio のアンチ パターンは、します。  
  
 **ソリューションのより強力な:**リンクをクリックして、ユーザーを求めるは質問が発生します。  
  
-   Windows Azure サービスのしくみ  
  
-   Windows Azure モバイル サービス プロジェクトを必要がある場合ですか。  
  
#### <a name="using-click-here-for-links"></a>「ここをクリックして」へのリンクを使用します。  
 ハイパーリンクは、自己記述型にする必要があります。 「ここをクリックして」を使用するアンチ パターンまたはそのような違いをお勧めします。  
  
 **不適切な:** 「ここをクリックして新しいプロジェクトを作成する方法についてはします」。
  
 **Good:** 「どのようにプロジェクトは作成、新しいですか?」