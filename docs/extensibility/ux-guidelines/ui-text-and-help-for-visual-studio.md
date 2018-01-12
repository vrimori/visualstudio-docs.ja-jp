---
title: "UI テキストと Visual Studio のヘルプ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8747d07-6c90-46cc-b425-55b589f7e9e4
caps.latest.revision: "2"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 555fd622f5655a69ba77f3905a39635e01831c76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ui-text-and-help-for-visual-studio"></a>UI テキストと Visual Studio のヘルプ
##  <a name="BKMK_UITextAndTerminology"></a>UI テキストと用語  
 わかりやすくテキストは、効果的な UI にとって不可欠です。 ソフトウェアのユーザーから傾向の読み取りにラベルを最初に、つまり、前のタスクを完了するために最も関連します。 静的なテキストが少ない頻度で読み取られます。 このおおよその順序で、UI の読み取り後に、ウィンドウ全体のクイック スキャンでの作業セッションを開始するユーザーを計画します。  
  
1.  中央の対話型コントロール  
  
2.  ボタンをコミットします。  
  
3.  対話型のコントロールが別の場所が見つかりません  
  
4.  主な手順  
  
5.  補足の説明  
  
6.  ウィンドウのタイトル  
  
7.  メイン ボディの他の静的なテキスト  
  
### <a name="usage-patterns-for-ui-text"></a>UI テキストの使用パターン  
  
#### <a name="title-bar-text"></a>タイトル バーのテキスト  
 タイトル バーのテキストは、UI を生成するコマンドと一致する必要があります。  
  
#### <a name="instructional-text-helper-text"></a>説明テキスト (ヘルパー テキスト)  
 一部のダイアログで、ウィンドウまたはページの対処方法を説明する目立つの主な指示を提供することをお勧めします。 これとも呼ば"ヘルパー text"です。  
  
##### <a name="writing-style-rules-for-helper-text"></a>ヘルパー テキストのスタイル ルールの作成  
  
-   しないわかりやすいことを説明します。 絶対に必要なしない限りでは、説明のテキストは含まれません。  
  
-   説明のテキストは常に、ダイアログ ボックスの上部に配置され、実行するタスクを参照してください。  
  
-   正確にユーザーに説明するために必要なです。 過剰な通信および冗長性を回避します。  
  
-   各ウィンドウを確認し、重複する単語および文を削除します。  
  
-   短い説明のテキストを保持します。 詳細については、必要な特定のユーザーまたはシナリオには場合、は、オンラインの概念の詳細なトピックへのリンクを提供します。  
  
-   すべての単語は、重みを保持し、必要ができるように、テキストを書きます。  
  
-   既存の Microsoft ガイダンスに従う[ユーザー インターフェイス テキスト](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)と[スタイルとトーン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)です。  
  
#### <a name="supplemental-instructions"></a>補足手順  
 補足的な手順については、ユーザー コントロールを理解するか、またはグループ化を制御するときに役立つ追加情報を提供します。 ヒントのテキスト入力コントロールが想定しているどのような形式を理解するために必要な可能性があります。 補足の手順を慎重に使用します。 ここでは、ユーザーが作成する任意の影響を及ぼす可能性を完全に理解しない可能性が高い場合に、これらを予約します。  
  
 ![Visual Studio での補足のテキスト](../../extensibility/ux-guidelines/media/0601-b_supplementaltext1.png "0601 b_SupplementalText1")  
  
 **Visual Studio での補足のテキスト**  
  
 ![Visual Studio での補足のテキスト](../../extensibility/ux-guidelines/media/0601-c_supplementaltext2.png "0601 c_SupplementalText2")  
  
 **Visual Studio での補足のテキスト**  
  
#### <a name="infotips"></a>ヒント  
 多くの場合、指示テキスト、UI のインプレースでの位置には長過ぎる場合がありますか、または経験豊富なユーザーに乱雑さと同様に自分で、新しいユーザーにのみ便利です。 この場合、ヒントの下のツールヒントとして、または情報の説明テキストを配置してください。  
  
 ヒントは、顕著なコントロールに関連する特定のヒントのアイコンは、使用されていない目障りを使用してそれらの近くに配置する必要があります。  
  
 ![Visual Studio でのヒント](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Visual Studio のヒントの例**  
  
##### <a name="writing-style-rules-for-infotips"></a>ヒントのスタイル ルールの書き込み  
  
-   完全な文章としてヒントを作成します。 特定の動詞で文の場合も、アドレスと終了区切り記号が必要です。  
  
-   ヒントを使用して、メイン命令または情報を補完します。 だけを使用するさまざまな単語を主な概念を再確認する場合、ヒントは不要です。  
  
-   ヒントを簡潔にしてください。 小規模の単語やプレーンを使用して日常的な言語をサポートしており、ユーザーのことをお勧めします。  
  
-   既存の Microsoft ガイダンスに従う[ユーザー インターフェイス テキスト](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx)と[スタイルとトーン](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742477\(v=vs.85\).aspx)です。  
  
#### <a name="control-labels"></a>コントロールのラベル  
 コントロールのラベルおよびすべき short、簡潔なに従って、[コントロール用の Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx)です。  
  
 コントロール ラベルの書式と、UI 内での配置の詳細についてを参照してください[for Visual Studio のレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md)です。  
  
#### <a name="help-links"></a>ヘルプ リンク  
 説明のテキスト内で、または UI の本体で、ヘルプ リンクを配置するか、できます。 ヘルプへのリンク内部ダイアログを起動したりできます。  
  
##### <a name="visual-style-rules-for-help-links"></a>ヘルプ リンク用の visual スタイル ルール  
  
-   ハイパーリンクの正しい環境の色を使用します。 正しくスタイル設定されたハイパーリンク クリックされたときに、赤はについて簡単に点滅しません。 これを表示する場合は、環境の色が使用されていないことを示しますが、します。  
  
-   下線は、ホバー時や段落内のリンクが埋め込まれたときにのみ使用してください。  
  
-   ハイパーリンクのビジュアルとの相互作用のスタイルの詳細については、ボタンとハイパーリンクを参照してください。  
  
##### <a name="writing-style-rules-for-help-links"></a>ヘルプのリンクのスタイル ルールの作成  
  
-   ダイアログ ボックスを起動するときに、省略記号の標準を維持します。 タスクは、追加の UI を必要とする場合は、省略記号ボタンを移動するための省略記号なし。  
  
     ![Visual Studio でのヘルプ リンク](../../extensibility/ux-guidelines/media/0601-e_helplink.png "0601 e_HelpLink")  
  
     **ヘルプ リンクにある省略記号 (...) は、追加の UI が必要なタスクを示します。**  
  
-   ユーザーの目的ではないためにへのリンクの開始は"詳細"を表示がありません必要があります。 ユーザーは、するには、特定の質問に答える、一般的な教育は表示されませんが。  
  
-   語句のヘルプにリンク、質問、トピックに応答するようにします。  
  
     正しくありません。  
     「Windows Azure モバイル サービスの料金に関する詳細については」  
  
     そうです：  
     "な価格オプションの Windows Azure モバイル サービスで利用できるか。"  
  
-   使用しないで *をクリックしています.*リンク テキスト。  
  
-   リンクの単語のみ"here"ことはありません。 これで、ハイパーリンク付きの単語のみを音声がスクリーン リーダーによって問題が発生します。  
  
     正しくありません。  
     "Windows Azure モバイル サービスで情報を見つける**ここ**"  
  
     そうです：  
     "な価格オプションの Windows Azure モバイル サービスで利用できるか。"  
  
-   ヘルプ リンクの正しい書き込みスタイルの詳細については、次を参照してください。、[ヘルプについては、Windows デスクトップ](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742494\(v=vs.85\).aspx)です。  
  
#### <a name="hint-text"></a>ヒント テキスト  
 ヒントのテキストは、コントロール内で、またはコントロールの下のレベルのウォーターマークとして表示されます。 正しい書式設定は、適切な VSColors トークンを使用して適用されます`Environment.GrayText`です。  
  
 これは、いくつかの形式で表示できます。  
  
-   コントロールのラベル: の代わりに  
  
     ![Visual Studio でのテキストをヒント](../../extensibility/ux-guidelines/media/0601-f_hinttext1.png "0601 f_HintText1")  
  
-   、動詞を使用して指示を提供します。  
  
     ![Visual Studio でのテキストをヒント](../../extensibility/ux-guidelines/media/0601-g_hinttext2.png "0601 g_HintText2")  
  
-   必要なエントリを示すテキスト。  
  
     ![Visual Studio でのテキストをヒント](../../extensibility/ux-guidelines/media/0601-h_hinttext3.png "0601 h_HintText3")  
  
#### <a name="watermark-text"></a>ウォーターマーク テキスト  
 空のデザイン画面で、テキストは実行できるだけでなく、該当する場合、関連する他のウィンドウを開くためのリンクを実現する新機能を示す必要があります。  
  
 ![Visual Studio でのテキストの透かし](../../extensibility/ux-guidelines/media/0601-i_watermarktext.png "0601 i_WatermarkText")  
  
 **Visual Studio でのウォーターマーク テキストの例**  
  
### <a name="common-terminology"></a>一般的な用語  
  
|用語|説明|コメント|  
|----------|-----------------|-------------|  
|サインイン/サインアウト|動詞が web プロパティに認証を表すため、web の同義語として使用します。 クライアント内でお一度だけ同様に、トップレベル概念の署名に使用内外 IDE ユーザー接続は、ローミングとライセンスなどの上位レベルの機能では使用その他のすべての接続を提供する最上位レベルの id を表します。|IDE ユーザーは、最上位の IDE ユーザーを表すので、サインインを表す必要があります/動詞、サインアウトするのみの機能です。|  
|接続/切断|オンライン サービスへの接続を 1 つを機能が維持される場所で使用します。|ここで、一度に 1 つのアクティブな Azure 接続をのみがあることができます、サーバー エクスプ ローラーでは、接続と切断の例を示します。|  
|追加/削除|非破棄します。 追加または一覧からのものを削除するときに使用します。|サーバー リストの TFS 接続マネージャー ダイアログでは、追加/削除の例を示します。|  
|削除|破壊的なです。 要素が削除されている場合にのみ使用を完全に破棄またはディスクから削除します。|結果がディスクからファイルを削除する場合、プロンプトが必要です"delete"一般にします。|  
  
## <a name="error-messages"></a>エラー メッセージ  
  
### <a name="overview"></a>概要  
 エラーが発生します。 ユーザーが実行できる操作の制限を設定すると、可能なエラー メッセージを防ぐうえで実用的な最初の手順です。 ただし、エラーが発生した場合、適切に記述されたエラー メッセージは、問題を軽減するために効果的に移動できます。 エラー メッセージは、おそらく最も重要な種類の同期は、解決する必要がある問題があるため、ユーザーに表示される通知のいずれかです。 不適切なエラー メッセージには、エラーの原因を判断する自分と考えられる解決策をユーザーがままにします。  
  
 ユーザーには、過剰に注意を払いまたはエラー メッセージをユーザーに値を追加する書き込みのみに必要なメッセージが発生するための混乱を招くを停止可能性があります。 メッセージが通知するだけである場合は、別の表示形式を使用します。  
  
### <a name="rules-for-creating-an-error-message"></a>エラー メッセージを作成するための規則  
  
-   エラー メッセージを構築するときに、対象ユーザーに適切なエラー レベルを選択します。 該当する場合は、ユーザーが行える操作を提供する簡単な集計のことがわかります。 状態をユーザーが知っている必要がない何もしません。  
  
-   建設的なサポートを提供します。 読み取り、処理命令を含むエラー メッセージに簡単です。  
  
-   二重否定を使用しないでください。  
  
-   両方、自動化されたを実行し、任意のエラー メッセージを記述する手動文法およびスペルを確認します。  
  
-   複雑なエラー メッセージ、シーケンシャル通信を回避します。 エラー メッセージに F1 フックアップを使用しないでください。 メッセージ自体を十分にする必要があります。  
  
-   適切なアイコンを使用します。  
  
-   質問を簡単に理解し、"Delete"と「キャンセル」などのクリアの選択肢のボタンの使用  
  
-   警告などの作業を進めるの結果がどのようになるかについて明確のようになります。 ボタンは、その結果を示す必要があります。  
  
-   エラーの場合は、ユーザーが問題を解決する実行できる内容を記述します。 ボタンは操作をするか、言う「閉じる」。 エラー メッセージには、[OK] ボタンを使用しないでください。  
  
-   いくつかの質問に、エラー メッセージを構築するときに、自分でファイルを確認してください。  
  
    -   ユーザーが単独でこのエラーの問題を解決する方法を見つけることができますか。  
  
    -   ユーザーは、このエラーと同じボキャブラリを使用しますか。  
  
    -   このエラーがあいまいです。 または、複数ある状況で共有しますか。 場合は、どの操作を行うガイド ユーザー必要があるソリューションにしますか。  
  
#### <a name="build-errors"></a>ビルド エラー  
 Visual Studio が、ソフトウェアの開発ツールであるため、多くのコンポーネントのコンパイル、変換、または開発者の作業をバイナリ形式に変換する手順をエンコードがあります。 これらの変換には、コンパイラは正しく作成されていないファイルを処理できない場合、またはコンパイラ オプションが正しく設定されなかったときにエラーが発生します。  
  
 Visual Studio ユーザーには、ビルド エラーを解決する開発時間の膨大な数を費やすことができます。 依存関係またはときにエラー メッセージが適切に作成することができますしづらくなるエラーの原因を明らかにエラーがあるときに、この解決時間が増加します。  
  
 最適なビルド エラーのオートコンプリート機能を提供しない Visual Studio は、最初の場所に出現するものは、IntelliSense を示す波線します。 スキーマの検証コントロールと同様のツールは、同じ種類のフィードバックを提供します。 これらのメカニズムは、事前にビルド エラーの可能性を緩和すること、適切な形式のコードを構築するためにユーザーを説明します。  
  
 Visual Studio には、ユーザーが読み取るし、ドキュメント ウィンドウで発生したエラーのナビゲート、ツール ウィンドウが用意されています。 ユーザーが迅速に大量のコードを移動して、問題の場所に直接移動できるように、キーボード ショートカットが提供されます。 Visual Studio では、ユーザーが、エラーの詳細については、ヘルプ トピックに直接移動できるように、特定のヘルプ キーワード/コンテキスト ID に関連付けるには、各ビルド エラーこともできます。  
  
 明確で正確なビルド エラーを記述します。  
  
-   **通常の言語を使用して**ほとんどまたはまったくないコンパイラの専門用語での問題を説明します。 ビルド エラーのテキストは、過度に技術的なことはできません。  
  
-   **考えられる原因を説明します。** たとえば、"プロパティと値の間にコロン、' (プロパティ): (値)' 宣言します"。  
  
-   考えられる修正内容の詳細についてを説明します。 十分な空き領域がない場合、対応するヘルプ トピックに追加の詳細を入れることがあります。  
  
### <a name="components-of-a-well-written-error-message"></a>適切に記述されたエラー メッセージのコンポーネント  
  
#### <a name="use-the-shell-dialog-service-for-error-messages"></a>エラー メッセージをシェル ダイアログ サービスを使用します。  
 シェル ダイアログ サービスを使用すると、メジャーを変更せずに個々 の要素、具体的には、フォント、メッセージの外観を制御できます。 使用して、 **IErrorInfo**メカニズムに報告を使用して**IVsUIShell::SetErrorInfo/ReportErrorInfo**です。  
  
#### <a name="choose-an-effective-and-appropriate-notification-presentation"></a>有効かつ適切な通知プレゼンテーションを選択します。  
 (同期通知) のデータの損失を防ぐためにすぐに対処が必要な場合は、重大な警告にモーダル ダイアログ ボックスを使用します。 読み取らずメッセージを閉じるときに負の値のような影響する可能性がある場合は、重要なアイコンが予約されています。 データの損失は、アラーム レベル応答を必要とする重大な状況です。 "重大"アイコンの過剰に使用するには、ユーザーがその重要性が desensitizes します。 エラー メッセージは、本質的に情報がある場合は、モーダル ダイアログ ボックス (非同期通知) に代わる方法を検討します。  
  
#### <a name="provide-a-clean-succinct-explanation-of-why-the-problem-occurred-rather-than-a-technical-explanation"></a>技術的な説明ではなく、問題が発生した理由のクリーン、簡潔な説明を提供します。  
 技術的な詳細についてでを持つユーザーに過負荷になりますエラー メッセージを無視する可能性が高くなります。 適切なメッセージの例:  
  
-   「要求されたファイルを開けません。」  
  
-   「インターネットに接続できません。」  
  
#### <a name="provide-information-about-how-to-fix-the-problem"></a>問題を解決する方法についてを説明します。  
 ユーザーの提案、問題を解決する方法を提供します。 正直なユーザーに提案がない場合です。 テクニカル サポートまたはコミュニティのサポートなど、代替のオンライン ソースへの直接のリンクを提供します。 問題に関連する特定のオンライン情報をユーザーに示すしようとしてください。 エラー ID は、ユーザーをその特定のエラーについてのディスカッション スレッドにリンクを検討してください。 適切なメッセージの例:  
  
-   「は、インターネットに接続してこの操作を再試行することを確認してください。」  
  
-   「ファイルが存在してを開くには、権限があることを確認してください。」  
  
#### <a name="write-a-message-that-is-short-and-to-the-point"></a>短期的およびポイントであるメッセージを記述します。  
 エラー メッセージが表示できる、説明、およびソリューションを提供がすぎる好きである場合に、まだ無視されます。 1 つのソリューションでは、[詳細] ボタンとプログレッシブ漏えいを使用します。 たとえば、短い説明/ソリューションを指定し、詳細ボタンの下の詳細を格納します。 ユーザーに、エラーの詳細を読み取る場合、実行ができます。  
  
 メッセージの言語になります。  
  
-   **ドメインに適したです。** ユーザーが理解する言語を使用します。 お客様は、開発者は、多くの場合、必要はありません、コンテキストとある用語。  
  
-   **特定します。** あいまいな言い回しを回避し、関連するオブジェクトの特定の名前と場所を提供します。 たとえば、エラー メッセージ「文字が無効です」などありません便利です。 検索を開始しますか。 「ファイルが見つかりません。」 どのファイルですか。  
  
-   **礼儀です。** ユーザーを非難したり、間抜けしたりしないでください。 悪意のある、または不快感を与える言語を回避する (強制終了、実行、終了、致命的な不正な)。 大文字のテキストが誇張表現として使用される多くの場合、およびとして読み取ることができないしないでください。 ユーモアを使用しないでください。  
  
-   **そうです。** (アルファ) であっても、正しいスペルおよび文法を使用します。 入力ミスは、不自然および恥ずかしい思いです。  
  
-   **適切なコンテキストです。** 適切なボタンのテキストを使用します。 [OK] ボタンを回避し、代わりに"Continue"または「はい/いいえ。」  
  
### <a name="error-message-examples"></a>エラー メッセージの例  
  
|良い|正しくありません。|  
|----------|---------|  
|"、ダイヤルする番号がサービスにありません。 ください番号を確認し、再度ダイヤルまたは 0 をオペレーターにダイヤルします。"|-"エラー (449): 無効な数"<br />-"このハンドルされない例外エラーを示します、操作が正常に完了しました"。<br /><br /> ![Visual Studio での不適切なエラー メッセージ](../../extensibility/ux-guidelines/media/0602-a_errordialog.png "0602 a_ErrorDialog")|  
  
## <a name="accessing-help"></a>ヘルプにアクセスします。  
  
### <a name="overview"></a>概要  
 MSDN のドキュメントについては、以外は、Visual Studio ユーザーは、UI の中にユーザーを支援するためにいくつかのアクセス ポイントを持っています。 これらのアクセス ポイントが常に使用可能であることを確認の機能チームは、環境によって提供されるヘルプ システムを利用する必要があります。 これらのアクセス ポイントは次のとおりです。  
  
-   **ダイアログの手順と補足のテキストです。** 方向または詳細については、ui 画面またはヒント アイコンの上のホバー時の使用可能ないずれかを示す静的テキストです。  
  
-   **F1 ヘルプ**(エディターのみ)。 Visual Studio エディター内でユーザーが信頼できること、いつでも F1 キーを押してが表示されます、ヘルプ トピックを現在の選択範囲を特定します。 F1 キーに関連付けられているトピックは該当して役に立つことを確認します。  
  
-   **ヘルプ トピックへのハイパーリンクをします。** ダイアログ、ツール ウィンドウ、またはの詳細については、テクノロジ、機能、またはタスクを実行する方法については、ユーザーを支援するトピックを起動するためのデザイン サーフェイス内のハイパーリンクです。  
  
-   **スマート タグおよびビルドのダイアログ ボックスなどのヘルパー UI メカニズムです。** これらのメカニズムは、UI 要素を理解するうえで、ユーザーを支援またはスマート タグまたはビルダーのダイアログ ボックスなどのタスクを容易にします。  
  
-   **UI のヘルプ ボタン**(非推奨)。 関連の F1 ヘルプ トピックへのアクセスを提供するタイトル バーに表示されるインジケーター。  
  
### <a name="text"></a>テキスト  
  
#### <a name="instructional-and-supplemental-text-in-dialogs"></a>ダイアログの手順と補足のテキスト  
 複雑なタスクをサポートするダイアログ ボックス、または複雑なコントロールの近くに、ダイアログ ボックスの上部にある多くの場合、UI 内での説明テキストを提供する必要があります。 参照してください[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)スタイルの作成方法の詳細。  
  
#### <a name="infotips"></a>ヒント  
 多くの場合、説明のテキストは、UI 内の場所に配置するのには長過ぎる場合がありますか、経験豊富なユーザーに乱雑さと同様に自分で、新しいユーザーにのみ役立ちます可能性があります。 この場合、ヒントの下のツールヒントとして、または情報の説明テキストを配置してください。  
  
 ヒントは、顕著なコントロールに関連する特定のヒントのアイコンは、使用されていない目障りを使用してそれらの近くに配置する必要があります。  
  
 ![Visual Studio でのヒント](../../extensibility/ux-guidelines/media/0601-d_infotip.png "0601 d_InfoTip")  
  
 **Visual Studio のヒントの例**  
  
### <a name="interactive-help-mechanisms"></a>対話型ヘルプ メカニズム  
  
#### <a name="f1-help"></a>F1 ヘルプ  
 F1 ヘルプが必要がない別の場所でエディターまたはデザイン サーフェイス内の Visual Studio 環境でします。  
  
#### <a name="hyperlinks-to-help-topics"></a>ヘルプ トピックへのハイパーリンク  
 ハイパーリンクは、操作を実行、IDE 内で移動する、またはブラウザーでヘルプを起動に使用できます。 参照してください[UI テキストと用語](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)の詳細については、言語および 07.10.01 ボタンとビジュアルとレイアウトのガイドラインについてはハイパーリンクです。  
  
#### <a name="help--buttons-in-dialog-title-bars-deprecated"></a>ヘルプ (非推奨) ダイアログのタイトル バーの [?] ボタン  
 ほとんどの場合、ダイアログ ボックスのタイトル バーの [?] ヘルプ ボタンの使用は推奨されていません。 UI のトピックでは、不要になった、ドキュメント モデルの一部と、したがってできない可能性があります、関連するトピックへのリンクをします。 基本的に、タイトル バー ボタン、F1 ヘルプと同様、ダイアログ ボックスにする必要はなくなりました。 場合によっては、このであってもできる使用できる、概念や手順の詳細があることを示すインジケーターとハイパーリンクが新しい UI で使用されることがより一般的です。  
  
##### <a name="dialogs-created-through-the-environment"></a>環境によって作成されたダイアログ ボックス  
 多くのシェル ダイアログを使って作成、 **VBDialogBoxParam**関数。 この共有関数が更新され、移行に役立つ、**ヘルプ** ダイアログ ボックスを**しますか?** 旧バージョンとアーキテクチャを維持しながらボタン互換性があり、拡張可能です。  
  
 具体的には、 **VBDialogBoxParam**関数は参照 ID を持つボタン用のダイアログ テンプレート**IDHELP** (9) またはラベルは**ヘルプ**または**&のヘルプ**. 非表示にされて、[ヘルプ] ボタンが見つかった場合、および**WS_EX_CONTEXTHELP**スタイルが、ダイアログでは、配置に追加、**しますか?** ダイアログのタイトル バーのボタンをクリックします。  
  
 ダイアログ プロシージャをスタックにプッシュし、処理前のダイアログ プロシージャという名前のダイアログを起動、ダイアログ ボックスが作成されると、 **DialogPreProc**です。 ときに、**しますか?** ボタンをクリックすると、送信、 **WM_SYSCOMMAND**の**SC_CONTEXTHELP**ダイアログ ボックスにします。 **DialogPreProc**このコマンドをキャプチャし、それを変更して、 **WM_HELP**は元のダイアログ プロシージャに渡されるメッセージ  
  
 ほとんどの環境が作成したダイアログでは、ダイアログで、[ヘルプ] ボタンがあります。 ダイアログ ボックスが表示されたら、[ヘルプ] ボタンは自動非に限って、**しますか?** ボタンが機能します。 場合、**しますか?** ボタンの削除または Windows で変更がこれまで、このソリューションでは、元のヘルプ ボタンにすばやく移動することができます。  
  
 このソリューションによってバグを引き起こす可能性のある 4 つの仮定を行います。  
  
-   ダイアログ ボックスの [ヘルプ] ボタンは**IDHELP** (9)。  
  
-   ダイアログ ボックスは、[ヘルプ] ボタンが非表示と正しい検索します。  
  
-   ダイアログ ボックスでは、winproc は置換しません。  
  
-   ダイアログ ボックスは、別のダイアログ ボックスの内部では埋め込まれません。  
  
 ダイアログ msenv 内に存在して、使用しない場合**VBDialogBoxParam**を活用することを調査**VBDialogBoxParam**独自のハンドラーを実装する前にします。  
  
##### <a name="dialogs-created-through-other-packages"></a>その他のパッケージによって作成されたダイアログ ボックス  
 ダイアログの msenv の外部に存在する場合、独自のソリューションを実装することができます。 VSPackage で、共有ダイアログ クラスは、タイトル バーに、ボタンを移動するか、各ダイアログ ボックスで、ハンドラーの実装を検討してください。 次のコードでは、作業を開始するため、実装のスケルトンを示します。  
  
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
 ウィンドウのタイトル バーのヘルプ ボタンの既定の動作をオーバーライドすることは、マネージ コードで簡単です。 この動作を示す完全なデモ アプリケーションを次に示します。 基本的には、フォームをオーバーライドする必要があります**WndProc**メソッドとし、起動の F1 ヘルプを要求時に、 **SC_CONTEXTHELP**メッセージを傍受します。  
  
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
  
## <a name="see-also"></a>参照  
 [Visual Studio のフォントと書式](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md)   
 [Visual Studio のレイアウト](../../extensibility/ux-guidelines/layout-for-visual-studio.md)   
 [Visual Studio の通知と進行状況](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)