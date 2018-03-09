---
title: "Visual Studio で遅延診断拡張機能 UI |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: PooyaZv
ms.author: pozandev
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dffc67e550cb57f9f089e180ff399f27c817d253
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>方法: 診断 UI 拡張機能による遅延のため

UI が応答しない状態になると、Visual Studio は、リーフで始まると、ベースに向かって、UI スレッドの呼び出し履歴を調べます。 Visual Studio がインストールされ有効な拡張機能の一部であるモジュールをコール スタック フレームが属していると判断した場合、通知が表示されます。

![UI の遅延 (応答がない) の通知](media/ui-delay-notification-in-vs.png)

通知は、こと (つまり、応答がない、ui) の UI の遅延された可能性があります、拡張機能からのコードの結果をユーザーに通知します。 また、拡張機能またはその拡張子の今後の通知を無効にするオプションで、ユーザーも提供します。

このドキュメントでは、拡張機能のコードでの原因は UI の遅延の通知を診断する方法について説明します。 

> [!NOTE]
> UI の遅延の診断には、Visual Studio の実験用インスタンスを使わないでください。 つまり、UI の遅延の通知が表示されませんが、実験用インスタンスを使用する場合、UI の遅延の通知に必要な呼び出し履歴の分析の一部がオフになります。

診断のプロセスの概要は次のとおりです。
1. トリガーのシナリオを識別します。
2. アクティビティのログ記録を VS を再起動します。
3. ETW トレースを開始します。
4. 再度表示通知をトリガーします。
5. ETW トレースを停止します。
6. 遅延の ID を取得するアクティビティのログを確認します。
7. 手順 6 で遅延の ID を使用して、ETW トレースを分析します。

次のセクションで取り上げますこれらの手順の詳細。

## <a name="identifying-the-trigger-scenario"></a>トリガーのシナリオを識別します。

UI の遅延を診断するためは、まず、どのような (アクションのシーケンス) が原因で、通知を表示する Visual Studio を識別する必要があります。 これは、ログ記録をオンになっていると通知を後で実行することにあります。

## <a name="restarting-vs-with-activity-logging-on"></a>アクティビティのログ記録で VS を再起動します。

Visual Studio は、「アクティビティ ログ」を生成できます問題をデバッグするときに役立つ情報を提供します。 アクティビティの Visual Studio でのログ記録をオンにするで Visual Studio を起動、`/log`コマンド ライン オプションです。 Visual Studio を起動した後、動作状況ログは次の場所に格納されます。

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

インスタンス ID で、VS を検索する方法の詳細については、次を参照してください。[を検出すると、Visual Studio のインスタンスを管理するためのツール](../install/tools-for-managing-visual-studio-instances.md)です。 UI の遅延と関連する通知の詳細について調べるには後でこのアクティビティのログを使用します。

## <a name="starting-etw-tracing"></a>ETW トレースの開始

使用することができます[PerfView](https://github.com/Microsoft/perfview/) ETW トレースを収集します。 PerfView は、ETW トレースを収集するためと、それを分析するための使いやすいインターフェイスを提供します。 トレースを収集するのにには、次のコマンドを使用します。

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

これにより、UI の遅延の通知に関連するイベントの Visual Studio を使用して、プロバイダーは、"Microsoft VisualStudio"プロバイダー。 また、PerfView を使用して「にスタックのスレッド」ビューを生成するカーネル プロバイダーのキーワードを指定します。

## <a name="triggering-the-notification-to-appear-again"></a>再度表示通知をトリガーします。

PerfView トレースの収集が開始に再度表示される、トリガー操作 (手順 1) の通知のシーケンスを使用できます。 通知が表示されると、PerfView を処理し、出力トレース ファイルを生成するためのトレースの収集を停止できます。

## <a name="stopping-etw-tracing"></a>ETW トレースを停止しています

トレースの収集を停止するだけで使用して、 `Stop collection` PerfView ウィンドウのボタンをクリックします。 トレースの収集を停止した後、PerfView は ETW イベントを自動的に処理し、出力トレース ファイルを生成します。

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>遅延の ID を取得するアクティビティのログを確認します。

前述のようでのアクティビティ ログを見つけることができます`%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`です。 ノードで利用状況ログに書き込む Visual Studio が拡張機能 UI の遅延を検出するたびに`UIDelayNotifications`ソースとして。 このノードには、4 つ UI の遅延についての情報にはが含まれています。

- UI の遅延の ID、VS のセッションで、UI の遅延を一意に識別する連続番号
- セッション ID は、開始から終了まで、Visual Studio セッションを一意に識別します。
- UI の遅延の通知が表示されたかどうか
- UI の遅延の原因は拡張機能

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> 通知にすべての UI の遅延が発生します。 したがっては常に確認する、「通知に表示しますか?」 右側の UI の遅延を正しく識別する値。

アクティビティ ログで、正しい UI の遅延を見つけたら、ノードに指定された UI の遅延の ID を書き留めます。 次の手順で対応する ETW イベントを検索するには、ID を使用します。

## <a name="analyzing-the-etw-trace"></a>ETW トレースを分析します。

次に、トレース ファイルを開きます。 これを行う PerfView のまたは新しいインスタンスを起動して、上、左のウィンドウのトレース ファイルの場所を現在のフォルダー パスを設定して、同じインスタンスを使用します。

![Perfview でフォルダー パスを設定します。](media/perfview-set-path.png)

次に、左側のウィンドウで、トレース ファイルを選択し、右クリックまたはコンテキスト メニューから開くを選択して開きます。

> [!NOTE]
> 既定では、PerfView は、Zip アーカイブを出力します。 Trace.zip を開くときに自動的にアーカイブの圧縮を解除し、トレースが表示されます。 トレースの収集中に"Zip"ボックスをオフにして、これを省略できます。 ただしを転送し、別のコンピューター間でのトレースの使用を計画している場合は強くお勧め"Zip"ボックスをオフにするとします。 このオプションを指定せず Ngen アセンブリに必要な Pdb は、トレースを伴うされませんし、移行先コンピューターでしたがってする Ngen アセンブリからのシンボルが解決しません。 (を参照してください[このブログの投稿](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/)Ngen アセンブリについての Pdb です)。 

PerfView を処理し、トレースを開くには数分かかることができます。 トレースが表示されたら、その下にあるさまざまな「ビュー」の一覧が表示されます。

![PerfView トレースの概要ビュー](media/perfview-summary-view-events-selected.png)

おはまず、「イベント」ビューを使用して UI の遅延の時間範囲を取得します。

1. トレースの下の「イベント」ノードを選択すると、右クリックまたはコンテキスト メニューから開く を選択して、「イベント」ビューを開きます。
2. 選択"`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`"左側のウィンドウでします。
3. Enter キーを押します

選択範囲が適用されるとすべて`ExtensionUIUnresponsiveness`右側のウィンドウでイベントが表示されます。

![イベント ビューでイベントを選択します。](media/perfview-event-selection.png)

右側のウィンドウ内の各行は、UI の遅延に対応します。 イベントには、手順 6 でのアクティビティ ログで遅延 ID に一致する必要があります"遅延 ID"の値が含まれています。 `ExtensionUIUnresponsiveness`が発生した UI の遅延イベントのタイムスタンプの末尾 (約) 記号 UI の遅延の終了時刻。 イベントには、遅延の期間も含まれています。 UI の遅延が開始されたときのタイムスタンプを取得する終了タイムスタンプから期間を引くことができます。

![UI の遅延の時間範囲を計算します。](media/ui-delay-time-range.png)

たとえば、前のスクリーン ショット イベントのタイムスタンプが 12,125.679 と遅延期間は 6,143.085 (ミリ秒)。 したがって
* 開始を遅らせるは 12,125.679 6,143.085 5,982.594 を = です。
* UI の遅延時間の範囲は、5,982.594 に 12,125.679 です。

時間範囲を作成したらはイベント ビューから終了して、「スレッド (StartStop アクティビティ) の時間履歴」ビューを開きます。 このビューは、UI スレッドをブロックしている拡張子多くの場合、単なるを待機している他のスレッドまたは O バインド操作のために特に便利です。 したがってはほとんどの場合に移動するオプションで、「CPU スタック」ビューでは、スレッドは、この期間中に CPU が使用されていないブロックが費やす時間がキャプチャされません可能性があります。 「スレッド時刻のスタックは、」は、正しく表示がブロックされている時間によってこの問題を解決します。

![PerfView の概要 ビュー内のスレッド (StartStop アクティビティ) の時間履歴ノード](media/perfview-thread-time-with-startstop-activities-stacks.png)

「にスタックのスレッド」を開くときに表示し、分析を開始する"devenv"プロセスを選択してください。

![スレッドの UI の遅延の分析のための時間履歴ビュー](media/ui-delay-thread-time-stacks.png)

ページの左上で「にスタックのスレッド」ビューにスタックは、その時間の範囲に調整するために、Enter キーを押して、前の手順でおが計算された値を時間範囲を設定できます。

> [!NOTE]
> スレッドが UI を確認する (スタートアップ) スレッドは直感に反する Visual Studio が既に開いている後に、トレースの収集を開始できます。 ただし、UI (スタートアップ) スレッドのスタック上の最初の要素は最も可能性の高い常にオペレーティング システム Dll (ntdll.dll および kernel32.dll) devenv 続く.!? msenv.!? です。 このシーケンスは、UI スレッドを見つけるのに役立ちます。

 ![スタートアップ スレッドを識別します。](media/ui-delay-startup-thread.png)

このビューはのみ、パッケージからのモジュールが含まれているスタックを含めることによってさらにフィルターできます。

* 既定では追加、グループ化を削除する空のテキストに"GroupPats"を設定します。
* セットに既存のプロセスのフィルターだけでなく、アセンブリ名の一部を含めるには、"IncPats"です。 この場合、"devenv; である必要があります。UIDelayR2"です。

![時刻のスタックのスレッド ビューで GroupPath および IncPath 設定](media/perfview-tts-group-path-inc-path.png)

PerfView は [ヘルプ] メニューで、コードでパフォーマンスのボトルネックを特定する際のガイダンスを詳しく説明します。 さらに、次のリンクでは、Visual Studio のスレッド処理、コードを最適化するために Api を利用する方法の詳細についてを提供します。

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

> [!NOTE]
> 経由で制御する必要は依存関係によりを通常どおりに対応していない場合 (例: 拡張機能は、UI スレッドで同期の VS サービスを呼び出す必要かどうか)、それについて認識しております。 場合は、Visual Studio パートナー プログラムのメンバーでは、弊社までご連絡開発者サポート リクエストを送信しています。 それ以外の場合、ツールを使用して、問題を報告する に、フィードバックを送信し、含める`"Extension UI Delay Notifications"`タイトルにします。 また、分析の詳細な説明を含めてください。
