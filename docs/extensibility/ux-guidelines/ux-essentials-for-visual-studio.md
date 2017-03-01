---
title: "Visual Studio の UX Essentials |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7f10e2cefc0986a2457cc61945a60acfd1a4ef78
ms.lasthandoff: 02/22/2017

---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio のユーザー エクスペリエンスの要点
## <a name="best-practices"></a>ベスト プラクティス  
  
### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1.Visual Studio 環境内で一貫しています。  
  
-   シェル内で既存の相互作用のパターンに従います。  
  
-   シェルのビジュアル言語と職人気質の要件と一致する機能を設計します。  
  
-   存在する場合は、共有のコマンドとコントロールを使用します。  
  
-   Visual Studio 階層と、どのコンテキストを確立し、そのドライブの UI を理解します。  
  
### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2.フォントと色の環境のサービスを使用します。  
  
-   UI は、カスタマイズ オプション ダイアログ ボックスで フォントおよび色 ページで公開される場合を除き、現在の環境フォント設定を尊重必要があります。  
  
-   UI 要素には、共有環境トークンまたは機能固有のトークンを使用して、VSColor サービスを使用する必要があります。  
  
### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3.新しい VS スタイルで一貫性のあるすべての画像を確認します。  
  
-   アイコン、グリフ、およびその他のグラフィックスの Visual Studio のデザインの原則に従います。  
  
-   グラフィック要素のテキストを配置しないでください。  
  
### <a name="4-design-from-a-user-centric-perspective"></a>4.ユーザー中心の観点から設計します。  
  
-   内の個々 の機能の前にタスク フローを作成します。  
  
-   ユーザーを理解しておくし、その知識を spec ファイルで明示的にします。  
  
-   UI を確認するときは、詳細情報と同様に包括的なエクスペリエンスを評価します。  
  
-   機能していて、ロケール、または言語に関係なく魅力的なままになるように UI を設計します。  
  
## <a name="screen-resolution"></a>画面の解像度  
  
### <a name="minimum-resolution"></a>解像度の最小  
 Visual Studio Dev14 の最低限の解像度は、1280 x 1024 です。 つまり、ある*可能な*最適なユーザー エクスペリエンスができない場合がありますが、この解像度では、Visual Studio を使用しています。 すべての側面が 1280 × 1024 より低い解像度では使用される保証はありません。  
  
 最初のダイアログのサイズでは、この最小解像度を使用して 96 dpi 内で IDE のフレーム内に収まるようために高さ 1000 ピクセルを超えることはできません。  
  
### <a name="high-density-displays"></a>高密度が表示されます。  
 Visual Studio での UI は、すべての DPI スケール変換があらかじめ Windows でサポートされる要素で正常に動作する必要があります: 150%、200%、250% です。  
  
## <a name="anti-patterns"></a>アンチ パターン  
 Visual Studio には、次のガイドラインとベスト プラクティスは、UI の多くの例が含まれています。 一貫性を維持するために、開発者は、多くの場合、製品 UI の設計パターンが構築しているようなから借用します。 これは、こと私たちのドライブのユーザーとの対話と視覚的なデザインの一貫性を利用するは場合によってはまず優先順位付けの参加を解除またはスケジュールの制約のためのガイドラインに準拠しないいくつかの詳細を含む機能の有効なアプローチです。 このような場合は、させませんチームがこれらの「アンチ パターン」の&1; つをコピーする Visual Studio 環境内で不適切か、矛盾した UI を大幅に増えているためです。  
  
### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>既定では、エラー状態に示すように必要なフィールド/設定  
  
#### <a name="feature-team-goals"></a>機能チームのゴール  
  
-   構成する必要がある要素を追加したことをユーザーに警告します。  
  
-   入力を必要とする領域に、ユーザーの注意を促します。  
  
#### <a name="anti-pattern-solution"></a>ソリューションのアンチ パターン  
 ユーザーがアクションを開始するとすぐに、タスクが完了する前に、すぐに構成を必要とする領域の横にある重要な分岐点のアイコンを配置します。  
  
#### <a name="example-manifest-designer-declarations"></a>例: マニフェスト デザイナーの宣言  
 一覧に宣言を追加すると、すぐには、ユーザーが必要なプロパティを設定するまで引き続き発生するエラー状態で配置します。  
  
 ここで、通知に使用されるアイコンには、"x"が含まれているため、その他の問題があるの横にアイコンを使用できないので、一般的なを削除します。 その結果、UI がより不恰好コントロール削除 ボタンを使用します。  
  
 ![マニフェスト デザイナー エラー宣言のアンチ パターン](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti パターン")  
  
 **既定では、エラー状態で UI を配置することは、Visual Studio のアンチ パターンです。**  
  
#### <a name="alternatives"></a>代替手段  
 この問題は、もっと良い方法もあります。  
  
-   ユーザーが警告なしの宣言を追加できるようにし、次に、すぐに移動して、項目のプロパティを設定します。  
  
-   警告アイコン (ゴールド三角形) を追加する場合またはフォーカスが移動、項目からなど、一覧に別の宣言を追加するデザイナー内でタブを変更しようとします。  
  
-   ユーザーは、すべての宣言のプロパティを設定する前にタブを変更しようとすると、アプリケーションがビルドされないことを説明するダイアログをポップアップ表示 (または、どのような影響)、警告が解決されるまでです。 ユーザーがダイアログ ボックスを閉じるし、タブか、アイコン (重大または警告 をクリック) が追加宣言 タブにされます。  
  
### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>UI を破棄する前にテキストを読み取るユーザーの強制  
  
#### <a name="feature-team-goals"></a>機能チームのゴール  
 説明テキストを表示せずに、UI を閉じますにユーザーを禁止します。  
  
#### <a name="anti-pattern"></a>アンチ パターン  
 X の一般的なパターンを担う VS UI 内でのさまざまな場所にリンクされたビデオを挿入するチームは、ユーザー エクスペリエンスで指定されたボタンとツールヒントの説明を閉じて、代わりに、ドロップダウン リストと「を表示しないもう一度」リンクを実装します。  
  
 ![説明テキストのアンチ パターン-正しくない](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")  
  
 **正しくない: Visual Studio 内でのアンチ パターンを UI を破棄する前に説明文を読み取るユーザーの強制です。**  
  
#### <a name="result"></a>結果  
 閉じるボタン (1 回のクリック) 単純なのではなく、ユーザーを強制して、2 回のクリックを使用して、単にビデオのリンクが表示されるすべての場所に UI を閉じます。  
  
#### <a name="alternatives"></a>代替手段  
 この状況に正しく設計は Internet Explorer、Office、および Visual Studio に共通のパターンに準拠する: ホバー時、ユーザーは、tooltip の説明を確認し、1 回のクリックは、UI を非表示にします。  
  
 ![説明テキストのアンチ パターン-正しい](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti パターン修正")  
  
 **正しい: ビデオへのリンクが、ホバー時の追加情報を含むツールヒントを表示、設計どおりにし、[X] をクリックするとさらに対話することがなく、メッセージを消去します。**  
  
### <a name="using-command-bars-for-settings"></a>コマンド バー設定を使用します。  
 ![コマンド バーのアンチ パターン-図 A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti パターン-FigureA")  
  
 **図 a: コマンド バーのアンチ パターン**  
  
 **図 A**このアンチ パターンを表します。 コマンドは、単に適用されるコマンド ボタンの下に設定します。 このスケッチでは、[デバッグ開始] 以外のコマンドは、ブラウザー、デバッグなしで開始、およびステップ インでビューなど-は、選択した設定を尊重します。  
  
 ![コマンド バーのアンチ パターン-図 B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti パターン-FigureB")  
  
 **図 b: 優れたですが、まだコマンド バーのアンチ パターン**  
  
 ように、わずかに良いそれでもの望ましくないが、ツールバーでこの種類の設定を配置する**図 B**します。分割ボタンは、小さい領域おり、改善をドロップダウン リストではそのため、両方の設計を使用しているツールバーがありません。 実際にコマンドを昇格します。  
  
 ![コマンド バーのアンチ パターン-図 C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti パターン-FigureC")  
  
 **Visual Studio のコマンド バーのパターンの図 c: の正しい使用します。**  
  
 **図 C**設定は、一連のコマンドに関連付けられます。 設定されているグローバルの設定はなく、お&4; つのコマンドの間で切り替えるだけです。 これは、ツールバーのコマンドで許容される場合だけです。  
  
### <a name="control-anti-patterns"></a>コントロールのアンチ パターン  
 いくつかアンチ パターンは、単に不適切な使用またはコントロールまたはコントロールのグループのプレゼンテーションです。  
  
#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>ハイパーリンクではないグループのラベルとして使用される基礎となります。  
 のみのハイパーリンクのテキストに下線を使用してください。  
  
 **正しくありません。**  
  
 ![下線付きの文字グループのラベルになるアンチ パターン](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102 g_GroupLabelIncorrect")  
  
 **ハイパーリンクではありません下線付きのテキストは、Visual Studio のアンチ パターンです。**  
  
 **よし：**  
  
 ![下線付きの文字グループのラベル (正しい) になるアンチ パターン](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102 h_GroupLabelCorrect")  
  
 **スタイルが正しく、非ハイパーリンク テキスト修飾環境のフォントで表示します。**  
  
#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>ポップアップ ダイアログでチェック ボックスの結果をクリックすると  
 Windows Azure アプリケーションの発行 ウィザードでの"すべての役割のリモート デスクトップを有効にする チェック ボックスをクリックすると、すぐに、ポップアップ ダイアログで、Visual Studio のアンチ パターンが表示されます。 さらに、チェック ボックス フィールドを満たせないでチェック ボックスを選択した後は別の相互作用のアンチ パターンです。  
  
 ![チェック ボックス ポップアップのアンチ パターン](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102 i_CheckboxPopup")  
  
 **Visual Studio のアンチ パターンは、チェック ボックスをクリックすると後に、ダイアログ ボックスが表示することです。**  
  
### <a name="hyperlink-anti-patterns"></a>ハイパーリンクのアンチ パターン  
 次の例には、2 つのアンチ パターンが含まれています。  
  
1.  ホバー時の赤にフォア グラウンドでは、フォント サービスから、適切な共有色が使用されていないことを意味します。  
  
2.  「詳細」は、概念的なトピックへのリンクの適切なテキストではありません。 ユーザーの目的については、任意の影響を理解していないです。  
  
 ![ハイパーリンクのアンチ パターン](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102 j_HyperlinkIncorrect")  
  
 **色のサービスを無視し、「詳細」のハイパーリンクを使用して、Visual Studio のアンチ パターンです。**  
  
 **ソリューションの向上:**ユーザーは、リンクをクリックして確認すると問題が発生します。  
  
-   Windows Azure サービスのしくみ  
  
-   Windows Azure モバイル サービス プロジェクトを必要がある場合は?  
  
#### <a name="using-click-here-for-links"></a>「クリックして」のリンクを使用します。  
 ハイパーリンクは、自己記述型にする必要があります。 アンチ パターン「ここをクリックして」を使用するか、いずれかのようなバリエーションをお勧めします。  
  
 **不良:** 「ここをクリックして新しいプロジェクトを作成する方法についてです」。  
  
 **Good:** 「どのように教えて新しいプロジェクト」
