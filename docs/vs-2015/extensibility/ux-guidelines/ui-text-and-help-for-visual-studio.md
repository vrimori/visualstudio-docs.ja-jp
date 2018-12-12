---
title: UI テキストと Visual Studio のヘルプ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 208fdec375927c53c185465b4ded05f7ed3fb406
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777475"
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI テキストと Visual Studio のヘルプ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_UITextAndTerminology"></a> UI テキストと用語  
 わかりやすくテキストは、効果的な UI に非常に重要です。 ソフトウェアのユーザーが読み取る傾向があるラベルを最初に、つまり、手元のタスクの完了に最も関連します。 静的テキストは、少ない頻度で読み取られます。 この概算の順序では、UI の読み取り後に、ウィンドウ全体のクイック スキャンでの作業セッションを開始するユーザーを計画します。  
  
1.  対話型のコントロール センター  
  
2.  コミット ボタン  
  
3.  対話型のコントロールが別の場所が見つかりません  
  
4.  主な手順  
  
5.  補足の説明  
  
6.  ウィンドウのタイトル  
  
7.  メインの本文でその他の静的なテキスト  
  
### <a name="usage-patterns-for-ui-text"></a>UI テキストの使用パターン  
  
#### <a name="title-bar-text"></a>タイトル バーのテキスト  
 タイトル バーのテキストは、UI を生成するコマンドと一致する必要があります。  
  
#### <a name="instructional-text-helper-text"></a>説明のテキスト (ヘルパー テキスト)  
 一部のダイアログで、メイン ウィンドウまたはページの対処方法を説明する手順については、著名なを提供することをお勧めします。 これとも呼ば"ヘルパー text"です。  
  
##### <a name="writing-style-rules-for-helper-text"></a>ヘルパー テキストに対するスタイル ルールの作成  
  
-   明らかな原因を説明しません。 絶対に必要な場合を除きでは、説明のテキストは含まれません。  
  
-   説明のテキストは、ダイアログの上部にある常に配置され、実行されているタスクを参照してください。  
  
-   正確に、実行に必要な説明もユーザーにします。 過剰な通信と冗長性を回避します。  
  
-   各ウィンドウを確認し、重複する単語とステートメントを排除します。  
  
-   短い説明のテキストを保持します。 詳細については、必要な特定のユーザーまたはシナリオには場合、は、詳細な概念のオンライン トピックへのリンクを提供します。  
  
-   すべての単語の重みを保持し、必要がありますようにテキストを書きます。  
  
-   既存の Microsoft ガイダンスに従って[ユーザー インターフェイス テキスト](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)と[スタイルとトーン](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)します。  
  
#### <a name="supplemental-instructions"></a>補足手順  
 補足の手順では、ユーザー コントロールを理解するか、またはグループの制御に役立つ追加情報を提供します。 ヒントのテキスト入力コントロールで想定されるどのような形式を理解するために必要な可能性があります。 補足の手順を慎重に使用します。 ユーザーがれる任意の影響を完全に理解しない可能性が高いことがある場合に、これらを予約します。  
  
 ![Visual Studio での補足テキスト](../../extensibility/ux-guidelines/media/0601-b-supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Visual Studio での補足テキスト**  
  
 ![Visual Studio での補足テキスト](../../extensibility/ux-guidelines/media/0601-c-supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Visual Studio での補足テキスト**  
  
#### <a name="infotips"></a>ヒント  
 多くの場合、説明のテキストは、UI で、インプレースを配置するのには長過ぎる場合があります。 または煩雑さに慣れているユーザーのように感じて、新しいユーザーにのみ便利な場合があります。 この場合、ヒントの下のツールヒントとして/情報では説明のテキストを配置する必要があります。  
  
 ヒントは、顕著に関連して、特定のヒントのアイコンはまだ目障りを使用する必要がありますが、コントロールの近くに配置する必要があります。  
  
 ![Visual Studio でのヒント](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **Visual Studio のヒントの例**  
  
##### <a name="writing-style-rules-for-infotips"></a>ヒントのスタイル ルールの書き込み  
  
-   ヒントは、完全な文として記述します。 特定の動詞、文のケースと末尾に句点を必要とします。  
  
-   ヒントを使用して、メイン インストラクションや情報を補完します。 主要なアイデアをもう一度説明別の単語を使用した場合、ヒントは不要です。  
  
-   ヒントを簡潔にしてください。 スモール ワードと形式を使用して日常的な言語をサポートし、ユーザーをお勧めしています。  
  
-   既存の Microsoft ガイダンスに従って[ユーザー インターフェイス テキスト](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)と[スタイルとトーン](https://msdn.microsoft.com/library/windows/desktop/dn742477\(v=vs.85\).aspx)します。  
  
#### <a name="control-labels"></a>コントロールのラベル  
 コントロールのラベルが短い、簡潔とに従ってください、[コントロールについては、Windows デスクトップ](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)します。  
  
 コントロール ラベルの書式と、UI 内での配置の詳細についてを参照してください[Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md)します。  
  
#### <a name="help-links"></a>ヘルプ リンク  
 ヘルプ リンクは、指示テキスト内でまたは UI の本文か配置できます。 ヘルプへのリンク ダイアログ ボックスの内部を起動したりできます。  
  
##### <a name="visual-style-rules-for-help-links"></a>ヘルプ リンク用の visual スタイル規則  
  
-   ハイパーリンクの適切な環境の色を使用します。 正しくスタイル設定されたハイパーリンクがクリックされたときの red はについて簡単に点滅しません。 これを表示する場合は、環境の色が使用されていないことを示す値です。  
  
-   下線は、ホバーまたは段落内のリンクが埋め込まれたときにのみ使用する必要があります。  
  
-   ハイパーリンクの表示と対話のスタイルの詳細については、ボタンやハイパーリンクを参照してください。  
  
##### <a name="writing-style-rules-for-help-links"></a>ヘルプ リンクのスタイル ルールの作成  
  
-   ダイアログ ボックスを起動するときに、省略記号の標準を維持します。 タスクには、追加の UI が必要な場合は、省略記号ボタンを移動するための省略記号なし。  
  
     ![Visual Studio でのヘルプ リンク](../../extensibility/ux-guidelines/media/0601-e-helplink.png "0601 e_HelpLink")  
  
     **ヘルプ リンクで省略記号 (...) は、追加の UI が必要なタスクを示します。**  
  
-   リンクは必要があります、ユーザーの意図でないために、「学んで、」で開始できません。 ユーザーは、特定の質問に回答を一般的な教育は表示されませんが。  
  
-   語句のヘルプにリンクが質問のトピックに応答するようにします。  
  
     正しくありません。  
     「Windows Azure Mobile Services の価格の詳細について説明します」  
  
     そうです：  
     「どのような価格オプションは、Windows Azure Mobile Services の使用可能な」でしょうか。  
  
-   使用しないでください*をクリックしています.* リンクのテキスト。  
  
-   リンクの単語のみ「ここ」ことはありません。 これは、ハイパーリンク付きの単語のみの音声がスクリーン リーダーによっての問題が発生します。  
  
     正しくありません。  
     "Windows Azure Mobile Services での情報を検索**ここ**"  
  
     そうです：  
     「どのような価格オプションは、Windows Azure Mobile Services の使用可能な」でしょうか。  
  
-   ヘルプ リンクの正しい書き込みスタイルの詳細については、次を参照してください。、[ヘルプについては、Windows デスクトップ](https://msdn.microsoft.com/library/windows/desktop/dn742494\(v=vs.85\).aspx)します。  
  
#### <a name="hint-text"></a>ヒント テキスト  
 コントロール内で、またはコントロールの下のレベルのウォーターマークとしてヒント テキストが表示されます。 適切な VSColors トークンを使用してによって適用される正しい書式`Environment.GrayText`します。  
  
 これは、いくつかの形式で表示できます。  
  
-   コントロールのラベル: の代わりに  
  
     ![Visual Studio でテキストをヒント](../../extensibility/ux-guidelines/media/0601-f-hinttext1.png "0601 f_HintText1")  
  
-   ように指示して動詞。  
  
     ![Visual Studio でテキストをヒント](../../extensibility/ux-guidelines/media/0601-g-hinttext2.png "0601 g_HintText2")  
  
-   必要なエントリを示すテキスト。  
  
     ![Visual Studio でテキストをヒント](../../extensibility/ux-guidelines/media/0601-h-hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>ウォーターマーク テキスト  
 空のデザイン画面で、テキストを実行できるだけでなく、該当する場合、関連する他のウィンドウを開くリンクを提供するものを示す必要があります。  
  
 ![Visual Studio でのテキストの透かし](../../extensibility/ux-guidelines/media/0601-i-watermarktext.png "0601 i_WatermarkText")  
  
 **Visual Studio でのウォーターマーク テキストの例**  
  
### <a name="common-terminology"></a>一般的な用語  
  
|用語|説明|コメント|  
|----------|-----------------|-------------|  
|サインイン/サインアウト|動詞の web プロパティに認証を表すために、web の同義語として使用します。 内のクライアントとして使用しますこの 1 回最上位レベルの概念の IDE ユーザー接続は、ローミングや、ライセンスなどのより高度な機能は他のすべての接続で使用を提供する最上位レベルの id を表すとの間の署名します。|IDE ユーザーは、最上位の IDE ユーザーを表しているために、サインインを表す/動詞、サインアウトする必要がありますのみの機能です。|  
|接続/切断|機能のオンライン サービスへの接続を 1 つが維持される場所で使用します。|サーバー エクスプ ローラーでのみ使用できます、一度に 1 つのアクティブな Azure 接続、接続と切断の例に示します。|  
|追加/削除|非破壊的です。 追加またはものは、一覧から削除する場合に使用します。|TFS 接続マネージャーのサーバーの一覧 ダイアログでは、追加/削除の例を示します。|  
|削除|破壊的です。 要素が削除されている場合にのみ使用を完全に破棄またはディスクから削除します。|結果がディスクからファイルを削除する場合、プロンプトが必要です"delete"一般にします。|  
  
## <a name="error-messages"></a>エラー メッセージ  
  
### <a name="overview"></a>概要  
 エラーが発生します。 ユーザーが実行できる操作の制限の設定とは、回避のエラー メッセージを防止するうえでの実用的な第一歩です。 ただし、エラーが発生した場合、適切に記述されたエラー メッセージは、問題の軽減に長い道を移動できます。 エラー メッセージは、ほぼ間違いなく最も重要な種類の同期されていて、解決する必要がある問題があるため、ユーザーに表示される通知のいずれかです。 品質の低いエラー メッセージは、独自のエラーの原因を判断して、考えられる解決策でユーザーをままにします。  
  
 ユーザーは、過剰に注意を払い、またはユーザーに値を追加書き込みに必要なだけのメッセージが発生するために、わかりづらいエラー メッセージの場合は、停止可能性があります。 メッセージは、単に通知がある場合は、別の表示形式を使用します。  
  
### <a name="rules-for-creating-an-error-message"></a>エラー メッセージを作成するための規則  
  
-   エラー メッセージを構築するときに、対象ユーザーの適切なエラーのレベルを選択します。 該当する場合、ユーザーが行うことができます、アクションを提供する簡単な概要を目標とします。 ユーザーが知る必要がないものはすべての状態をしないでください。  
  
-   建設的な支援を提供します。 読み取りし、処理命令を含むエラー メッセージに簡単です。  
  
-   二重否定は使用しないでください。  
  
-   両方自動実行して、手動の文法およびスペル チェックを記述するすべてのエラー メッセージを確認します。  
  
-   複雑なエラー メッセージ、シーケンシャル通信をしないようにします。 エラー メッセージ、F1 フックアップを使用しないでください。 メッセージ自体は、十分な必要があります。  
  
-   適切なアイコンを使用します。  
  
-   質問を簡単に理解し、"Delete"と「キャンセル」などの明確な選択肢がありますボタンの使用  
  
-   警告を先に進むの結果がどのようになるかを明確にします。 ボタンには、その結果を示す必要があります。  
  
-   エラーの場合、ユーザーが何実行できる、問題を解決するについて説明します。 ボタンは操作をするか、「閉じる」と答える エラー メッセージを [OK] ボタンを使用しないでください。  
  
-   いくつかの質問を自問してみるエラー メッセージを構築するとき:  
  
    -   ユーザーがだけでこのエラーの問題を解決する方法を見つけることができますか。  
  
    -   ユーザーは、このエラーと同じボキャブラリを使用しますか。  
  
    -   このエラーがあいまいです。 または複数の状況で共有しますか。 場合は、方法はするガイド ユーザーに必要なソリューションでしょうか。  
  
#### <a name="build-errors"></a>ビルド エラー  
 Visual Studio は、ソフトウェア開発ツールであるために、コンパイル、変換、または開発者の作業をバイナリ形式に変換する手順をエンコード多くのコンポーネントがあります。 コンパイラは正しく作成されたファイルを処理できない場合、またはコンパイラ オプションが正しく設定されなかったときにこれらの変換エラーが発生することができます。  
  
 Visual Studio のユーザーには、膨大な数のビルド エラーを解決する開発時間を費やすことができます。 エラーがある依存関係、ときにエラー メッセージが適切に記述、これが難しく、エラーの原因を明らかにするために、この解決時間が増加します。  
  
 最適なビルド エラーは、オートコンプリート機能を提供しない Visual Studio は、最初の場所に出現するものと IntelliSense の波線を表示します。 スキーマの検証コントロールと同様のツールは、同じ種類のフィードバックを提供します。 これらのメカニズムは、事前にビルド エラーの可能性を緩和すること、適切な形式でコードを作成するユーザーを説明します。  
  
 Visual Studio では、ユーザーが読み取りおよびそのドキュメント ウィンドウ内で発生したエラーをナビゲートのツール ウィンドウを提供します。 ユーザーがすばやく大量のコードを移動し、問題の場所に直接移動ように、キーボード ショートカットが提供されます。 Visual Studio では、ユーザーは、エラーの詳細については、ヘルプ トピックに直接移動できるように、特定のヘルプ キーワード/コンテキスト ID に関連付けられる場合は、各ビルド エラーもできます。  
  
 明確で正確なビルド エラーを記述します。  
  
-   **わかりやすい言葉**ほとんどまたはまったくないコンパイラの専門用語に問題が説明します。 ビルド エラーのテキストを過度に技術的なすることはできません。  
  
-   **考えられる原因を説明します。** たとえば、"プロパティと値の間にコロンが不足している、' (プロパティ): (値)' の宣言です"。  
  
-   考えられる修正内容について詳しく説明します。 十分な空き領域がない場合は、対応するヘルプ トピックに追加の詳細情報を配置することがあります。  
  
### <a name="components-of-a-well-written-error-message"></a>適切に記述されたエラー メッセージのコンポーネント  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>エラー メッセージをシェル ダイアログ サービスを使用します。  
 シェルのダイアログ サービスを使用すると、メッセージの外観を制御できます: 特定のフォント — 個々 の要素を大幅に変更なし。 使用して、 **IErrorInfo**メカニズムおよびそれらのレポートを使用して**IVsUIShell::SetErrorInfo/ReportErrorInfo**。  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>有効かつ適切な通知、プレゼンテーションを選択します。  
 (同期の通知) のデータの損失を回避するために早急な対応が必要な場合は、重大な警告があるモーダル ダイアログ ボックスを使用します。 読まずメッセージを閉じるときの不適切な結果を招く可能性の場合は、重要なアイコンが予約されています。 データの損失は、アラーム レベル応答を必要とする重要な状況です。 "重大"アイコンの乱用には、ユーザーがその重要性が desensitizes します。 エラー メッセージは、本質的に情報がある場合は、モーダル ダイアログ ボックス (非同期の通知) に代わる方法を検討してください。  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>技術的な説明ではなく、問題が発生した理由のクリーンで簡潔な説明を提供します。  
 技術的な詳細については、内でユーザー負荷がかかりすぎるようにしてエラー メッセージを無視する可能性が高くなります。 適切なメッセージングの例:  
  
-   「要求されたファイルを開けません。」  
  
-   「インターネットに接続できません。」  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>問題を解決する方法についてを説明します。  
 ユーザーの提案、問題を解決する方法を提供します。 正直に言うユーザー修正案がない場合です。 テクニカル サポート、コミュニティのサポートなど、代替のオンライン ソースへの直接リンクを提供します。 ユーザーをポイントして、問題に関連する特定のオンライン情報をお試しください。 エラー ID は、ユーザーをその特定のエラーについてのディスカッション スレッドにリンクを検討してください。 適切なメッセージングの例:  
  
-   「確認は、インターネットに接続してこの操作をやり直してください。」  
  
-   「ファイルが存在して、それを開くアクセス許可があることを確認してください。」  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>短期保存とポイントには、メッセージを記述します。  
 エラー メッセージが表示できるを説明して、ソリューションが提供がも好きである場合に、まだ無視されます。 1 つのソリューションでは、[詳細] ボタンをプログレッシブの公開を使用します。 たとえば、短い説明/ソリューションを提供し、詳細ボタンの下の詳細。 ユーザーが選択したエラーの詳しい情報を読み取る場合、実行できます。  
  
 メッセージの言語は次のようになります。  
  
-   **ドメインの適切な。** ユーザーが認識言語を使用します。 お客様は、開発者は、多くの場合がないコンテキストと用語があります。  
  
-   **特定します。** あいまいな言い回しを回避し、関連するオブジェクトの特定の名前と場所を提供します。 たとえば、エラー メッセージ「文字が無効です」などに便利です。 文字? 「ファイルが見つかりませんでした。」 ファイルを指定しますか。  
  
-   **お勧めします。** ユーザーを非難したり、見下したりしないでください。 悪意のあるまたは侮辱的な言語の回避 (強制終了、実行、終了、致命的な無効な)。 叫んで考えることが多くの場合ととして読み取ることができませんが、大文字のテキストを回避します。 ユーモアを使用しないでください。  
  
-   **そうです。** (アルファ) であっても、正しいスペルと文法を使用します。 入力ミスは、不自然および厄介です。  
  
-   **適切なコンテキスト。** 適切なボタンのテキストを使用します。 [OK] ボタンを回避し、代わりに"Continue"または「はい/いいえ。」  
  
### <a name="error-message-examples"></a>エラー メッセージの例  
  
|良い|正しくありません。|  
|----------|---------|  
|"、ダイヤルする番号がサービスでは不要になった。 ください番号を確認しますと再度ダイヤルまたは 0 をオペレーターにダイヤルします。"|-"(449) エラー: 無効な数"<br />-"このハンドルされない例外エラーを示します、操作が正常に完了しました"。<br /><br /> ![Visual Studio での不適切なエラー メッセージ](../../extensibility/ux-guidelines/media/0602-a-errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>ヘルプへのアクセス  
  
### <a name="overview"></a>概要  
 MSDN のドキュメントの他は、Visual Studio ユーザーは、UI の中にユーザーを支援するいくつかのアクセス ポイントを持ちます。 これらのアクセス ポイントが常に使用できることを確認するには、機能チームは、環境によって提供されるヘルプ システムを活用する必要があります。 これらのアクセス ポイントは次のとおりです。  
  
-   **ダイアログの手順と補足テキスト。** 方向、または詳細については、画面またはヒント アイコンにマウスの使用可能な UI で提供する静的テキスト。  
  
-   **F1 ヘルプ**(エディターのみ)。 Visual Studio エディター内でユーザーが信頼できること、いつでも F1 キーを押してにより現在の選択範囲に固有のヘルプ トピック。 F1 キーに関連付けられているトピックが適切なや役に立つことを確認します。  
  
-   **ヘルプ トピックへのハイパーリンクです。** ダイアログ、ツール ウィンドウ、または、トピックの詳細については、テクノロジ、機能、またはタスクを実行する方法については、ユーザーを支援するためを起動するデザイン サーフェイス内のハイパーリンクです。  
  
-   **スマート タグと構成のダイアログ ボックスなどのヘルパー UI メカニズム。** これらのメカニズムは、UI 要素を理解するうえで、ユーザーを支援またはスマート タグまたはビルダーのダイアログ ボックスなどのタスクを容易にします。  
  
-   **UI のヘルプ ボタン**(非推奨)。 関連の F1 ヘルプ トピックにアクセスできるように、タイトル バーに表示されるインジケーター。  
  
### <a name="text"></a>テキスト  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>ダイアログ ボックスで、教育および補足テキスト  
 ダイアログの複雑なタスクをサポートする、または複雑なコントロールの近くに、ダイアログ ボックスの上部にある多くの場合、UI 内での説明のテキストを提供する必要があります。 参照してください[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)書き方の詳細について。  
  
#### <a name="infotips"></a>ヒント  
 多くの場合、説明のテキストは、UI 内の場所に配置するのには長過ぎる場合があります。 または煩雑さに慣れているユーザーのように感じて、新しいユーザーにのみ便利な場合があります。 この場合、ヒントの下のツールヒントとして/情報では説明のテキストを配置する必要があります。  
  
 ヒントは、顕著に関連して、特定のヒントのアイコンはまだ目障りを使用する必要がありますが、コントロールの近くに配置する必要があります。  
  
 ![Visual Studio でのヒント](../../extensibility/ux-guidelines/media/0601-d-infotip.png "0601 d_InfoTip")  
  
 **Visual Studio のヒントの例**  
  
### <a name="interactive-help-mechanisms"></a>対話型ヘルプ メカニズム  
  
#### <a name="f1-help"></a>F1 ヘルプ  
 F1 ヘルプが必要です、エディターや、デザイン サーフェイス内が Visual Studio 環境でない他の場所。  
  
#### <a name="hyperlinks-to-help-topics"></a>ヘルプ トピックへのハイパーリンク  
 ハイパーリンクは、アクションを実行、IDE 内で移動する、またはブラウザーでヘルプを起動に使用できます。 参照してください[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)言語と 07.10.01 についてボタンやハイパーリンクをビジュアルとレイアウトのガイドライン。  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>ヘルプ (非推奨) ダイアログのタイトル バーに [?] ボタン  
 ほとんどの場合、ダイアログ ボックスのタイトル バーのヘルプ [?] ボタンは非推奨とされます。 UI のトピックでは、不要になった、ドキュメント モデルの一部と、したがってがない場合、関連するトピックにリンクします。 基本的には、タイトル バーのボタンが F1 ヘルプと同じものと、ダイアログ ボックスでする必要はなくなりました。 場合によっては、これもできます、使用可能な概念や手順の詳細があることを示すインジケーターとしてハイパーリンクが新しい UI で使用されることがより一般的な。  
  
##### <a name="dialogs-created-through-the-environment"></a>環境を使って作成されたダイアログ ボックス  
 多くのシェルのダイアログ ボックスが作成された、 **VBDialogBoxParam**関数。 この共有関数は、移動で支援するために更新されました、**ヘルプ**ボタンをダイアログから、**でしょうか。** 旧バージョンとアーキテクチャを維持しながらボタンと互換性があり、拡張します。  
  
 具体的には、 **VBDialogBoxParam**関数は id がボタンのダイアログ テンプレート**IDHELP** (9) か、ラベル**ヘルプ**または **&のヘルプ**. 非表示にされて、ヘルプ ボタンが見つかった場合、 **WS_EX_CONTEXTHELP**配置 ダイアログにスタイルを追加、**でしょうか。** ダイアログのタイトル バーにボタンをクリックします。  
  
 スタックにダイアログ プロシージャをプッシュし、処理前のダイアログ プロシージャという名前のダイアログを起動、ダイアログ ボックスが作成されると、 **DialogPreProc**します。 ときに、**でしょうか。** ボタンをクリックすると、送信、 **WM_SYSCOMMAND**の**SC_CONTEXTHELP**  ダイアログ ボックス。 **DialogPreProc**このコマンドをキャプチャし、それを変更して、 **WM_HELP** 、元のダイアログ プロシージャに渡されるメッセージ  
  
 多くの環境が作成したダイアログ ボックスでは、ダイアログ ボックスのヘルプ ボタンがあります。 [ヘルプ] ボタンは、自動非表示になりのみ、ダイアログ ボックスが表示されたら、**でしょうか。** ボタンは機能します。 場合、**でしょうか。** ボタンはこれまで削除または、Windows で変更された、このソリューションで [ヘルプ] ボタン、元にすばやく移動できます。  
  
 このソリューションは、バグを引き起こす可能性のある 4 つの前提条件です。  
  
- ダイアログ ボックスの [ヘルプ] ボタンを**IDHELP** (9)。  
  
- ダイアログ ボックスが正しいよう、[ヘルプ] ボタンを非表示にします。  
  
- ダイアログ ボックスでは、winproc は置換しません。  
  
- ダイアログ ボックスは、別のダイアログ内では埋め込まれません。  
  
  ダイアログ msenv 内に存在して使用しない場合**VBDialogBoxParam**、活用することを調査**VBDialogBoxParam**独自のハンドラーを実装する前にします。  
  
##### <a name="dialogs-created-through-other-packages"></a>その他のパッケージを使って作成されたダイアログ ボックス  
 ダイアログの msenv の外部にある場合、独自のソリューションを実装することができます。 VSPackage で、共有ダイアログ クラスは、タイトル バーに、ボタンを移動または各ダイアログ ボックスで、ハンドラーの実装を検討してください。 次のコードでは、実装を開始するためのスケルトンは。  
  
```  
struct DLGPROCITEM  
{  
    FARPROC proc; // The info used to create the dialog.  
    DLGPROCITEM* procPrev;  
};  
  
DLGPROCITEM* g_dlgProcStack = NULL;  
  
// A dialog starter/wrapper function is used to push the new  
// dialog proc to the top of our dialog proc stack.  
  
int SomeDialogStarterFunction(hinst, id, proc, etc)  
{  
    if (g_dlgProcStack == NULL)  
    {  
        g_dlgProcStack = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = NULL;  
    }  
    else  
    {  
        DLGPROCITEM* procItem = new DLGPROCITEM;  
        g_dlgProcStack->procPrev = g_dlgProcStack;  
        g_dlgProcStack = procItem;  
    }  
}  
  
// Pop this dialog proc off the dialog proc stack.  
  
DialogBoxIndirectParam...(...)  
{  
    DLGPROCITEM* procItem = g_dlgProcStack->procPrev;  
    delete g_dlgProcStack;  
    g_dlgProcStack = procItem;  
}  
  
// A wrapper dialog procedure will allow us to capture the  
// SC_CONTEXTHELP button on the title bar from Windows and  
// forward it as a simple WM_HELP message back to the dialog.  
  
INT_PTR CALLBACK DialogPreProc(HWND hwndDlg, UINT uMsg,  
    WPARAM wParam, LPARAM lParam)  
{  
    if (uMsg == WM_SYSCOMMAND && wParam == SC_CONTEXTHELP)  
    {  
        uMsg = WM_HELP;  
        wParam = 0;  
        lParam = 0;  
    }  
    return CallWindowProc((WNDPROC)g_dlgProcStack->proc,  
        hwndDlg, uMsg, wParam, lParam);  
}  
```  
  
##### <a name="help-buttons-in-managed-code"></a>マネージ コードでヘルプ ボタン  
 ウィンドウのタイトル バーのヘルプ ボタンの既定の動作をオーバーライドすることは、マネージ コードで簡単です。 この動作を示す完全なデモ アプリケーションを次に示します。 基本的には、フォームをオーバーライドする必要があります**WndProc**メソッドと、火災の F1 ヘルプを要求する**SC_CONTEXTHELP**メッセージをインターセプトします。  
  
```  
using System;  
using System.Windows.Forms;  
  
public class HelpForm : Form  
{  
    private const int SC_CONTEXTHELP = 0xF180;  
    private const int WM_SYSCOMMAND = 0x0112;  
  
    public HelpForm()  
    {  
        this.ClientSize = new System.Drawing.Size(300, 250);  
        this.HelpButton = true;  
        this.MaximizeBox = false;  
        this.MinimizeBox = false;  
        this.Name = "HelpForm";  
        this.Text = "Help Form";  
    }  
  
    protected override void WndProc(ref Message m)  
    {  
        if (m.Msg == WM_SYSCOMMAND && SC_CONTEXTHELP == (int)m.WParam)  
            ShowHelp();  
        else  
            base.WndProc(ref m);  
    }  
  
    private void ShowHelp()  
    {  
        MessageBox.Show("F1 Help goes here.");  
    }  
  
     [STAThread]  
    static void Main()  
    {  
        Application.EnableVisualStyles();  
        Application.EnableRTLMirroring();  
        Application.Run(new HelpForm());  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio のフォントと書式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio のレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Visual Studio の通知と進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

