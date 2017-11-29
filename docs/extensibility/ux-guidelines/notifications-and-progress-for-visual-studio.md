---
title: "通知および Visual Studio の進行状況を |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0d16ed0f58929a6559812261c3443b3561375205
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="notifications-and-progress-for-visual-studio"></a>通知および Visual Studio の進行状況
##  <a name="BKMK_NotificationSystems"></a>通知システム  
  
### <a name="overview"></a>概要  
 何が起こっているか Visual Studio でのソフトウェアの開発タスクに関するをユーザーに通知するためにいくつかの方法はあります。  
  
 任意の種類の通知を実装する: 場合  
  
-   **最小値への通知の数を保持する**効果的な番号です。 通知メッセージは、大半の Visual Studio ユーザー、または特定の機能/機能領域のユーザーに適用する必要があります。 通知の過剰な使用は、sidetrack ユーザーまたは見かけ上、システムの使いやすさが低下する可能性があります。  
  
-   **クリア、実践的なメッセージを提供することを確認**より複雑な選択を行うと、さらに行い、適切なコンテキストを呼び出すため、ユーザーが使用できることです。  
  
-   **同期および非同期のメッセージを適切に存在します。** 同期の通知は、早急に措置が必要なもの、web サービスがクラッシュする場合や、コードなど、例外がスローされることを示しています。 そのような状況など、モーダル ダイアログ ボックスで、入力を必要とする方法ですぐのユーザーに通知する必要があります。 非同期の通知とは引数があるが、ユーザーについてが知っておく必要ありませんが作用する、すぐに web サイトの展開が終了する場合は、ビルド操作の完了またはなど。 それらのメッセージよりアンビエントされ、ユーザーのタスクのフローを中断しません必要があります。  
  
-   **モーダル ダイアログ ボックスをユーザーがさらに操作を実行するを防ぐために必要な場合にのみを使用して**メッセージの受信確認またはダイアログ ボックスで表示を決定する前にします。  
  
-   **有効でなくなったときに、アンビエント通知を削除します。** 通知を破棄する場合は、通知が問題に対処する操作はすでに実行するユーザーは必要ありません。  
  
-   **通知が誤った相関関係につながる可能性があります。** ユーザーは、そのアクションの 1 つ以上が生成されたことを通知実際と因果関係がないときと思われる可能性があります。 コンテキスト、トリガー、および通知のソースに関する通知メッセージのチェック ボックスをオフにします。  
  
### <a name="choosing-the-right-method"></a>適切なメソッドを選択します。  
 この表を使用すると、メッセージのユーザーに通知する正しい方法を選択する際に役立ちます。  
  
|メソッド|用途|使用しないでください。|  
|------------|---------|----------------|  
|[モーダル エラー メッセージ ダイアログ ボックス](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|続行する前にユーザーからの応答が必要な場合に使用します。|ユーザーをブロックし、そのフローが中断する必要がない場合に使用しないでください。 関与レベルが低く、別の方法でメッセージを表示することである場合は、モーダル ダイアログ ボックスを使用しないでください。|  
|[IDE ステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|プロセスの状態に関するアンビエント テキスト情報がある場合に使用します。|単独で使用しません。 最適な別のフィードバック メカニズムと組み合わせて使用します。|  
|[埋め込まれた情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|ツール ウィンドウまたはドキュメント ウィンドウでは、進行状況、エラー状態、結果、および実践的な情報の通知を使用します。|情報は、情報バーが配置される場所に関係がない場合は使用しないでください。<br /><br /> ドキュメント/ツール ウィンドウの外側は使用しないでください。|  
|[マウス カーソルが変化](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|プロセスが起こっていることを通知するために使用可能性があります。 マウス カーソルが描画モードなど、特定のモードがドラッグ アンド ドロップが進行中またはするときなど、マウスの状態の変更があることを通知するも使用されます。|短い進行中の変更を使用しないか、カーソルのどきどき場合 (たとえば、プロセス全体の代わりに長い実行中のプロセスの部分に関連付けられている) ときに可能性があります。|  
|[進行状況インジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|(不確定または不確定)、進行状況をレポートする必要がある場合に使用します。 さまざまな進行状況インジケーターの種類とそれぞれの具体的な使用方法があります。 参照してください[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)です。||  
|[Visual Studio の通知ウィンドウ](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知ウィンドウでは、パブリックに拡張できません。 ただし、ライセンスと Visual Studio をまたはパッケージに更新プログラムの情報を通知きわめて重要な問題など、Visual Studio に関するメッセージの範囲を通信するために使用されます。|その他の種類の通知を使用しないでください。|  
|[エラー一覧](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|問題 (エラー/警告/情報) を持つユーザーの現在開いているソリューションに直接関連する問題、ときに、コードでアクションを実行する必要があります。<br /><br /> これは、たとえば含みます。<br /><br /> コンパイラのメッセージ (エラー/警告/情報)<br /><br /> コードのコード アナライザー/診断メッセージ<br /><br /> -メッセージを構築します。<br /><br /> プロジェクトまたはソリューションのファイルに関連する問題に適したものが最初に、ソリューション エクスプ ローラーを示す値を検討してください。|ユーザーの開いているソリューションのコードへの関係を持たない項目は使用しないでください。|  
|エディターの通知: 電球|修正プログラムを開いているファイルに存在する問題を解決する必要がある場合に使用します。<br /><br /> 電球はリファクタリングなどの要求時にユーザーのコードで取得されて、その場合は「通知のスタイル。」が表示されないクイック操作をホストするためも使用する必要がありますに注意してください。|開いているファイルへの関係を持たない項目は使用しないでください。|  
|エディターの通知: 波線|開いているコード (たとえば、エラーの赤の波線) の特定の期間に関する問題をユーザーに警告を使用します。|開いているコードの特定の期間に関係しない項目は使用しないでください。|  
|[埋め込まれたステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|使用すると、コンテンツまたは特定のツール ウィンドウ、ドキュメント ウィンドウまたはダイアログ ウィンドウのコンテキスト内のプロセスに関連するステータスを提供します。|一般的な製品の通知、プロセス、または特定のウィンドウ内で、コンテンツへの関係を持たない項目は使用しないでください。|  
|[Windows トレイ通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|アウト オブ プロセス用の通知を表面化またはコンパニオン アプリケーションを使用します。|IDE に関連する通知を使用しないでください。|  
|[通知バブル](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|使用して、リモート プロセスの通知または変更**外**IDE のです。|プロセスのユーザーに通知するための手段として使用しないでください**内**IDE です。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="BKMK_ModalErrorMessageDialogs"></a>モーダル エラー メッセージ ダイアログ ボックス  
 モーダル エラー メッセージ ダイアログ ボックスを使用して、ユーザーの確認/アクションが必要なエラー メッセージを表示します。  
  
 ![モーダル エラー メッセージ](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901 01_ModalErrorMessage")  
  
 **データベースへの無効な接続文字列のユーザーに警告モーダル エラー メッセージ ダイアログ ボックス**  
  
####  <a name="BKMK_IDEStatusBar"></a>IDE ステータス バー  
 ユーザーがステータス バーのテキストを確認する可能性、オールラウンドのコンピューターのエクスペリエンスと Windows プラットフォームの特定の経験を相互に関連付けます。 Visual Studio のお客様は、でも知識豊富な Windows ユーザーは、ステータス バーに変更を見落とす可能性がありますが、両方の領域で発生する傾向があります。 そのため、ステータス バーは最適な情報提供を目的のまたは使用冗長なキューの他の場所の情報が表示されます。 ダイアログ ボックスで、または通知ツール ウィンドウで、あらゆる種類のユーザーがすぐに解決する必要がある重要な情報を指定する必要があります。  
  
 Visual Studio のステータス バーは、いくつかの種類の情報を表示する許可するように設計されています。 フィードバック、デザイナー、進行状況バー、アニメーション、およびクライアントの領域に分かれています。  
  
 フィードバック領域とデザイナーの領域は常に表示します。 進行状況バー、アニメーションの地域は常に動的なユーザーのコンテキスト ベース。 デザイナーの領域が、テキスト メッセージに付随するリソースから抽出された文字列の長さで決まる静的幅を持ちます。 これにより、ローカリゼーション、コードの変更を必要とせず、幅のサイズを変更できます。 英語、この文字列の幅はほぼ同じ値が 220 ピクセルです。 デザイナーの領域は通常の動作し、フィードバック領域が残りの領域を差し引かれます。  
  
 ステータス バーは IDE をデバッグ モードの場合などのさまざまな IDE 状態変更を通信することで、視覚的な効果と機能の値を追加するも色分け表示します。  
  
 ![IDE ステータス バーの色の変更](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901 02_IDEStatusBar")  
  
 **IDE ステータス バーの色**  
  
####  <a name="BKMK_EmbeddedInfobar"></a>埋め込まれた情報バー  
 情報バーは、ドキュメント ウィンドウまたはツール ウィンドウの上部にある状態または条件をユーザーに通知を使用できます。 ユーザーが簡単に操作を実行できるようにできるようにコマンドも提示できます。 情報バーは、標準のシェル コントロールです。 動作させ、IDE の他のユーザーと一貫性がないが、独自に作成しないでください。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)実装の詳細および使用ガイダンスについてはします。  
  
 ![情報バーを埋め込み](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901 03_EmbeddedInfobar")  
  
 **デバッグ履歴モードでは、IDE と同じ方法では、標準的なデバッグ モードで行われるように、エディターが応答しないをユーザーに警告に、情報バーは、ドキュメント ウィンドウに埋め込まれます。**  
  
####  <a name="BKMK_MouseCursorChanges"></a>マウス カーソルが変化  
 マウス カーソルを変更する場合は、VSColor サービスに関連付けられていますが、既に、カーソルに関連付けられている色を使用します。 カーソルが変化進行中の操作を示すために使用するだけでなく、ユーザーがドラッグ、ドロップ、またはオブジェクトを選択するために使用できるターゲットを合わせるゾーンにヒットします。  
  
 操作の場合、ユーザーが、これ以上の入力を表現することを妨げて使用可能なすべての CPU 時間を確保する必要がある場合にのみ、ビジー状態/待機カーソルを使用します。 マルチ スレッドを使用して適切に記述されたアプリケーションとほとんどの場合、ユーザーがその他の操作を実行できなくと時間をまれにする必要があります。  
  
 他の場所に表示された情報を要求する冗長カーソル変更が便利でことに注意してください。 は、ユーザーを解決する必要がありますが重要に何かを伝えるためしようとしているときに特に、ユーザーとの通信の唯一の方法として、カーソル変更しないでください。  
  
####  <a name="BKMK_NotSysProgressIndicators"></a>進行状況インジケーター  
 進行状況インジケーターは、完了するまで複数の数秒かかるプロセス中にユーザーにフィードバックを与えるため重要です。 進行状況インジケータを表示する、インプレース (近く起点の進行中の操作)、表示される埋め込みステータス バー、モーダル ダイアログ ボックス、または Visual Studio のステータス バーにします。 ガイダンスに従って[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)これらの使用と実装に関連します。  
  
####  <a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio の通知ウィンドウ  
 Visual Studio の通知ウィンドウでは、ライセンス、環境 (Visual Studio)、拡張、および更新プログラムに関する開発者に通知します。 ユーザーは、個々 の通知を閉じることができます。 または特定の種類の通知を無視することもできます。 無視される通知の一覧を管理する、**ツール > オプション**ページ。  
  
 通知ウィンドウは、現在の拡張ではありません。  
  
 ![Visual Studio の通知ウィンドウ](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901 06_VSNotificationsWindow")  
  
 **Visual Studio の通知ツール ウィンドウ**  
  
####  <a name="BKMK_ErrorList"></a>エラー一覧  
 エラー一覧内での通知は、エラーと警告をコンパイル中に発生し、ビルド プロセス、やその特定のコード エラーをコード内を移動することができますを示します。  
  
 ![エラー一覧](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901 08_ErrorList")  
  
 **Visual Studio でのエラー一覧**  
  
####  <a name="BKMK_EmbeddedStatusBars"></a>埋め込まれたステータス バー  
 IDE ステータス バー動的であるためと、クライアントの地域コンテキストをアクティブなドキュメント ウィンドウと、ユーザーのコンテキストやシステムの応答での更新情報に設定することは困難情報の継続的な表示を維持または長期的な上の状態を指定非同期プロセスです。 たとえば、IDE ステータス バーは複数の実行やすぐに対応可能な項目の選択のテストの実行結果の通知を適切なではありません。 ユーザーが、選択を行うか、プロセスを開始するドキュメントまたはツール ウィンドウのコンテキストでこのようなステータス情報を保持する重要です。  
  
 ![埋め込まれたステータス バー](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901 09_EmbeddedStatusBar")  
  
 **Visual Studio で埋め込みステータス バー**  
  
####  <a name="BKMK_WindowsTray"></a>Windows トレイ通知  
 システムの横にある通知領域は、Windows は、Windows タスク バーのクロックします。 多くのユーティリティとソフトウェア コンポーネントは、ユーザーが画面の解像度を変更したり、ソフトウェア更新プログラムを取得するように、システム全体のタスクのコンテキスト メニューを取得できるように、この領域にアイコンを提供します。  
  
 環境レベル通知は、Windows 通知領域ではなく、Visual Studio の通知ハブに表示される必要があります。  
  
####  <a name="BKMK_NotificationBubbles"></a>通知バブル  
 エディターまたはデザイナー内で情報提供を目的として、または Windows 通知領域の一部として、通知バブルを表示できます。 ユーザーは、重要でない通知の利点は、後で解決できる問題としてこれらのバブルを認識します。 バブルは、ユーザーがすぐに解決する必要がありますのある重要な情報に適さないものです。 通知バブルを使用すると、Visual Studio では、場合、[通知バブルの Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)です。  
  
 ![通知バブル](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901 07_NotificationBubbles")  
  
 **Visual Studio の使用、Windows 通知領域に通知バブル**  
  
##  <a name="BKMK_ProgressIndicators"></a>進行状況インジケーター  
  
### <a name="overview"></a>概要  
 進行状況インジケーターは、ユーザー フィードバックの提供の通知システムの重要な部分です。 プロセスおよび操作は完了時にユーザーを教えてくれるとします。 使い慣れたインジケーターの種類には、進行状況バー、スピン カーソル、およびアニメーションのアイコンが含まれます。 進行状況インジケーターの配置と型は、何が表示されているを含む、コンテキストとどのくらいの時間プロセスまたは操作の完了に要するに依存します。  
  
#### <a name="factors"></a>要因  
 、どのインジケーターの種類は適切な判断するためには、次の要素を決定する必要があります。  
  
1.  **タイミング:**操作にかかる時間の長さ  
  
2.  **モダリティ:**操作が (ロック、プロセスが完了するまで UI) の環境にモーダルかどうか  
  
3.  **永続的/非定常:**かどうか、進行状況の最終結果する必要があります報告や表示可能なは後で  
  
4.  **不確定/不定:**かどうかの操作終了時刻と進行状況を計算できます  
  
5.  **グラフィック/Textual 場所:**かどうか、進行状況やプロセスは、メッセージ、またはツリーのコントロールなどの特定のコントロールの本体でのキャプチャされたインライン  
  
6.  **近接:**進行状況をそれに関連する UI に近接するかどうか。 (可能性のある離れ、ステータス バーにすることなど、これには、プロセスを起動するボタンの近くにあるですか?)  
  
#### <a name="determinate-progress"></a>確定した進行状況  
  
|進行状況の種類|使用するタイミングと方法|メモ|  
|-------------------|-------------------------|-----------|  
|進行状況バー (不確定)|予想される所要時間の > 5 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。|**しない**アニメーションにテキストを埋め込みます。|  
|情報バー|コンテキストの UI に関連付けられたメッセージ。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)です。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。|**しない**を複数のプロセスを示す必要がある場合は、複数の情報バーを使用します。 積み上げ進行状況バーを使用してください。|  
|[出力] ウィンドウ|一時的な通知: アプリケーション レベルのプロセスにそのユーザーが必要な**確認**完了した後の詳細。|**しない**ユーザーが後でデータを参照する必要がある場合に使用します。|  
|ログ ファイル|場合 intransient 通知と組み合わせて使用することが重要と**保存**完了した後に詳細情報。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスをユーザーが**必要はありません**完了した後の詳細。<br /><br /> 表示される埋め込みの進行状況バーが含まれます。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。||  
  
#### <a name="indeterminate-progress"></a>不確定な進行状況  
  
|進行状況の種類|使用するタイミングと方法|メモ|  
|-------------------|-------------------------|-----------|  
|進行状況バー (不確定)|予想される所要時間の > 5 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。|**しない**アニメーションにテキストを埋め込みます。|  
|Ant (アニメーション化された水平方向のドット数)|サーバーへのラウンド トリップされます。<br /><br /> コンテキストの near ポイントは、親コンテナーの一番上に配置されます。|**しない**コンテナー全体を親として持たない場合に使用します。|  
|スピン ボックス (進行状況リング)|コンテキストの UI またはスペースがな考慮事項に関連付けられたプロセス。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。||  
|情報バー|コンテキストの UI に関連付けられたメッセージ。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)です。|**しない**を複数のプロセスを示す必要がある場合は、複数の情報バーを使用します。 積み上げ進行状況バーを使用してください。|  
|[出力] ウィンドウ|一時的な通知: アプリケーション レベルのプロセスそのユーザーはするが**確認**完了した後の詳細。|**しない**セッション中に維持する必要がある情報を使用します。|  
|ログ ファイル|場合 intransient 通知と組み合わせて使用することが重要と**保存**完了した後に詳細情報。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスをユーザーが**必要はありません**完了した後の詳細。<br /><br /> 埋め込みの進行状況バーが含まれます。<br /><br /> プロセスの詳細の説明テキストを含めることがあります。||  
  
### <a name="progress-indicator-types"></a>進行状況インジケーターの種類  
  
#### <a name="progress-bars"></a>進行状況バー  
  
##### <a name="indeterminate"></a>不確定です  
 ![不確定な進行状況バー](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901 04_Indeterminate")  
  
 **不確定な進行状況バー**  
  
 操作の全体的な進行状況を「不確定」を意味またはプロセスを特定することはできません。 操作を必要とする時間数がバインド解除済みまたは不明な数のオブジェクトにアクセスするには、不確定な進行状況バーを使用します。 何が起こっているかに付属するのに説明テキストを使用します。 タイムアウトを使用して、時間ベースの操作に範囲を与えます。 不確定な進行状況バーは、アニメーションを使用して、進行状況が出されているがその他の情報を指定しないことを示します。 単独での精度の考えられる不足のみに基づく不確定な進行状況バーを選択しないでください。  
  
##### <a name="determinate"></a>不定になります  
 ![確定した進行状況バー](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901 05_Determinate")  
  
 **確定した進行状況バー**  
  
 「不確定」を操作またはプロセスが必要になります、範囲指定された時間、期間を正確に予測できない場合でもです。 完了を明確に示します。 進行状況バーが 100% には、操作が完了しない限り、ことはありません。 確定した進行状況バーのアニメーションでは、左から右へを 0 から 100% に移動します。  
  
 操作中に旧バージョンとの進行状況インジケーターを動かすことはありません。 バーを前方に移動徐々 に、操作が開始されるときにし、これが終了すると 100% に到達します。 進行状況バーのポイントは、数の手順が必要に関係なく、操作全体のかかるがどのくらいの時間の概要を把握するためにです。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>同時実行 (積み上げ進行状況バー) のレポート  
 操作で、長い時間がかかる場合は、いくつかの分、2 つの進行状況バーを使用する可能性がありますおそらく、操作に対する全体的な進行状況と現在のステップの進行状況のいずれかを示しています。 たとえば、セットアップ プログラムは、多くのファイルをコピーして場合、プロセス全体の所要時間、2 番目は、現在のファイルの割合を示すことができます、またはディレクトリがコピーされるときに示すために 1 つの進行状況バーを使用できます。 複数の 5 つの同時実行操作または積み上げ進行状況バーを使用してプロセスを報告しません。 6 つ以上の同時実行操作やレポートにプロセスがあれば、モーダル ダイアログ ボックスで使用、[キャンセル] ボタンとレポートを出力ウィンドウに進行状況の詳細。  
  
##### <a name="textual-descriptions"></a>テキストの説明  
 何が起こっているかに付属する説明のテキストと、推定完了時刻を使用します。 操作の実行時間を判断する場合は、フィードバックの提供の方が適して可能性があります、進行状況バーではなく、アニメーションのアイコン。  
  
 Visual Studio には、Visual Studio に統合された任意の製品で使用できるステータス バーに標準の進行状況バーが用意されています。 進行状況バーがアニメーション処理中に何が起こっているかのテキスト説明については、ステータス バーのテキストを更新することができます。  
  
#### <a name="other-progress-indicators"></a>その他の進行状況インジケーター  
  
##### <a name="ants-animated-horizontal-dots"></a>Ant (アニメーション化された水平方向のドット数)  
 ![進行状況 ant](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903 01_Ants")  
  
 「アリ、」水平方向のアニメーションのドットは不確定なラウンド トリップ サーバー プロセスの視覚的な参照を提供します。  
  
##### <a name="spinner-progress-ring"></a>スピン ボックス (進行状況リング)  
 ![進行状況スピナー](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903 02_Spinner")  
  
 スピン ボックス"(とも呼ばれる、進行状況リング) は、コンテキストの UI に関連して、主に使用される、不確定な進行状況インジケーターです。 テキストのカテゴリ ヘッダー、メッセージング、またはコントロールなど、関連するコンテンツに近接、スピン ボックスを表示します。  
  
##### <a name="cursor-feedback"></a>カーソルからのフィードバック  
 2 ~ 7 秒かかる操作の場合は、カーソルのフィードバックを提供します。 つまり、通常、オペレーティング システムによって提供される待機カーソルを使用します。 ガイダンスについては、MSDN の記事を参照してください。 [Cursors.Wait プロパティ](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)です。  
  
#### <a name="progress-indicator-locations"></a>進行状況インジケーターの場所  
  
##### <a name="status-bar"></a>ステータス バー  
 ステータス バーには、ユーザーの作業を中断することがなく、メッセージと有用な情報をユーザーに表示する場所に、アプリケーションが与えられます。 ウィンドウの下部に通常表示するには、進行状況の状態になります、進行状況バーのインジケーターとの組み合わせでの進行状況の測定に関するメッセージを含むツール ヒント ウィンドウ。  
  
 ![進行状況バー付きのステータス バー](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903 03_StatusBarProgressBar")  
  
 **進行状況バー付きのステータス バー**  
  
 ![メッセージング付きのステータス バー](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903 04_StatusBarMessage")  
  
 **説明テキストをステータス バー**  
  
##### <a name="infobar"></a>情報バー  
 同様に、情報バー、ステータス バーが提供コンテキストの通知とメッセージング、するなど、進行状況バーまたはスピン不確定な進行状況インジケーターのペアリングもできます。 詳細なレベルの進行状況や確定した進行状況を示す値、情報バーは提供しません必要があります。 参照してください[情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)です。  
  
 ![進行状況バーとメッセージング付きの情報バー](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903 05_InfoBar")  
  
 **進行状況バーと説明テキストを含むページ**  
  
 ![ウィンドウ内の情報バー](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903 06_InfoBarInWindow")  
  
 **コード分析 ウィンドウ内の情報バー**  
  
##### <a name="inline"></a>インライン  
 インラインの進行状況を示す値は、いずれかの進行状況ローダー型で表すことができます。 通常の進行状況インジケーターとペアになり、メッセージングしますが、必要ではありません。  
  
 ![インラインの進行状況スピナー](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903 07_InlineSpinner")  
  
 **スピン ボタンの説明テキストと組み合わせる**  
  
 ![インラインの積み上げ進行状況バー](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903 08_InlineStackedProgress")  
  
 **不確定の積み上げ進行状況バー**  
  
 ![インラインの進行状況メッセージング](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903 09_InlineText")  
  
 **サーバー エクスプ ローラーのインライン テキスト: を更新しています.**  
  
##### <a name="tool-windows"></a>ツール ウィンドウ  
 グローバルの進行状況の表示は、ツールバーのすぐ下に配置されている不確定な進行状況バーで表されます。  
  
 ![グローバル不確定な進行状況バー](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903 23_GlobalIndeterminate")  
  
 **チーム エクスプ ローラーのグローバル不確定な進行状況バー**  
  
##### <a name="dialogs"></a>ダイアログ ボックス  
 ダイアログ ボックスには、いずれかの進行状況ローダー型を含めることができます。 進行状況インジケーターするメッセージングと組み合わせて使用したりできるようを細分化されたおよびサブ プロセスに進行状況を示す値の複数のレベルと組み合わせて使用します。  
  
 ![複数の進行状況インジケーターの種類を持つダイアログ](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903 11_Dialog")  
  
 **同時実行プロセスと複数の進行状況インジケーターの種類の visual Studio ダイアログ**  
  
 ![ダイアログの進行状況ローダーとメッセージングを](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903 12_Dialog2")  
  
 **進行状況ローダーとメッセージング インライン コマンドの実行に visual Studio のダイアログ**  
  
##### <a name="document-well"></a>ドキュメント ウェル  
 ドキュメントは、コントロールとの組み合わせで複数の進行状況ローダーの種類を表示できます。  
  
 ![進行状況もドキュメントのメッセージング](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903 13_DocumentWell")  
  
 **ツールバーの下の不確定な進行状況バー**  
  
##### <a name="output-window"></a>[出力] ウィンドウ  
 出力ウィンドウは、プロセスの流れとインライン テキスト メッセージングを使用して継続的な処理の進行状況の処理に適しています。 出力ウィンドウの進行状況レポートとステータス バーを使用する必要があります。  
  
 ![[出力] ウィンドウでのメッセージングの進行状況](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903 14_OutputWindow")  
  
 **継続的なプロセスの状態と出力ウィンドウ、メッセージを待ちます**  
  
##  <a name="BKMK_Infobars"></a>情報バー  
  
### <a name="overview"></a>概要  
 情報バーのアテンションのポイントの近くにインジケーターをユーザーに付与し、視覚的な外観との相互作用の一貫性を確保共有情報バー コントロールを使用します。  
  
 ![情報バー](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904 01_Infobar")  
  
 **Visual Studio での情報バー**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>情報バーの適切な使用方法  
  
-   ユーザーに提供する、現在のコンテキストに関連する非ブロッキングしますですが、重要なメッセージ  
  
-   いくつかの対話に影響を及ぼしますデバッグ履歴などを実行する UI が特定の状態または条件であることを示します  
  
-   システムが拡張機能でパフォーマンスの問題が原因となってときなどの問題を検出されたことをユーザーに通知するには  
  
-   エディターのタブとスペース ファイルが混在ことが検出された場合など、アクションを簡単に実行する方法をユーザーに提供するには  
  
##### <a name="do"></a>操作を行います。  
  
-   短いと、ポイントには、情報バーのメッセージ テキストを保持します。  
  
-   簡潔なリンクやボタンのテキストを保持します。  
  
-   ユーザーに提供する、"action"オプションを最小限に抑える必要な操作のみを表示を確認します。  
  
##### <a name="dont"></a>できません：  
  
-   情報バーを使用すると、ツールバーに配置する必要がある標準のコマンドを提供できます。  
  
-   モーダル ダイアログ ボックスの代わりに、情報バーを使用します。  
  
-   フローティング ウィンドウ外メッセージを作成します。  
  
-   同じウィンドウ内のいくつかの場所で複数の情報バーを使用します。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>同時に複数の情報バーを表示できますか。  
 [はい]、同時に複数の情報バーを表示できます。 これらが表示されます、先着順に上およびその他の情報バーを示す下に表示されている最初の情報バー。  
  
 ユーザーは、一度に最大 3 つの情報バーを参照してください、多くの情報バーがある場合、情報バー領域になるスクロール可能な後です。  
  
### <a name="creating-an-infobar"></a>情報バーを作成します。  
 情報バーには、左から右への 4 つのセクションがあります。  
  
-   **アイコン:**これは、いずれかのアイコンを追加することの警告アイコンなどの情報バーを表示したいです。  
  
-   **Text:**シナリオ/状況ユーザーを説明するテキストには、テキスト内へのリンクと共には追加できます必要な場合です。 簡潔なテキストを保持してください。  
  
-   **アクション:**このセクションでは、リンクや、情報バーで、ユーザーが実行できるアクションのボタンを含める必要があります。  
  
-   **[閉じる] ボタン:**右側に最後のセクションは、[閉じる] ボタンを持つことができます。  
  
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
  
 ![ハイパーリンクを含むページ](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904 02_InfobarHyperlink")  
  
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
 ネイティブ コードからの情報バーを提供するために、IVsInfoBar インターフェイスを実装します。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>情報バーからの情報バー ui 要素の取得  
 InfoBarModel または IVsInfoBar の実装は、UI に表示するために、ui 要素に変換する必要がありますをデータ モデルです。 SVsInfoBarUIFactory/IVsInfoBarUIFactory サービスと、ui 要素を取得できます。  
  
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
 情報バーは、次の場所の 1 つ以上で表示されます。  
  
-   ツール ウィンドウ  
  
-   ドキュメント タブ内  
  
> [!IMPORTANT]
>  グローバルなコンテキストに関するメッセージを提供する情報バーを配置することができます。 これは、ツールバーと、ドキュメント ウェルの間で表示されます。 これは推奨されません「ジャンプし、動かさない」に問題が発生するため、IDE の場合を除き、避ける必要があります、どうしても必要であり適切な。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane に情報バーを配置します。  
 ToolWindowPane.AddInfoBar(IVsInfoBar) メソッドは、ツール ウィンドウに情報バーを追加するために使用できます。 この API は、(どの InfoBarModel は、既定の実装) IVsInfoBar を追加できますか、または、IVsUIElement です。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>ドキュメントまたは ToolWindowPane 以外に、情報バーを配置します。  
 任意 IVsWindowFrame に情報バーを配置するには、VSFPROPID_InfoBarHost プロパティを使用して、フレームの IVsInfoBarHost を取得し、情報バーの ui 要素を追加します。  
  
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
  
#### <a name="placing-an-infobar-in-the-main-window"></a>メイン ウィンドウに情報バーを配置します。  
 メイン ウィンドウで、情報バーを配置するには、VSSPROPID_MainWindowInfoBarHost ivsshell でサービスを使用して、メイン ウィンドウの IVsInfoBarHost を取得して、情報バーの ui 要素を追加します。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>自分の情報バーで、ユーザーが操作を知ってですか。  
 はい、おはすべてのイベントのアクションを返します、情報バーの作成者。 アクションを実行するバーに表示されるユーザーの選択に基づいて IDE 情報バーの作成者の責任です。 情報バーを持つ閉じるボタンがクリックしてされました、ホストから自動的に削除されますが、後に削除するその他の情報バーの必要性を閉じる場合は、追加の作業が必要です。 製品利用統計情報は、各バーによって個別に記録される必要があります。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane 情報バーのイベントの受信  
 ToolWindowPane には、情報バーの 2 つのイベントがあります。 InfoBarClosed イベントは、ToolWindowPane の情報バーが閉じられたときに発生します。 ハイパーリンクまたは内の情報バー ボタンがクリックされたときに、InfoBarActionItemClicked イベントが発生します。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement から直接情報バーのイベントの受信  
 情報バーの UIElement から直接イベントをサブスクライブする IVsInfoBarUIElement.Advise を使用できます。 IVsInfoBarUIEvents を実装すると、閉じる受信し、クリックしてイベントの作成者が許可されます。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="BKMK_ErrorValidation"></a>エラーの検証  
 入力すると、ユーザー情報は、必須フィールドをスキップする場合など、または不適切な形式でデータを入力するときに使用できませんが、使用するコントロールの検証またはブロックしているポップアップ エラー ダイアログ ボックスを使用する代わりに、コントロールの近くのフィードバックをことをお勧めします。  
  
### <a name="field-validation"></a>フィールドの検証  
 フォームとフィールドの検証は、3 つのコンポーネントで構成されています: コントロール、アイコン、およびツールヒント。 いくつかの種類のコントロールには、これを使用できる、テキスト ボックスは、例として使用されます。  
  
 ![フィールドの検証 &#40;空白&#41;] (../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905 01_FieldValidation")  
  
 フィールドが必要な場合がありますを示すテキストが透かし**\<必要 >**フィールド背景が薄いをする必要があります黄色 (VSColor: `Environment.ControlEditRequiredBackground`)、フォア グラウンドがグレー表示にする必要があります (VSColor: `Environment.ControlEditRequiredHintText`)。  
  
 ![「必須」のラベルを持つ検証をフィールド](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905 02_FieldValidationRequired")  
  
 プログラムでは、コントロールの状態を判断できます*に入力された無効なコンテンツ*か別のコントロールにフォーカスを移動した場合、ユーザーが [OK] のコミット ボタンをクリックしたときか、ユーザーが文書またはフォームを保存するときにします。  
  
 無効なコンテンツの状態が確認された場合、コントロールの内部、または同様の横にアイコンが表示されます。 アイコンまたはコントロールのいずれかのホバー時のエラーを説明するツールヒントが表示されます。 さらに、無効な状態を作成しているコントロールの周囲に 1 ピクセルの境界線を表示します。  
  
 ![検証のレイアウトの仕様をフィールド](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905 03_LayoutSpecs")  
  
 **フィールドの検証のレイアウトの仕様**  
  
#### <a name="acceptable-variations-for-icon-location"></a>アイコンの場所のバリエーションを許容  
 ユーザーで検証エラーの通知が必要になる無数の特別なケースがあります。 考慮すると、コントロールの種類と、UI の構成には、自分の状況に該当するアイコンの配置を選択します。  
  
 ![アイコンの場所の場所の適切な](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905 04_IconLocation")  
  
 **許容されるバリエーションのフィールドの検証 アイコンの場所**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>サーバーまたはネットワーク接続へのラウンド トリップを必要とする検証  
 場合によっては、サーバーへのラウンド トリップが、コンテンツの検証に必要なし、認証されると、ユーザーの進行状況とエラー状態を表示することがあります。 次の図には、このケース テーブルと、推奨される UI の例を示します。  
  
 ![サーバーへのラウンド トリップに関連する検証](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905 05_RoundTrip")  
  
 **サーバーへのラウンド トリップに関連する検証**  
  
 「を確認しています...」と「再試行」のテキストが収まるように、コントロールの右側に十分な空き領域を指定する必要がありますに注意してください。  
  
#### <a name="in-place-warning-text"></a>インプレース警告テキスト  
 エラーの状態で、コントロールの近くに、エラー メッセージを配置に使用できる空きスペースがある場合は、単独でツールヒントを使用してこれをお勧めします。  
  
 ![&#45; 場所警告](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905 06_InPlaceWarning")  
  
 **インプレース警告テキスト**  
  
#### <a name="watermarks"></a>透かし  
 場合によって、コントロール全体またはウィンドウがエラー状態です。 このような状況では、エラーを示すために透かしを使用します。  
  
 ![ウォーターマーク](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905 07_Watermark")  
  
 **透かしのフィールドの検証**