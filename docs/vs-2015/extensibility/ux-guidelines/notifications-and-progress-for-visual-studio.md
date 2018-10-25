---
title: 通知と進行状況 for Visual Studio |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8494878dfc1760717e8e01b408822ea5dd1ea6cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49248002"
---
# <a name="notifications-and-progress-for-visual-studio"></a>通知と Visual Studio の進行状況
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

##  <a name="BKMK_NotificationSystems"></a> 通知システム  
  
### <a name="overview"></a>概要  
 ソフトウェア開発タスクに関する Visual Studio の動作をユーザーに通知するためにいくつかの方法はあります。  
  
 任意の種類の通知を実装する: 場合  
  
-   **最小値への通知の数を維持**有効な番号です。 通知メッセージは、大半の Visual Studio のユーザー、または特定の機能/機能領域のユーザーに適用する必要があります。 通知の過剰な使用は sidetrack ユーザーまたは認識される、システムの使いやすさが低下し可能性があります。  
  
-   **クリア、アクション可能メッセージを提供することを確認**ユーザーがより複雑な選択できるようにし、さらにアクションを実行する適切なコンテキストを呼び出しに使用できます。  
  
-   **同期および非同期メッセージを適切に表示します。** 同期の通知は、早急な措置が必要な web サービスがクラッシュしたときや、コードなど、例外がスローされたことを示します。 モーダル ダイアログ ボックスなど、その入力を必要とする方法ですぐにそのような状況のユーザーに通知する必要があります。 非同期の通知は、ユーザーが認識する必要がありますが不要になるにすぐに、動作など、web サイトのデプロイが完了したら、ビルド操作が完了すると、ものです。 これらのメッセージのよりアンビエントとユーザーの作業の流れを中断しない必要があります。  
  
-   **ユーザーがさらにアクションを実行するを防ぐために必要な場合にのみ、モーダル ダイアログ ボックスを使用して、** メッセージの受信確認またはダイアログ ボックスで表示を決定する前にします。  
  
-   **有効でなくなったときに、アンビエント通知を削除します。** 通知を破棄する場合は、通知が問題に対処するため、既に取得しているユーザーは必要ありません。  
  
-   **通知を誤った相関関係につながることに注意します。** ユーザーは、1 つ以上のアクションがトリガーされる通知実際と因果関係がないときと思われる可能性があります。 コンテキスト、トリガー、および通知のソースに関する通知メッセージのチェック ボックスをオフにします。  
  
### <a name="choosing-the-right-method"></a>適切な方法の選択  
 メッセージのユーザーに通知するのに適切な方法の選択を支援するために、このテーブルを使用します。  
  
|メソッド|使用|使用しないでください。|  
|------------|---------|----------------|  
|[モーダル エラー メッセージ ダイアログ ボックス](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|続行する前にユーザーの応答が必要なときに使用します。|ユーザーをブロックし、そのフローを中断する必要がない場合は使用しないでください。 もう 1 つでない方法でメッセージを表示する可能性がある場合は、モーダル ダイアログ ボックスを使用しないでください。|  
|[IDE のステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|プロセスの状態に関するアンビエント テキスト情報がある場合に使用します。|単独で使用しません。 最適な別のフィードバック メカニズムと組み合わせて使用。|  
|[埋め込まれた情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|ツール ウィンドウまたはドキュメント ウィンドウでは、進行状況、エラー状態、結果、または実用的な情報の通知を使用します。|情報は、情報バーが配置される場所に関係がない場合は使用しないでください。<br /><br /> ドキュメント/ツール ウィンドウの外側は使用しないでください。|  
|[マウス カーソルの変更](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|プロセスが起こっていることを通知するために使用可能性があります。 マウス カーソルが描画モードなど、特定のモードがドラッグ アンド ドロップがまたは進行状況のときなど、マウスの状態の変化があることを通知にも使用されます。|短い進行中の変更を使用しないか、カーソルのどきどき場合 (たとえば、プロセス全体の代わりに長い実行中のプロセスの部分に関連付けられている) 場合は、可能性があります。|  
|[進行状況インジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|(有限または無限)、進行状況を報告する必要がある場合に使用します。 これは、さまざまな進行状況インジケーターの種類とそれぞれの使用状況を特定します。 参照してください[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)します。||  
|[Visual Studio の通知ウィンドウ](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知ウィンドウが公開されている拡張可能ではありません。 ただし、さまざまなライセンスを Visual Studio またはパッケージに更新プログラムの情報を通知と重要な問題など、Visual Studio に関するメッセージを通信するために使用されます。|その他の種類の通知を使用しないでください。|  
|[エラー一覧](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|問題は、問題 (エラー/警告/情報) を持つユーザーの現在開いているソリューションに直接関係している場合は、アクション、コードを実行する必要があります。<br /><br /> これに含まれます、たとえば。<br /><br /> コンパイラのメッセージ (エラー/警告/情報)<br /><br /> コードのコード分析/診断メッセージ<br /><br /> -メッセージを構築します。<br /><br /> プロジェクトまたはソリューション ファイルに関連する問題に適したものは、最初、ソリューション エクスプ ローラーを示す値を検討してください。|ユーザーの開いているソリューションのコードへの関係がない項目を使用しないでください。|  
|エディターの通知: 電球|開いているファイルに存在する問題を解決するための修正プログラムがある場合に使用します。<br /><br /> 電球がオンデマンドで、リファクタリングなどのユーザーのコードに作成されますが、その場合は「通知のスタイル」は表示されませんが、クイック アクションをホストするためも使用する必要があります。|開いているファイルへの関係を持たない項目は使用しないでください。|  
|エディターの通知: 波線|問題が開かれているコード (たとえば、エラーの赤の波線) の特定のスパンとユーザーに警告を使用します。|開いているコードの特定の範囲に関連していない項目は使用しないでください。|  
|[埋め込まれたステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|使用すると、コンテンツまたは特定のツール ウィンドウ、ドキュメント ウィンドウまたはダイアログ ウィンドウのコンテキスト内のプロセスに関連する状態を提供します。|一般的な製品の通知、プロセス、または特定のウィンドウ内で、コンテンツへの関係を持たない項目を使用しないでください。|  
|[Windows トレイ通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|アウト プロセスのプロセスに対して通知を画面またはコンパニオン アプリケーションを使用します。|IDE に関連する通知を使用しないでください。|  
|[通知バブル](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|リモート プロセスの通知したり、変更を使用して**外**の IDE。|プロセスのユーザーに通知するための手段として使用しないでください**内**IDE。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a> モーダル エラー メッセージ ダイアログ ボックス  
 モーダル エラー メッセージ ダイアログ ボックスを使用して、ユーザーの確認/アクションが必要なエラー メッセージを表示できます。  
  
 ![モーダル エラー メッセージ](../../extensibility/ux-guidelines/media/0901-01-modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **データベースへの無効な接続文字列のユーザーに警告モーダル エラー メッセージ ダイアログ ボックス**  
  
####  <a name="BKMK_IDEStatusBar"></a> IDE のステータス バー  
 ステータス バーのテキストをユーザーが気付くことが発生する可能性、オールラウンドのコンピューターや Windows プラットフォームでの特定のエクスペリエンスを相互に関連付けます。 Visual Studio の顧客ベースはも知識を持つ Windows ユーザーは、ステータス バーに変更を見逃す可能性がある場合に、両方の領域で発生する傾向があります。 そのため、ステータス バーは最適な参考用または使用冗長キューの他の場所の情報が表示されます。 ダイアログ ボックスで、または、通知ツール ウィンドウで、あらゆる種類のユーザーをすぐに解決しなければならない重要な情報を提供する必要があります。  
  
 Visual Studio のステータス バーは、いくつかの種類の情報を表示できるように設計されています。 フィードバック、デザイナー、進行状況バー、アニメーション、およびクライアントの領域に分かれています。  
  
 フィードバック領域とデザイナーの領域は常に表示します。 進行状況バーとアニメーションのリージョンは、常に、動的、ユーザーのコンテキスト ベース。 デザイナー領域が、静的幅がテキスト メッセージの付属のリソースから取得される文字列の長さによって決まります。 これにより、コードの変更を必要とせず、幅のサイズを変更するローカライズできます。 英語では、この文字列の幅はほぼ値が 220 ピクセルです。 デザイナー領域が通常どおりに動作し、フィードバック領域が残りの領域を吸収します。  
  
 ステータス バーは IDE をデバッグ モードの場合など、さまざまな IDE の状態変更を通信することで視覚的な効果と機能の値を追加するも色分け表示します。  
  
 ![IDE ステータス バーの色の変更](../../extensibility/ux-guidelines/media/0901-02-idestatusbar.png "0901 02_IDEStatusBar")  
  
 **IDE ステータス バーの色**  
  
####  <a name="BKMK_EmbeddedInfobar"></a> 埋め込まれた情報バー  
 状態または条件をユーザーに知らせるドキュメント ウィンドウまたはツール ウィンドウの上部にある、情報バーを使用できます。 コマンドは、ユーザーがあるアクションを簡単に実行できるようになるようにも提供できます。 情報バーは、標準のシェル コントロールです。 IDE の他のユーザーと一貫性がないし、動作は、独自に作成しないでください。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)実装の詳細および使用ガイダンス。  
  
 ![情報バーが埋め込まれた](../../extensibility/ux-guidelines/media/0901-03-embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **情報バーは、IDE がデバッグ履歴モードと同じ方法では、標準のデバッグ モードでは、エディターは応答しませんをユーザーに警告、ドキュメント ウィンドウに埋め込まれます。**  
  
####  <a name="BKMK_MouseCursorChanges"></a> マウス カーソルの変更  
 マウス カーソルを変更する場合は、VSColor service に関連付けられているし、カーソルに関連付けられている色を使用します。 カーソル変更進行中の操作を示すために使用できますだけでなく、ユーザーがドラッグ、ドロップ、またはオブジェクトを選択するために使用できるターゲットを合わせるゾーンにヒットします。  
  
 操作の場合、それ以上の入力を表現するため、ユーザーは使用可能なすべての CPU 時間を確保する必要がある場合にのみ、待機時間/マウス カーソルを使用します。 マルチ スレッドを使用して適切に記述されたアプリケーションのほとんどの場合、ユーザーが他の操作を実行できなくと時間がまれな必要があります。  
  
 別の場所情報の冗長的な合図が表示されたカーソルの変更は便利なことに注意してください。 カーソルの変更は、ユーザーが対処必要のある重要な何かを伝達するためにしようとした場合は特に、ユーザーとの通信の唯一の方法としては依存しないでください。  
  
####  <a name="BKMK_NotSysProgressIndicators"></a> 進行状況インジケーター  
 進行状況の指標は、完了するまで複数の数秒かかる場合プロセス中にユーザーにフィードバックを提供するために重要です。 進行状況の指標を表示する、インプレース (近く起点の進行中の操作)、埋め込みステータス バーが、モーダル ダイアログで、または Visual Studio のステータス バーにします。 ガイダンスに従って[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)に関するこれらの使用と実装します。  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio の通知ウィンドウ  
 Visual Studio の通知ウィンドウには、ライセンス、環境 (Visual Studio)、拡張機能、および更新プログラムについて開発者に通知します。 ユーザーは、個々 の通知を無視してかまいませんまたは特定の種類の通知を無視することができます。 無視される通知の一覧が管理されている、**ツール > オプション**ページ。  
  
 通知ウィンドウが現在の拡張ではありません。  
  
 ![Visual Studio の通知ウィンドウ](../../extensibility/ux-guidelines/media/0901-06-vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Visual Studio の通知ツール ウィンドウ**  
  
####  <a name="BKMK_ErrorList"></a> エラー一覧  
 エラー一覧内での通知は、エラーおよび警告をコンパイル中に発生やビルド プロセス、し、その特定のコード エラーが発生するコード内を移動するユーザーを示します。  
  
 ![エラー一覧](../../extensibility/ux-guidelines/media/0901-08-errorlist.png "0901 08_ErrorList")  
  
 **Visual Studio でのエラー一覧**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a> 埋め込まれたステータス バー  
 IDE のステータス バーは、アクティブなドキュメント ウィンドウと、ユーザーのコンテキストやシステムの応答で更新情報を設定、クライアント領域のコンテキストで、動的であるためすることは困難で長期的な状態を返したり情報の継続的な表示を維持非同期のプロセス。 たとえば、IDE のステータス バーでは、複数の実行や選択項目をすぐに実施のテストの実行結果の通知を適していません。 ユーザーが選択を行うか、プロセスを開始するドキュメントまたはツール ウィンドウのコンテキストでこのようなステータス情報を保持する重要です。  
  
 ![埋め込まれたステータス バー](../../extensibility/ux-guidelines/media/0901-09-embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Visual Studio での埋め込みステータス バー**  
  
####  <a name="BKMK_WindowsTray"></a> Windows トレイ通知  
 システムの横にある通知領域は、Windows は、Windows タスク バーにクロックします。 多くのユーティリティとソフトウェア コンポーネントは、ユーザーが画面の解像度を変更したり、ソフトウェア更新プログラムを取得するなど、システム全体のタスクのコンテキスト メニューを取得できるように、この領域にアイコンを提供します。  
  
 環境レベルの通知は、Windows 通知領域ではなく、Visual Studio の通知ハブに表示する必要があります。  
  
####  <a name="BKMK_NotificationBubbles"></a> 通知バブル  
 通知バブルは、エディターまたはデザイナー内で情報として、または Windows 通知領域の一部として表示できます。 ユーザーは、これは重要でない通知特典です。 後で、解決できる問題としてこれらのバブルを認識します。 バブルでは、ユーザーがすぐに解決しなければならない重要な情報に適していません。 次の Visual Studio で通知バブルを使用する場合、[通知バブルの Windows デスクトップ ガイダンス](https://msdn.microsoft.com/library/windows/desktop/dn742472\(v=vs.85\).aspx)します。  
  
 ![通知バブル](../../extensibility/ux-guidelines/media/0901-07-notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Visual Studio の使用、Windows 通知領域に通知バブル**  
  
##  <a name="BKMK_ProgressIndicators"></a> 進行状況インジケーター  
  
### <a name="overview"></a>概要  
 進行状況のインジケーターは、ユーザーにフィードバックを提供するための通知システムの重要な部分です。 プロセスおよび操作は完了時に、ユーザーに通知します。 使い慣れたインジケーターの種類には、進行状況バー、スピン カーソル、およびアニメーション化されたアイコンが含まれます。 型と進行状況インジケーターの配置は、完了までに報告されている内容を含むコンテキストと、プロセスまたは操作をどのくらいの時間がかかるに依存します。  
  
#### <a name="factors"></a>要因  
 どのインジケーターの種類が適切で判断するには、次の要因を判断する必要があります。  
  
1.  **タイミング:** 処理にかかる時間の長さ  
  
2.  **モダリティ:** 操作が (ロック、プロセスが完了するまで UI) の環境にモーダルかどうか  
  
3.  **永続的な/Transient:** 進行状況の最終結果を後で報告されるや表示可能なをある必要があるかどうか  
  
4.  **不確定/不定:** かどうか、操作の終了時刻と進行状況を計算できます  
  
5.  **グラフィック/Textual 場所:** かどうか、進行状況やプロセスは、メッセージ、またはツリー コントロールなどの特定のコントロールの本体で、キャプチャされたインライン  
  
6.  **近接:** 進行状況をそれに関連する UI に近接するかどうか。 (可能性のある離れた、ステータス バーにあることができますやプロセスを起動するボタンの近くに配置するがあるなどのでしょうか。)  
  
#### <a name="determinate-progress"></a>確定した進行状況  
  
|進行状況の種類|使用するタイミングと方法|メモ|  
|-------------------|-------------------------|-----------|  
|進行状況バー (不確定)|予想される所要時間の > 5 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**アニメーションにテキストを埋め込みます。|  
|情報バー|関連付けられたコンテキストの UI メッセージです。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**を複数のプロセスを示すために必要なときに複数の情報バーを使用します。 積み上げ進行状況バーを代わりに使用します。|  
|[出力] ウィンドウ|一時的な通知: アプリ レベルのプロセスにそのユーザーがする**確認**完了した後の詳細。|**しない**ユーザーが後でデータを参照する必要がある場合に使用します。|  
|ログ ファイル|場合、intransient 通知と組み合わせて使用することが重要と**保存**完了した後の詳細。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスのユーザーは**必要はありません**完了した後の詳細。<br /><br /> 埋め込みの進行状況バーが含まれています。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
  
#### <a name="indeterminate-progress"></a>不確定な進行状況  
  
|進行状況の種類|使用するタイミングと方法|メモ|  
|-------------------|-------------------------|-----------|  
|進行状況バー (不確定)|予想される所要時間の > 5 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**アニメーションにテキストを埋め込みます。|  
|Ants (アニメーション化された水平方向のドット数)|サーバーへのラウンド トリップします。<br /><br /> 親コンテナーの上部にコンテキストの near ポイントが配置されます。|**しない**コンテナー全体を親として持たない場合に使用します。|  
|スピン ボックス (進行状況リング)|コンテキストの UI またはスペースがの考慮事項に関連付けられたプロセス。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
|情報バー|関連付けられたコンテキストの UI メッセージです。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。|**しない**を複数のプロセスを示すために必要なときに複数の情報バーを使用します。 積み上げ進行状況バーを代わりに使用します。|  
|[出力] ウィンドウ|一時的な通知: ユーザーが必要なアプリ レベルのプロセス**確認**完了した後の詳細。|**しない**セッション間で保持する必要がある情報を使用します。|  
|ログ ファイル|場合、intransient 通知と組み合わせて使用することが重要と**保存**完了した後の詳細。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスのユーザーは**必要はありません**完了した後の詳細。<br /><br /> 埋め込みの進行状況バーが含まれています。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
  
### <a name="progress-indicator-types"></a>進行状況インジケーターの種類  
  
#### <a name="progress-bars"></a>進行状況バー  
  
##### <a name="indeterminate"></a>不確定です  
 ![不確定な進行状況バー](../../extensibility/ux-guidelines/media/0901-04-indeterminate.png "0901 04_Indeterminate")  
  
 **不確定な進行状況バー**  
  
 操作の全体的な進行状況を「不確定」を意味またはプロセスを決定することはできません。 操作を必要とする無制限の時間の長さまたは不明な数のオブジェクトにアクセスするには、不確定な進行状況バーを使用します。 説明テキストを使用して、何が起こっているかに付随します。 時間ベースの操作に境界を提供するには、タイムアウトを使用します。 不確定な進行状況バーは、アニメーションを使用して、進行状況が行われているが、その他の情報を指定しないを示します。 単独で精度の考えられる不足にのみ基づいて、不確定な進行状況バーを選択しないでください。  
  
##### <a name="determinate"></a>不確定です。  
 ![確定した進行状況バー](../../extensibility/ux-guidelines/media/0901-05-determinate.png "0901 05_Determinate")  
  
 **確定した進行状況バー**  
  
 「不確定」境界付けられた長時間操作やプロセスが必要である場合でも意味量が時間を正確に予測することはできません。 完了を明確に示すためです。 進行状況バーが 100% には、操作が完了していなければことはありません。 確定した進行状況バーのアニメーションでは、左から右を 0 から 100% に移動します。  
  
 操作中に旧バージョンとの進行状況インジケーターを移動しません。 バーは、前方に移動着実に、操作の開始時におよび終了時に 100% に到達する必要があります。 進行状況バーのポイントは、数の手順に関係なく、操作全体の所要が時間の概要を把握するためにです。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>同時実行のレポート (積み上げ進行状況バー)  
 操作に長い時間がかかる場合、おそらくいくつかの分、2 つの進行状況バーを使用できますいずれかを示す操作の全体的な進行状況と現在のステップの進行状況。 たとえば、セットアップ プログラムでは、多数のファイルをコピーは場合を示すプロセス全体の所要時間を 2 つ目は、現在のファイルの割合を指定できますまたはディレクトリがコピーされるときに 1 つの進行状況バーを使用できます。 5 個の同時実行操作または積み上げ進行状況バーを使用してプロセスを報告しません。 5 個の同時操作やレポートにプロセスがあればを使用して、モーダル ダイアログ ボックスが [キャンセル] ボタンとレポートの出力ウィンドウに進行状況の詳細。  
  
##### <a name="textual-descriptions"></a>テキストの説明  
 何が起こっているかに付属する説明のテキストと、推定完了時刻を使用します。 操作にかかるかを判断することはできない場合、は、進行状況バーではなく、アニメーションのアイコン、フィードバックの提供に適してにあります。  
  
 Visual Studio には、Visual Studio 統合製品で使用できるステータス バーに標準の進行状況バーが用意されています。 進行状況バーがアニメーション化中に何が起こっているかのテキスト説明については、ステータス バーのテキストを更新することができます。  
  
#### <a name="other-progress-indicators"></a>その他の進行状況インジケーター  
  
##### <a name="ants-animated-horizontal-dots"></a>Ants (アニメーション化された水平方向のドット数)  
 ![進行状況の ants](../../extensibility/ux-guidelines/media/0903-01-ants.png "0903 01_Ants")  
  
 "Ants、"水平方向のアニメーションのドットは、不確定なラウンドト リップ サーバー プロセスのビジュアルの参照を提供します。  
  
##### <a name="spinner-progress-ring"></a>スピン ボックス (進行状況リング)  
 ![進行状況スピナー](../../extensibility/ux-guidelines/media/0903-02-spinner.png "0903 02_Spinner")  
  
 スピン ボックス (別名「進行状況リング」) は、主にコンテキストの UI 関連して使用される、不確定な進行状況インジケーターです。 テキスト カテゴリ ヘッダー、メッセージング、またはコントロールなどの関連するコンテンツに近接するスピン ボタンを表示します。  
  
##### <a name="cursor-feedback"></a>カーソルからのフィードバック  
 2 ~ 7 秒かかる操作では、カーソルからのフィードバックを提供します。 通常、オペレーティング システムによって提供される待機カーソルを使用してこれを意味します。 ガイダンスについては、MSDN の記事を参照してください。 [Cursors.Wait プロパティ](https://msdn.microsoft.com/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)します。  
  
#### <a name="progress-indicator-locations"></a>進行状況インジケーターの場所  
  
##### <a name="status-bar"></a>ステータス バー  
 ステータス バーには、ユーザーの作業を中断することがなく、ユーザーにメッセージと有用な情報を表示する場所に、アプリケーションが与えられます。 通常、ウィンドウの下部に表示されます、進行状況の状態は、進行状況バー インジケーターと組み合わせての進行状況の測定に関するメッセージを含むツール ヒント ウィンドウになります。  
  
 ![進行状況バーとステータス バー](../../extensibility/ux-guidelines/media/0903-03-statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **進行状況バーとステータス バー**  
  
 ![メッセージング付きのステータス バー](../../extensibility/ux-guidelines/media/0903-04-statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **説明テキストをステータス バー**  
  
##### <a name="infobar"></a>情報バー  
 同様に、情報バー、ステータス バーを提供コンテキストの通知、メッセージング、不確定な進行状況インジケーターなど、進行状況バーまたはスピン ボタンと組み合わせて使用することができますも。 詳細なレベルの進行状況または不確定な進行状況の表示、情報バーは提供されませんする必要があります。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。  
  
 ![進行状況バーとメッセージング付きの情報バー](../../extensibility/ux-guidelines/media/0903-05-infobar.png "0903 05_InfoBar")  
  
 **進行状況バーと説明テキストを含むページ**  
  
 ![ウィンドウ内の情報バー](../../extensibility/ux-guidelines/media/0903-06-infobarinwindow.png "0903 06_InfoBarInWindow")  
  
 **コード分析 ウィンドウ内の情報バー**  
  
##### <a name="inline"></a>インライン  
 進行状況ローダーの種類のいずれかでは、インラインの進行状況を示す値を表現できます。 進行状況インジケーターがメッセージングでペアになっている通常が、これは必須ではありません。  
  
 ![インラインの進行状況スピナー](../../extensibility/ux-guidelines/media/0903-07-inlinespinner.png "0903 07_InlineSpinner")  
  
 **スピン ボタンの説明テキストと組み合わせる**  
  
 ![インラインの積み上げ進行状況バー](../../extensibility/ux-guidelines/media/0903-08-inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **不確定の積み上げ進行状況バー**  
  
 ![インラインの進行状況メッセージング](../../extensibility/ux-guidelines/media/0903-09-inlinetext.png "0903 09_InlineText")  
  
 **サーバー エクスプ ローラーのインライン テキスト: 更新しています.**  
  
##### <a name="tool-windows"></a>ツール ウィンドウ  
 グローバルの進行状況の表示は、ツールバーのすぐ下に配置されている、不確定な進行状況バーで表されます。  
  
 ![グローバルの不確定な進行状況バー](../../extensibility/ux-guidelines/media/0903-23-globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **チーム エクスプ ローラーのグローバル不確定な進行状況バー**  
  
##### <a name="dialogs"></a>ダイアログ ボックス  
 ダイアログ ボックスには、進行状況ローダーの種類のいずれかを含めることができます。 進行状況の指標でくメッセージングとペアになっているだけでなく複数レベルの細分化された表現とサブ プロセスに進行状況の表示と組み合わせます。  
  
 ![複数の進行状況インジケーターの種類を持つダイアログ](../../extensibility/ux-guidelines/media/0903-11-dialog.png "0903 11_Dialog")  
  
 **同時実行プロセスと複数の進行状況インジケーターの種類の visual Studio ダイアログ**  
  
 ![進行状況ローダーとメッセージング ダイアログ](../../extensibility/ux-guidelines/media/0903-12-dialog2.png "0903 12_Dialog2")  
  
 **進行状況ローダーとメッセージング コマンド実行のインラインでの visual Studio ダイアログ**  
  
##### <a name="document-well"></a>ドキュメント ウェル  
 ドキュメントは、コントロールと組み合わせて複数の進行状況ローダーの種類を表示できます。  
  
 ![進行状況もドキュメントのメッセージング](../../extensibility/ux-guidelines/media/0903-13-documentwell.png "0903 13_DocumentWell")  
  
 **ツールバーの下の不確定な進行状況バー**  
  
##### <a name="output-window"></a>[出力] ウィンドウ  
 出力ウィンドウは、プロセスの進行とインライン テキスト メッセージングを使用して継続的な進行状況を処理するために適しています。 出力ウィンドウの進行状況に関するレポートとステータス バーを使用する必要があります。  
  
 ![進行状況が出力ウィンドウにメッセージング](../../extensibility/ux-guidelines/media/0903-14-outputwindow.png "0903 14_OutputWindow")  
  
 **継続的なプロセスの状態と出力ウィンドウとメッセージを待機**  
  
##  <a name="BKMK_Infobars"></a> 情報の表示  
  
### <a name="overview"></a>概要  
 情報バーが注意の近くにインジケーターをユーザーに付与し、視覚的な外観と操作の一貫性を確保する共有の情報バー コントロールを使用します。  
  
 ![Infobar](../../extensibility/ux-guidelines/media/0904-01-infobar.png "0904-01_Infobar")  
  
 **Visual Studio で情報の表示**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>情報バーの適切な使用  
  
-   現在のコンテキストに関連する非ブロッキングしますですが、重要なメッセージをユーザーに提供するには  
  
-   デバッグ履歴など、いくつかの相互作用の影響を実行する UI が状態または条件であることを示します  
  
-   システムの拡張機能でパフォーマンスの問題が原因となって場合などの問題が検出されたことをユーザーに通知するには  
  
-   エディターのタブやスペースにファイルが混在ことが検出した場合など、アクションを簡単に実行する方法をユーザーに提供するには  
  
##### <a name="do"></a>操作を行います。  
  
-   つまり、およびポイントには、情報バーのメッセージ テキストを保持します。  
  
-   簡潔なリンクやボタンのテキストを保持します。  
  
-   最小限の場合、必要な操作のみを表示するユーザーに提供する、"action"オプションを確認します。  
  
##### <a name="dont"></a>できません：  
  
-   ツールバーに配置する必要がある標準のコマンドを提供する、情報バーを使用します。  
  
-   モーダル ダイアログ ボックスの代わりに、情報バーを使用します。  
  
-   期間外の浮動小数点のメッセージを作成します。  
  
-   同じウィンドウ内で複数の場所で複数の情報バーを使用します。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>同時に複数の情報バーを表示できますか。  
 はい、同時に複数の情報バーを表示できます。 これらは、上およびその他の情報バーが表示された下に表示されている最初の情報バーで、先着順に表示されます。  
  
 一度に最大 3 つの情報バーが表示されます、情報バーの詳細については、使用可能な場合、情報バーの領域になるスクロール可能な後。  
  
### <a name="creating-an-infobar"></a>情報バーを作成します。  
 情報バーには、左から右へ、4 つのセクションがあります。  
  
-   **アイコン:** これは、任意のアイコンを追加することの警告アイコンなど、情報バーを表示したいです。  
  
-   **テキスト:** シナリオ/状況ユーザーを説明するテキストでは、テキスト内のリンクと共には追加できますが必要な場合。 簡潔なテキストを保持してください。  
  
-   **アクション:** リンクやボタンは、情報バーで、ユーザーが実行できるアクションのこのセクションを含める必要があります。  
  
-   **[閉じる] ボタン:** 右側には、最後のセクションは閉じるボタンを持つことができます。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>マネージ コードで標準的な情報バーを作成します。  
 InfoBarModel クラスは、情報バーのデータ ソースの作成に使用できます。 これら 4 つのコンス トラクターのいずれかを使用します。  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
  
```  
  
```  
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);  
```  
  
 ハイパーリンク、動作設定ボタン、アイコンとテキスト、InfoBarModel を作成する例を次に示します。  
  
 ![ハイパーリンクを含むページ](../../extensibility/ux-guidelines/media/0904-02-infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
```  
var infoBar = new InfoBarModel(  
    textSpans: new[]  
    {  
        new InfoBarTextSpan("This is a "),  
        new InfoBarHyperlink("hyperlink"),  
        new InfoBarTextSpan(" InfoBar.")  
    },  
    actionItems: new[]  
    {  
        new InfoBarButton("Click Me")  
    },  
    image: KnownMonikers.StatusInformation,  
    isCloseButtonVisible: true);  
  
```  
  
#### <a name="creating-a-standard-infobar-in-native-code"></a>ネイティブ コードで標準的な情報バーを作成します。  
 ネイティブ コードから、情報バーを提供するために、IVsInfoBar のインターフェイスを実装します。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>情報バーから、情報バーを UIElement の取得  
 InfoBarModel または IVsInfoBar 実装は、データ モデルを UI に表示するには、UIElement に変換する必要があります。 SVsInfoBarUIFactory/IVsInfoBarUIFactory サービスでは、UIElement を取得できます。  
  
```  
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)  
{  
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;  
    if (infoBarUIFactory == null)  
    {  
        uiElement = null;  
        return false;  
    }  
  
    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);  
    return uiElement != null;  
}  
```  
  
### <a name="placement"></a>配置  
 情報バーは、次の場所の 1 つ以上表示されます。  
  
-   ツール ウィンドウ  
  
-   ドキュメント タブ内で  
  
> [!IMPORTANT]
>  グローバルなコンテキストに関するメッセージを提供する、情報バーを配置することになります。 これは、ツールバーと、ドキュメント ウェルの間が表示されます。 これは推奨されません「ジャンプし、ください」の問題が発生するため、IDE の場合を除き、避ける必要があります、どうしても必要かつ適切な。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane で、情報バーを配置します。  
 ツール ウィンドウに、情報バーを追加する ToolWindowPane.AddInfoBar(IVsInfoBar) メソッドを使用できます。 この API は、(どの InfoBarModel が既定の実装) IVsInfoBar を追加できますか、または、IVsUIElement します。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>ドキュメントまたは ToolWindowPane 以外に、情報バーを配置します。  
 任意の IVsWindowFrame に、情報バーを配置するには、VSFPROPID_InfoBarHost プロパティを使用して、フレームを IVsInfoBarHost を取得し、情報バーの UIElement します。  
  
```  
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)  
{  
    IVsInfoBarHost infoBarHost;  
    if (TryGetInfoBarHost(frame, out infoBarHost))  
    {  
        infoBarHost.AddInfoBar(uiElement);  
    }  
}  
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)  
{  
    object infoBarHostObj;  
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))  
    {  
        infoBarHost = null;  
        return false;  
    }  
  
    infoBarHost = infoBarHostObj as IVsInfoBarHost;  
    return infoBarHost != null;  
}  
  
```  
  
#### <a name="placing-an-infobar-in-the-main-window"></a>メイン ウィンドウで、情報バーを配置します。  
 メイン ウィンドウで、情報バーを配置するには、ivsshell でサービスの VSSPROPID_MainWindowInfoBarHost を使用して、メイン ウィンドウの IVsInfoBarHost を取得して、UIElement 情報バーを追加します。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>わかります、情報バーで、ユーザーが操作するときか。  
 はい、すべてのイベント アクション情報バーの作成者に返されます。 バーに表示されるユーザー選択に基づいて、IDE でアクションを実行する、情報バーの作成者の役目です。 情報バーは、ある閉じるボタンがクリックされたホストから自動的に削除されますが、後に削除するその他の情報の表示の必要性を閉じる場合は、追加の作業が必要です。 製品利用統計情報は、各情報バーを個別に記録される必要があります。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane 情報バーのイベントの受信  
 ToolWindowPane が情報バーの 2 つのイベントです。 InfoBarClosed イベントは、ToolWindowPane で、情報バーを閉じるときに発生します。 InfoBarActionItemClicked イベントは、ハイパーリンクや、情報バー内のボタンがクリックされたときに発生します。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement から直接情報バーのイベントの受信  
 情報バーの UIElement から直接イベントをサブスクライブする IVsInfoBarUIElement.Advise を使用できます。 IVsInfoBarUIEvents を実装すると、閉じる受信し、クリックしてイベントの作成者ことができます。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a> エラーの検証  
 必須のフィールドをスキップする場合など、または形式が正しくないデータが入力されると、許容されない情報を入力すると、ときに、コントロールの検証を使用またはブロックしているポップアップ エラー ダイアログを使用する代わりに、コントロールの近くにフィードバックすることをお勧めします。  
  
### <a name="field-validation"></a>フィールドの検証  
 フォームおよびフィールドの検証は、3 つのコンポーネントで構成されています。 コントロールを、アイコン、およびツールヒント。 いくつかの種類のコントロールには、これを使用できます、テキスト ボックスは、例として使用します。  
  
 ![フィールドの検証&#40;空白&#41;](../../extensibility/ux-guidelines/media/0905-01-fieldvalidation.png "0905 01_FieldValidation")  
  
 フィールドが必要な場合があります透かしテキストを示す**\<必要 >** フィールドの背景が光を指定する必要があります黄色 (VSColor: `Environment.ControlEditRequiredBackground`) と、フォア グラウンドが灰色になります (VSColor: `Environment.ControlEditRequiredHintText`)。  
  
 ![フィールドのラベルが"Required"検証](../../extensibility/ux-guidelines/media/0905-02-fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 コントロールの状態が判断できる*に入力された無効なコンテンツ*別のコントロールにフォーカスを移動するときか、または、ユーザーが [OK] のコミット ボタンをクリックしたときまたはユーザーがドキュメントまたはフォームを保存するときにします。  
  
 無効なコンテンツの状態が確認された場合、コントロールの内部または同様の横にアイコンが表示されます。 アイコンまたはコントロールのいずれかのポインターを合わせると、エラーを説明するツールヒントが表示されます。 さらに、1 ピクセルの枠線が無効な状態を作成しているコントロールの周囲に表示されます。  
  
 ![検証のレイアウトの仕様をフィールド](../../extensibility/ux-guidelines/media/0905-03-layoutspecs.png "0905 03_LayoutSpecs")  
  
 **フィールドの検証のレイアウトの仕様**  
  
#### <a name="acceptable-variations-for-icon-location"></a>アイコンの場所のバリエーションを許容  
 ユーザーが、検証エラーを通知する必要が無数の一意な場合があります。 コントロールの種類と、UI の構成では、考慮すると、自分の状況に適切なアイコンの配置を選択します。  
  
 ![アイコンの場所の許容可能な場所](../../extensibility/ux-guidelines/media/0905-04-iconlocation.png "0905 04_IconLocation")  
  
 **許容されるバリエーションのフィールド検証のアイコンの場所**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>サーバーまたはネットワーク接続へのラウンド トリップを必要とする検証  
 場合によっては、コンテンツを検証する、サーバーへのラウンド トリップが必要ですし、検証、ユーザーの進行状況とエラーの状態を表示することがあります。 次の図は、このケースと推奨される UI の例を示しています。  
  
 ![サーバーへのラウンド トリップに関連する検証](../../extensibility/ux-guidelines/media/0905-05-roundtrip.png "0905 05_RoundTrip")  
  
 **サーバーへのラウンド トリップに関連する検証**  
  
 「確認しています...」に対応するために、コントロールの右側に十分な使用可能な領域を指定する必要がありますに注意してください。 テキストを「再試行」してください。  
  
#### <a name="in-place-warning-text"></a>インプレース警告テキスト  
 エラーの状態で、コントロールの近くに、エラー メッセージに使用できる空きスペースがある場合に、単独のツールヒントを使用してこれをお勧めします。  
  
 ![&#45;配置警告](../../extensibility/ux-guidelines/media/0905-06-inplacewarning.png "0905 06_InPlaceWarning")  
  
 **インプレース警告テキスト**  
  
#### <a name="watermarks"></a>透かし  
 場合があります、コントロール全体またはウィンドウがエラー状態には。 このような状況では、エラーを示すウォーターマークを使用します。  
  
 ![透かし](../../extensibility/ux-guidelines/media/0905-07-watermark.png "0905 07_Watermark")  
  
 **ウォーターマーク フィールドの検証**

