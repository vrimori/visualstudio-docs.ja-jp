---
title: "通知と Visual Studio の進行状況 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 6
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
ms.openlocfilehash: 1f7823754601161200edafdce998ebe9aeab2723
ms.lasthandoff: 02/22/2017

---
# <a name="notifications-and-progress-for-visual-studio"></a>通知と Visual Studio の進行状況
##  <a name="a-namebkmknotificationsystemsa-notification-systems"></a><a name="BKMK_NotificationSystems"></a>通知システム  
  
### <a name="overview"></a>概要  
 何が起こっているか Visual Studio で、ソフトウェア開発タスクに関するユーザーに通知するいくつかの方法があります。  
  
 なんらかの通知の実装: 時  
  
-   **最小値への通知の数を保持する**効果的な番号です。 通知メッセージは、大半の Visual Studio のユーザーまたは特定の機能/機能区分のユーザーに適用される必要があります。 通知の過剰な使用は、sidetrack ユーザーまたは知覚可能なシステムの使いやすさが低下する可能性があります。  
  
-   **クリア、実践的なメッセージを提供することを確認**をさらに複雑な選択を行うとさらにアクションを起こすの適切なコンテキストを呼び出すにはユーザーを使用できます。  
  
-   **同期および非同期のメッセージを適切に表示します。** 同期の通知は、早急に措置が必要な web サービスがクラッシュしたときや、コードなど、例外がスローされることを示しています。 モーダル ダイアログ ボックスなどの入力を必要とするように今すぐこのような状況のユーザーに通知する必要があります。 非同期の通知は、ユーザーについて知っておくべきする必要はありません、すぐに操作など、ビルド操作が完了したときに、または、web サイトのデプロイが終了したものです。 これらのメッセージのよりアンビエントとユーザーのタスクのフローを中断しない必要があります。  
  
-   **モーダル ダイアログ ボックスをユーザーがさらにアクションを実行するを防ぐために必要な場合にのみを使用して**メッセージの受信確認またはダイアログ ボックスに表示される決定を行う前にします。  
  
-   **有効でなくなったときに、アンビエント通知を削除します。** ユーザーが通知された問題に対処するため、既に実行している場合、通知を破棄する必要はありません。  
  
-   **通知が誤った相関関係につながることに注意してください。** ユーザーとお考えの対処法の&1; つ以上が生成されたことを通知実際と因果関係がない場合。 コンテキスト、トリガー、および通知のソースに関する通知メッセージのチェック ボックスをオフにします。  
  
### <a name="choosing-the-right-method"></a>適切な方法を選択します。  
 このテーブルを使用して、メッセージのユーザーに通知する正しい方法を選択する際に役立ちます。  
  
|メソッド|用途|使用しないでください。|  
|------------|---------|----------------|  
|[モーダル エラー メッセージ ダイアログ ボックス](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|続行する前にユーザーからの応答が必要な場合に使用します。|ユーザーをブロックし、そのフローを中断する必要がない場合に使用しないでください。 簡単、別の方法でメッセージが表示可能な場合は、モーダル ダイアログ ボックスを使用しないでください。|  
|[IDE のステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|プロセスの状態に関するアンビエント テキスト情報がある場合に使用します。|単独では使用しません。 他のフィードバック メカニズムと組み合わせて使用最適です。|  
|[埋め込まれた情報バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|ツール ウィンドウまたはドキュメント ウィンドウでは、進行状況、エラー状態、結果、および実践的な情報の通知を使用します。|情報は、情報バーが配置される場所に関係がない場合は使用しないでください。<br /><br /> ドキュメント/ツール ウィンドウの外側は使用しないでください。|  
|[マウス カーソルが変化](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|プロセスが起こっていることを通知に使用できます。 ドラッグ アンド ドロップ操作が進行中かをマウスのカーソルは描画モードなどの特定のモードなど、マウスの状態の変化があることを通知にも使用されます。|短い進行中の変更には使用しないで、またはカーソルのどきどき場合 (たとえば、プロセス全体の代わりに長い時間実行中のプロセスの部分に関連付けられている) 場合は、可能性があります。|  
|[進行状況インジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|(有限または不確定)、進行状況を報告する必要がある場合に使用します。 さまざまな進行状況インジケーターの種類とそれぞれの具体的な使用方法があります。 参照してください[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)します。||  
|[Visual Studio の通知ウィンドウ](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|通知ウィンドウは、パブリックに拡張可能ではありません。 ただし、重要な問題を実際のライセンスと Visual Studio をまたはパッケージに更新プログラムの情報を通知など、Visual Studio に関するメッセージの範囲を通信するために使用されます。|その他の種類の通知を使用しないでください。|  
|[エラー一覧](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|問題は、問題 (エラー/警告/情報) を持つユーザーの現在開いているソリューションに直接関係している場合は、コードにアクションを実行する必要があります。<br /><br /> これは、たとえば含まれます。<br /><br /> コンパイラ メッセージ (エラー/警告/情報)<br /><br /> コードのコード分析/診断メッセージ<br /><br /> -メッセージを構築します。<br /><br /> 可能性がありますが、ソリューションまたはプロジェクトのファイルに関連する問題に適している、ソリューション エクスプ ローラーを示す値を最初に検討してください。|ユーザーのソリューションを開くコードへの関係がない項目を使用しないでください。|  
|エディターの通知: の Light Bulb|開いているファイルに存在する問題を解決するための修正プログラムがある場合に使用します。<br /><br /> 電球はリファクタリングなどの要求時にユーザーのコードで取得されているが、その場合は「通知スタイル」クイック操作をホストするためも使用する必要があります。|開いているファイルへの関係を持たない項目を使用しないでください。|  
|エディターの通知: 波線|開いているコード (たとえば、エラーの赤の波線) の特定の範囲の問題にユーザーに警告を使用します。|開いているコードの特定の期間に関係なく項目を使用しないでください。|  
|[埋め込まれたステータス バー](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|使用すると、コンテンツまたは特定のツール ウィンドウ、ドキュメント ウィンドウまたはダイアログ ウィンドウのコンテキスト内のプロセスに関連する状態を提供します。|一般的な製品の通知、プロセス、または特定のウィンドウ内で、コンテンツへの関係を持たない項目に対しては使用しないでください。|  
|[Windows トレイ通知](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|アウト プロセスのプロセスの通知を表示またはアプリケーションのコンパニオン使用します。|IDE に関連する通知を使用しないでください。|  
|[通知バブル](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|リモート プロセスの通知や変更に使用**外**IDE のです。|プロセスのユーザーに通知するための手段として使用しないで**内**IDE です。|  
  
### <a name="notification-methods"></a>通知方法  
  
####  <a name="a-namebkmkmodalerrormessagedialogsa-modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>モーダル エラー メッセージ ダイアログ ボックス  
 モーダル エラー メッセージ ダイアログ ボックスを使用して、ユーザーの確認またはアクションを必要とするエラー メッセージを表示できます。  
  
 ![モーダル エラー メッセージ](~/extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901&01;_ModalErrorMessage")  
  
 **データベースへの無効な接続文字列のユーザーに警告モーダル エラー メッセージ ダイアログ ボックス**  
  
####  <a name="a-namebkmkidestatusbara-ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE のステータス バー  
 そのオールラウンドのコンピューターや Windows プラットフォームの特定のエクスペリエンスに関連している可能性をユーザーがステータス バーのテキストに注意してください。 Visual Studio の顧客ベースも知識の豊富な Windows ユーザーは、ステータス バーに変更を見落とす可能性がありますが、両方の領域で発生する傾向があります。 そのため、ステータス バーは、最適な参考のためまたはとして使用、冗長的な通知の他の場所の情報が表示されます。 ダイアログ ボックスで、または、通知ツール ウィンドウには、任意の種類の重要な情報が、ユーザーはすぐに解決する必要がありますを指定する必要があります。  
  
 Visual Studio のステータス バーが表示される情報のいくつかの種類を許可するように設計されています。 フィードバック、デザイナー、進行状況バー、アニメーション、およびクライアントの領域に分かれています。  
  
 フィードバックの領域とデザイナーの領域は常に表示します。 進行状況バーとアニメーションの領域は、常に動的であり、ユーザー コンテキストに基づいています。 デザイナーの領域が、テキスト メッセージに付随するリソースから抽出された文字列の長さによって決まります静的な幅を持ちます。 これにより、コードの変更を必要とせず、幅のサイズを変更するローカライズできます。 英語、この文字列の幅はほぼ同じ値が 220 ピクセルです。 デザイナーの領域は通常の動作し、フィードバックの領域には、残りの領域を吸収します。  
  
 ステータス バーは IDE がデバッグ モードであるときなどのさまざまな IDE 状態変更を通信することで、視覚的な効果と関数型の値を追加も色分け表示します。  
  
 ![IDE ステータス バーの色の変更](~/extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901&02;_IDEStatusBar")  
  
 **IDE ステータス バーの色**  
  
####  <a name="a-namebkmkembeddedinfobara-embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>埋め込まれた情報バー  
 状態または条件のユーザーに通知するツール ウィンドウまたはドキュメント ウィンドウの上部にある情報バーを使用できます。 コマンドは、ユーザーが簡単に対処する方法を得られるようにも提供できます。 情報バーは、標準のシェル コントロールです。 機能し、IDE で一貫性のない他のユーザーが表示されますが、独自に作成しないでください。 参照してください[情報の表示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)の実装の詳細と使用のガイダンスです。  
  
 ![情報バーが埋め込まれている](~/extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901&03;_EmbeddedInfobar")  
  
 **デバッグ履歴モードで、IDE があり、エディターと標準的なデバッグ モードでは、同じ方法で応答があるユーザーに警告に、情報バーは、ドキュメント ウィンドウに埋め込まれます。**  
  
####  <a name="a-namebkmkmousecursorchangesa-mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>マウス カーソルが変化  
 マウス カーソルを変更する場合は VSColor サービスに関連付けられ、カーソルに関連付けられている色を使用します。 カーソルが変化進行中の操作を示すために使用するだけでなく、ユーザーは、ドラッグ、ドロップ、またはオブジェクトを選択するために使用できるターゲットを置くゾーンにヒットします。  
  
 さらに、入力を表現するため、ユーザー操作で使用可能なすべての CPU 時間を確保する必要が場合にのみ、ビジー/待機カーソルを使用します。 マルチ スレッドを使用して適切に記述されたアプリケーションにほとんどの場合、ユーザーがその他の操作を実行できなくと時間は、まれなする必要があります。  
  
 詳細については、冗長的な通知が表示された別の場所でカーソルの変更は便利なことに注意してください。 カーソルの変更は、ユーザーがおく必要がある重要な何かを伝えるためにしようとしている場合は特に、ユーザーとの通信の唯一の方法としては依存しないでください。  
  
####  <a name="a-namebkmknotsysprogressindicatorsa-progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>進行状況インジケーター  
 進行状況インジケーターは、完了に多くの数秒を要するプロセス中にユーザーにフィードバックを提供するため重要です。 進行状況インジケータを表示できる、インプレース (近く起点の進行中の操作)、埋め込みステータス バー、モーダル ダイアログ ボックス、または Visual Studio のステータス バーにします。 ガイダンスに従って[進行状況のインジケーター](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)これらの使用と実装に関連します。  
  
####  <a name="a-namebkmkvsnotificationstoolwindowa-visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio の通知ウィンドウ  
 Visual Studio の通知ウィンドウでは、ライセンス、環境 (Visual Studio)、拡張機能、および更新プログラムに関する開発者に通知します。 ユーザーは、個々 の通知を閉じることまたはを特定の種類の通知を無視できます。 無視される通知の一覧を管理する、**ツール > オプション**ページです。  
  
 通知ウィンドウは、現在の拡張ではありません。  
  
 ![Visual Studio の通知ウィンドウ](~/extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901&06;_VSNotificationsWindow")  
  
 **Visual Studio の通知ツール ウィンドウ**  
  
####  <a name="a-namebkmkerrorlista-error-list"></a><a name="BKMK_ErrorList"></a>エラー一覧  
 エラーの一覧で通知を示すエラーや警告のコンパイル中に発生やビルド プロセス、およびその特定のコード エラーをコード内を移動することができます。  
  
 ![エラー一覧](~/extensibility/ux-guidelines/media/0901-08_errorlist.png "0901&08;_ErrorList")  
  
 **Visual Studio でのエラー一覧**  
  
####  <a name="a-namebkmkembeddedstatusbarsa-embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>埋め込まれたステータス バー  
 IDE のステータス バー動的であるため、アクティブなドキュメント ウィンドウと、ユーザーのコンテキストやシステムの応答の更新情報を設定、クライアント領域のコンテキストで情報の継続的な表示を維持または長期的な非同期プロセスの状態を与えるにくくなっています。 たとえば、IDE のステータス バーは複数の実行やすぐに対応可能な項目の選択のテストの実行結果の通知を適切なではありません。 ユーザーが、選択を行うか、プロセスを開始するドキュメントまたはツール ウィンドウのコンテキストでこのようなステータス情報を保持する重要です。  
  
 ![埋め込まれたステータス バー](~/extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901&09;_EmbeddedStatusBar")  
  
 **Visual Studio で埋め込みステータス バー**  
  
####  <a name="a-namebkmkwindowstraya-windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows トレイ通知  
 システムの横にある通知領域は、Windows は、Windows タスク バーで、クロックします。 多くのユーティリティとソフトウェア コンポーネントは、ユーザーは、画面の解像度を変更したり、ソフトウェア更新プログラムを取得するなど、システム全体のタスクにコンテキスト メニューを取得できるように、この領域にアイコンを提供します。  
  
 環境レベル通知は、Windows 通知領域ではなく、Visual Studio の通知ハブに表示する必要があります。  
  
####  <a name="a-namebkmknotificationbubblesa-notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>通知バブル  
 通知バブルは、エディターとデザイナー内で情報または Windows 通知領域の一部として指定できます。 ユーザーは、重要でない通知向けの特典は、後で解決できる問題としてこれらのバブルを認識します。 バブルでは、大文字と小文字は重要な情報、ユーザーがすぐに解決する必要がありますが適していません。 次の Visual Studio で通知バブルを使用する場合、[通知バブルの Windows デスクトップ ガイダンス](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742472\(v=vs.85\).aspx)します。  
  
 ![通知バブル](~/extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901&07;_NotificationBubbles")  
  
 **Visual Studio の使用 Windows 通知領域に通知バブル**  
  
##  <a name="a-namebkmkprogressindicatorsa-progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>進行状況インジケーター  
  
### <a name="overview"></a>概要  
 進行状況インジケーターは、ユーザーにフィードバックを提供するための通知システムの重要な部分です。 プロセスと操作が完了したときに、ユーザーに通知します。 使い慣れたインジケーターの種類には、進行状況バー、スピン カーソル、およびアニメーションのアイコンが含まれます。 型と進行状況インジケーターの配置は、完了までにレポートされている情報を含む、コンテキスト、プロセスまたは操作をどのくらいの時間がかかるに依存します。  
  
#### <a name="factors"></a>要素  
 、どのインジケーターの種類では適切な判断するためには、次の要素を決定する必要があります。  
  
1.  **時間:**操作にかかる時間の長さ  
  
2.  **モダリティ:**操作が (ロック処理が完了するまで UI) の環境にモーダルかどうか  
  
3.  **永続的または一時的な:**は後で報告されたや表示可能である進行状況の最終的な結果が必要かどうか  
  
4.  **不確定/中間状態:**かどうか、操作の終了時刻と進行状況を計算できます  
  
5.  **グラフィック/Textual 場所:**かどうか、進行状況やプロセスは、メッセージ、またはツリー コントロールなどの特定のコントロールの本体でのキャプチャされたインライン  
  
6.  **近接:**進行状況が近くに関連付けられている UI にするかどうか。 など可能性のある遠く、ステータス バーにあることができます (これは、プロセスを起動するボタンの近くにする必要でしょうか。)  
  
#### <a name="determinate-progress"></a>確定した進行状況  
  
|進行状況の種類|使用するタイミングと方法|ノート|  
|-------------------|-------------------------|-----------|  
|進行状況バー (不定になります)|予想される所要時間の >&5; 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**アニメーションにテキストを埋め込みます。|  
|情報バー|コンテキストの UI に関連付けられたメッセージ。 参照してください[情報の表示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**を複数のプロセスを示す必要がある場合、複数の情報の表示を使用します。 積み上げ進行状況バーを使用してください。|  
|[出力] ウィンドウ|一時的な通知: アプリケーション レベルのプロセスにそのユーザーが必要な**確認**完了した後の詳細。|**しない**ユーザーが後でデータを参照する必要がある場合に使用します。|  
|ログ ファイル|Intransient 通知の場合と組み合わせて使用することが重要と**保存**完了した後に詳細です。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスのユーザーは**必要はありません**完了した後の詳細。<br /><br /> 埋め込みの進行状況バーが含まれます。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
  
#### <a name="indeterminate-progress"></a>不確定な進行状況  
  
|進行状況の種類|使用するタイミングと方法|ノート|  
|-------------------|-------------------------|-----------|  
|進行状況バー (中間)|予想される所要時間の >&5; 秒です。<br /><br /> プロセスの詳細の説明テキストを含めることができます。|**しない**アニメーションにテキストを埋め込みます。|  
|Ants (水平方向のドットをアニメーション化された)|サーバーへのラウンド トリップされます。<br /><br /> コンテキストの near ポイントは、親コンテナーの上部に配置されます。|**しない**コンテナー全体を親として持たない場合に使用します。|  
|スピン ボックス (進行状況リング)|コンテキストの UI またはスペースが重要な考慮事項に関連付けられたプロセス。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
|情報バー|コンテキストの UI に関連付けられたメッセージ。 参照してください[情報の表示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。|**しない**を複数のプロセスを示す必要がある場合、複数の情報の表示を使用します。 積み上げ進行状況バーを使用してください。|  
|[出力] ウィンドウ|一時的な通知: ユーザーが必要なアプリケーション レベルのプロセス**確認**完了した後の詳細。|**しない**セッション間で保持する必要がある情報を使用しています。|  
|ログ ファイル|Intransient 通知の場合と組み合わせて使用することが重要と**保存**完了した後に詳細です。||  
|ステータス バー|一時的な通知: アプリケーション レベルのプロセスのユーザーは**必要はありません**完了した後の詳細。<br /><br /> 埋め込みの進行状況バーが含まれます。<br /><br /> プロセスの詳細の説明テキストを含めることができます。||  
  
### <a name="progress-indicator-types"></a>進行状況インジケーターの種類  
  
#### <a name="progress-bars"></a>進行状況バー  
  
##### <a name="indeterminate"></a>不確定  
 ![不確定な進行状況バー](~/extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901&04;_Indeterminate")  
  
 **不確定な進行状況バー**  
  
 プロセスを特定できないや操作の全体的な進行状況を「中間」にことです。 不確定な進行状況バーを使用して、操作を非制限時間を必要とする、または不明な数のオブジェクトにアクセスします。 何が起こっているかに付属するのに説明文を使用します。 タイムアウトを使用して、時間ベースの操作に境界を与えます。 不確定な進行状況バーは、アニメーションを使用して、進行状況が出されているは、その他の情報を提供しないことを示します。 精度だけでの考えられる不足にのみ基づいて不確定な進行状況バーを選択しないでください。  
  
##### <a name="determinate"></a>不確定であります。  
 ![確定した進行状況バー](~/extensibility/ux-guidelines/media/0901-05_determinate.png "0901&05;_Determinate")  
  
 **確定した進行状況バー**  
  
 「不確定」を意味操作またはプロセスが制限された時間が必要である場合でも、その時間を正確に予測できないです。 入力候補が明確に表示します。 進行状況バーが 100% には、操作が完了しない限り、ことはありません。 確定した進行状況バーのアニメーションでは、左から右へを 0 から 100% に移動します。  
  
 操作中に旧バージョンとの進行状況インジケーターを動かすことはありません。 バー必要があります進め徐々 に、操作の開始時に、それが終了すると 100% に到達します。 進行状況バーのポイントは、数の手順に関係なく、操作全体のかかるがどのくらいの期間を理解するためにです。  
  
##### <a name="concurrent-reporting-stacked-progress-bars"></a>同時実行 (積み上げ進行状況バー) をレポート作成  
 操作に長い時間がかかる場合、いくつかの分、2 つの進行状況バーを使用することがあります、いずれかを示す操作に対する全体的な進行状況と現在のステップの進行状況。 たとえば、セットアップ プログラムは、多くのファイルをコピーして場合、プロセス全体にかかる&1; 秒間、現在のファイルの割合はどれかがわかりますまたはディレクトリがコピーされるときを示すために&1; つの進行状況バーを使用できます。 複数の&5; つの同時操作または積み上げ進行状況バーを使用してプロセスをレポートしません。 5 つ以上の同時操作やレポートにプロセスがあれば、モーダル ダイアログを使用し、[キャンセル] ボタンとレポートを出力ウィンドウに進行状況の詳細。  
  
##### <a name="textual-descriptions"></a>テキストの説明  
 何が起こっているかに付属する説明のテキストと、推定完了時刻を使用します。 操作の実行時間を判断することはできませんし、フィードバックの提供の方が適してあります進行状況バーではなく、アニメーションのアイコン。  
  
 Visual Studio には、Visual Studio に統合されたすべての製品で使用できるステータス バーに標準の進行状況バーが用意されています。 進行状況バーがアニメーション化中に何が起こっているかのテキストについては、ステータス バーのテキストを更新することができます。  
  
#### <a name="other-progress-indicators"></a>その他の進行状況インジケーター  
  
##### <a name="ants-animated-horizontal-dots"></a>Ants (水平方向のドットをアニメーション化された)  
 ![進行状況 ant](~/extensibility/ux-guidelines/media/0903-01_ants.png "0903&01;_Ants")  
  
 「アリ、」水平方向のアニメーションのドットは不確定なラウンドト リップ サーバー プロセスの視覚的な参照を提供します。  
  
##### <a name="spinner-progress-ring"></a>スピン ボックス (進行状況リング)  
 ![進行状況スピナー](~/extensibility/ux-guidelines/media/0903-02_spinner.png "0903&02;_Spinner")  
  
 スピン ボックス (別名「の進行状況リング」) は、コンテキストの UI に関連して、主に使用される、不確定な進行状況インジケーターです。 テキスト カテゴリ ヘッダー、メッセージ、またはコントロールなどの関連するコンテンツの近くに、スピン ボックスを表示します。  
  
##### <a name="cursor-feedback"></a>カーソルからのフィードバック  
 2. ~ 7. 秒かかる操作では、カーソルからのフィードバックを提供します。 通常は、オペレーティング システムによって提供される待機カーソルを使用することです。 ガイダンスについては、MSDN の記事を参照してください。 [Cursors.Wait プロパティ](https://msdn.microsoft.com/en-us/library/system.windows.input.cursors.wait\(v=vs.110\).aspx)します。  
  
#### <a name="progress-indicator-locations"></a>進行状況インジケーターの位置  
  
##### <a name="status-bar"></a>ステータス バー  
 ステータス バーには、ユーザーの作業を中断することがなく、メッセージと有用な情報をユーザーに表示するための場所に、アプリケーションが与えられます。 進行状況の状態は、通常、ウィンドウの下部に表示される、進行状況バー インジケーターと組み合わせて、進行状況の測定に関するメッセージを含むツール ヒントのウィンドウをなります。  
  
 ![進行状況バー付きのステータス バー](~/extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903&03;_StatusBarProgressBar")  
  
 **進行状況バー付きのステータス バー**  
  
 ![メッセージング付きのステータス バー](~/extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903&04;_StatusBarMessage")  
  
 **説明テキスト付きのステータス バー**  
  
##### <a name="infobar"></a>情報バー  
 同様、ステータス バーにある情報バーに提供します。 コンテキストの通知やメッセージングこれ不確定な進行状況インジケーターなど、進行状況バーまたはスピン ボタンとも組み合わせることができます。 情報バーは細かいレベルの進行状況または確定した進行状況を示す値を提供しません。 参照してください[情報の表示](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)します。  
  
 ![進行状況バーとメッセージング付きの情報バー](~/extensibility/ux-guidelines/media/0903-05_infobar.png "0903&05;_InfoBar")  
  
 **進行状況バーと説明テキストを含むページ**  
  
 ![ウィンドウ内の情報バー](~/extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903&06;_InfoBarInWindow")  
  
 **コード分析 ウィンドウ内の情報バー**  
  
##### <a name="inline"></a>インライン  
 ローダーの種類の進行状況のいずれかでは、インラインの進行状況を示す値を表現できます。 進行状況インジケーターは、メッセージングと組み合わせて使用通常が、これは必須ではありません。  
  
 ![インラインの進行状況スピナー](~/extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903&07;_InlineSpinner")  
  
 **スピン ボタンの説明テキストと組み合わせる**  
  
 ![インラインの積み上げ進行状況バー](~/extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903&08;_InlineStackedProgress")  
  
 **確定した積み上げ進行状況バー**  
  
 ![インラインの進行状況メッセージング](~/extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903&09;_InlineText")  
  
 **サーバー エクスプ ローラーのインライン テキスト: を更新する.**  
  
##### <a name="tool-windows"></a>ツール ウィンドウ  
 グローバルで進行状況を示す値は、ツールバーのすぐ下に配置されている不確定な進行状況バーで表されます。  
  
 ![グローバルで不確定な進行状況バー](~/extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903&23;_GlobalIndeterminate")  
  
 **チーム エクスプ ローラーのグローバルで不確定な進行状況バー**  
  
##### <a name="dialogs"></a>ダイアログ  
 ダイアログ ボックスには、進行状況ローダー型のいずれかを含めることができます。 進行状況インジケーターでくメッセージングとペアになってだけでなく表すを細分化されたおよびサブ プロセスに進行状況を示す値の複数のレベルと組み合わせます。  
  
 ![複数の種類の進行状況インジケーターを含むダイアログ](~/extensibility/ux-guidelines/media/0903-11_dialog.png "0903&11;_Dialog")  
  
 **同時実行プロセスと、複数の種類の進行状況インジケーターの visual Studio ダイアログ**  
  
 ![進行状況ローダーとメッセージング付きのダイアログ](~/extensibility/ux-guidelines/media/0903-12_dialog2.png "0903&12;_Dialog2")  
  
 **進行状況ローダーとメッセージング インライン コマンドの実行を含む visual Studio のダイアログ**  
  
##### <a name="document-well"></a>適切に文書化します。  
 でも、ドキュメントは、コントロールと組み合わせて複数の種類の進行状況ローダーを表示できます。  
  
 ![進行状況もドキュメントのメッセージング](~/extensibility/ux-guidelines/media/0903-13_documentwell.png "0903&13;_DocumentWell")  
  
 **ツールバーの下の不確定な進行状況バー**  
  
##### <a name="output-window"></a>[出力] ウィンドウ  
 [出力] ウィンドウでは、プロセスの進行とインライン テキスト メッセージングを使用して継続的な処理の進行状況の処理に適しています。 出力ウィンドウの進行状況レポートとステータス バーを使用する必要があります。  
  
 ![[出力] ウィンドウでのメッセージングの進行状況](~/extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903&14;_OutputWindow")  
  
 **継続的なプロセスの状態と出力ウィンドウとメッセージを待機**  
  
##  <a name="a-namebkmkinfobarsa-infobars"></a><a name="BKMK_Infobars"></a>情報の表示  
  
### <a name="overview"></a>概要  
 情報の表示が注目を集めるのポイントに近いインジケーターをユーザーに付与し、視覚的な外観と操作の一貫性を確保する、共有の情報バー コントロールを使用します。  
  
 ![情報バー](~/extensibility/ux-guidelines/media/0904-01_infobar.png "0904&01;_Infobar")  
  
 **Visual Studio で情報の表示**  
  
#### <a name="appropriate-uses-for-an-infobar"></a>情報バーの適切な使用方法  
  
-   現在のコンテキストに関連する非ブロッキングが、重要なメッセージをユーザーに提供するには  
  
-   デバッグ履歴など、いくつかの操作の影響を実行する UI が特定の状態または条件であることを示します  
  
-   拡張機能がパフォーマンスの問題を引き起こしている場合などの問題が検出されたことをユーザーに通知するには  
  
-   エディターのタブと空白のファイルが混在ことが検出された場合など、アクションを簡単に実行する方法をユーザーに付与するには  
  
##### <a name="do"></a>操作を行います。  
  
-   短いと、ポイントには、情報バーのメッセージ テキストを保持します。  
  
-   リンクやボタンのテキストを簡潔にしてください。  
  
-   ユーザーに提供する、"action"オプションを最小限に抑える、必要な操作のみを示すことを確認します。  
  
##### <a name="dont"></a>できません：  
  
-   情報バーを使用すると、ツールバーに配置する標準のコマンドを提供できます。  
  
-   モーダル ダイアログ ボックスの代わりに、情報バーを使用します。  
  
-   ウィンドウの外部のフローティング状態メッセージを作成します。  
  
-   同じウィンドウ内のいくつかの場所で複数の情報の表示を使用します。  
  
#### <a name="can-multiple-infobars-show-at-the-same-time"></a>同時に複数情報の表示を表示できますか。  
 はい、同時に複数の情報の表示を表示できます。 上部と追加情報の表示を示す下に表示されている最初の情報バーに、早い者勝ちの順序で表示されます。  
  
 ユーザーは、一度に最大&3; つの情報の表示に表示される、多くの情報の表示がある場合、情報バーの領域になるスクロール可能な後です。  
  
### <a name="creating-an-infobar"></a>情報バーを作成します。  
 情報バーには、左から右への&4; つのセクションがあります。  
  
-   **アイコン:**これは、任意のアイコンを追加する場所の警告アイコンなどの情報バーを表示したいです。  
  
-   **テキスト:**シナリオ/状況ユーザーを説明するテキストには、テキスト内のリンクと共には追加できますが必要な場合です。 簡潔なテキストを保持してください。  
  
-   **アクション:**このセクションでは、リンクや、情報バーで、ユーザーが実行できる操作のボタンを含める必要があります。  
  
-   **[閉じる] ボタン:**右側には、最後のセクションが [閉じる] ボタンを持つことができます。  
  
#### <a name="creating-a-standard-infobar-in-managed-code"></a>マネージ コードで標準的な情報バーを作成します。  
 InfoBarModel クラスは、情報バーのデータ ソースを作成するためにことができます。 これら&4; つのコンス トラクターのいずれかを使用します。  
  
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
  
 次に、ハイパーリンク、動作設定ボタン、アイコンとテキストが、InfoBarModel を作成する例を示します。  
  
 ![ハイパーリンクを含むページ](~/extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904&02;_InfobarHyperlink")  
  
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
 ネイティブ コードからの情報バーを提供するためには、「IVsInfoBar インターフェイスを実装します。  
  
```  
public interface IVsInfoBar  
{  
    IVsInfoBarActionItemCollection ActionItems { get; }  
    ImageMoniker Image { get; }  
    bool IsCloseButtonVisible { get; }  
    IVsInfoBarTextSpanCollection TextSpans { get; }  
}  
  
```  
  
#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>情報バーからの情報バー UIElement の取得  
 InfoBarModel または IVsInfoBar の実装とは、UI に表示するのには、UIElement に変換する必要がありますデータ モデルです。 UIElement は、SVsInfoBarUIFactory/IVsInfoBarUIFactory サービスで取得できます。  
  
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
 次の場所の&1; つ以上の情報の表示を表示できます。  
  
-   ツール ウィンドウ  
  
-   ドキュメント タブ内  
  
> [!IMPORTANT]
>  グローバル コンテキストについてのメッセージにある情報バーを配置することができます。 これは、ツールバーとものドキュメントの間が表示されます。 これは使用しないで「ジャンプし、動かさない」の問題が発生するため、IDE をお勧めしない限り、絶対に必要かつ適切なです。  
  
#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane に、情報バーを配置します。  
 ツール ウィンドウに、情報バーを追加する ToolWindowPane.AddInfoBar(IVsInfoBar) メソッドを使用できます。 この API は、(どの InfoBarModel は、既定の実装) IVsInfoBar を追加できますか、または、IVsUIElement です。  
  
#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>ドキュメントまたは ToolWindowPane 以外に、情報バーを配置します。  
 任意の IVsWindowFrame に、情報バーを配置するには、VSFPROPID_InfoBarHost プロパティを使って、フレームの IVsInfoBarHost を取得し、UIElement の情報バーを追加します。  
  
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
 メイン ウィンドウで、情報バーを配置するには、IVsShell サービスの VSSPROPID_MainWindowInfoBarHost を使用して、メイン ウィンドウの IVsInfoBarHost を取得し、UIElement 情報バーを追加します。  
  
### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>ユーザーが、自分の情報バーの操作をすれば、わかりますか。  
 はい、すべてのイベントのアクションを情報バーの作成者は返します。 アクションを実行するバーに表示されるユーザーの選択に基づく IDE 情報バーの作成者の責任です。 [閉じる] ボタンがクリックすると、ホストから情報の表示は自動的に削除されますが、後に削除するには、その他の情報の表示必要を閉じる場合は、追加の作業が必要です。 テレメトリを各情報バーによって個別に記録する必要があります。  
  
#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane 情報バーのイベントの受信  
 ToolWindowPane には、情報の表示の&2; つのイベントがあります。 ToolWindowPane の情報バーを閉じたときに、InfoBarClosed イベントが発生します。 ハイパーリンクまたはボタン バーの内側がクリックされたときに、InfoBarActionItemClicked イベントが発生します。  
  
#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>UIElement から直接情報バーのイベントの受信  
 情報バーの UIElement から直接イベントをサブスクライブする IVsInfoBarUIElement.Advise を使用できます。 IVsInfoBarUIEvents を実装すると、閉じる受信し、クリックしてイベントの作成者が許可されます。  
  
```  
public interface IVsInfoBarUIEvents  
{  
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);  
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);  
}  
  
```  
  
##  <a name="a-namebkmkerrorvalidationa-error-validation"></a><a name="BKMK_ErrorValidation"></a>エラーの検証  
 必須のフィールドをスキップする場合など、または不適切な形式でデータを入力するときに使用可能な情報が入力されたときを使用するコントロールの検証またはブロックしているポップアップ エラー ダイアログ ボックスを使用する代わりに、コントロールの近くのフィードバックことをお勧めします。  
  
### <a name="field-validation"></a>フィールドの検証  
 フォームとフィールドの検証は、3 つのコンポーネントで構成されています: コントロール、アイコン、およびツールヒント。 いくつかの種類のコントロールは、これを使用すること、テキスト ボックスを例として使用されます。  
  
 ![検証 (空白) をフィールド](~/extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905&01;_FieldValidation")  
  
 フィールドが必要な場合があります透かしテキストを示す**\<必要 >**フィールド背景は、光と黄色 (VSColor: `Environment.ControlEditRequiredBackground`) し、フォア グラウンドがグレー表示にする必要があります (VSColor: `Environment.ControlEditRequiredHintText`)。  
  
 ![「必須」のラベルを持つ検証をフィールド](~/extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905&02;_FieldValidationRequired")  
  
 プログラムでは、コントロールのフォントがの状態を判断する*に入力された無効なコンテンツ*[別のコントロールにフォーカスを移動するときまたはユーザーが [OK] のコミット] ボタンのクリックした場合またはユーザーが文書またはフォームを保存するとします。  
  
 無効なコンテンツの状態が確認された場合、コントロールの内側、またはその横にアイコンが表示されます。 アイコンまたはコントロールのいずれかのホバー時のエラーを説明するツールヒントが表示されます。 さらに、無効な状態を作成しているコントロールの周囲に 1 ピクセルの境界線を表示します。  
  
 ![検証のレイアウトの仕様をフィールド](~/extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905&03;_LayoutSpecs")  
  
 **フィールドの検証のレイアウトの仕様**  
  
#### <a name="acceptable-variations-for-icon-location"></a>アイコンの場所で使用可能なバリエーション  
 検証エラーを把握できるようにユーザーが必要な数多くの一意なケースもあります。 コントロールの種類と、UI の構成では、考慮すると、状況に合わせて適切なアイコンの配置を選択します。  
  
 ![アイコンの場所の場所の適切な](~/extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905&04;_IconLocation")  
  
 **許容可能なバリエーションのフィールドの検証 アイコンの場所**  
  
#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>サーバーまたはネットワーク接続へのラウンド トリップを必要とする検証  
 場合によっては、サーバーへのラウンド トリップは、コンテンツを検証するために必要なし、を検証、ユーザーの進行状況とエラーの状態を表示することがあります。 次の図には、このケース テーブルと推奨される UI の例を示します。  
  
 ![サーバーへのラウンド トリップに関連する検証](~/extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905&05;_RoundTrip")  
  
 **サーバーへのラウンド トリップに関連する検証**  
  
 「確認…」を実現するために、コントロールの右側に十分な空き容量を指定する必要がありますに注意してください。 テキストを「再試行」してください。  
  
#### <a name="in-place-warning-text"></a>インプレース警告テキスト  
 エラーの状態で、コントロールの近くに、エラー メッセージを配置に使用できる空きスペースがある場合は、これは、単独でツールヒントを使用することをお勧めです。  
  
 ![インプレース警告](~/extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905&06;_InPlaceWarning")  
  
 **インプレース警告テキスト**  
  
#### <a name="watermarks"></a>透かし  
 あります、コントロール全体またはウィンドウがエラー状態です。 このような状況では、エラーを示すウォーターマークを使用します。  
  
 ![透かし](~/extensibility/ux-guidelines/media/0905-07_watermark.png "0905&07;_Watermark")  
  
 **透かしのフィールドの検証**
