---
title: Visual Studio で診断拡張機能 UI が遅延 |Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: douge
ms.workload: multiple
ms.openlocfilehash: 1bf5dba23622c5dc3d964bdac19fec210aa60b1e
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639196"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>方法: UI の診断拡張機能によって遅延が発生

UI が応答しなくなった、リーフからベースの方向に、Visual Studio は、UI スレッドのコール スタックを調査します。 Visual Studio では、コール スタック フレームがインストールされ有効になっている拡張機能の一部であるモジュールに属していることを判断した場合、通知が表示されます。

![UI の遅延 (無応答) 通知](media/ui-delay-notification-in-vs.png)

通知は、拡張機能からのコードの結果があります (つまり、UI の無応答) UI の遅延にされていることをユーザーに通知します。 ユーザーは、拡張機能またはその拡張機能の今後の通知を無効にするオプションも提供します。

このドキュメントでは、UI の遅延通知の原因は拡張機能のコードで何を診断する方法について説明します。 

> [!NOTE]
> UI の遅延を診断する Visual Studio の実験用インスタンスを使わないでください。 つまり、UI の遅延通知が表示されませんが、実験用インスタンスを使用する場合、UI の遅延通知に必要な呼び出し履歴の分析の一部が無効になります。

診断のプロセスの概要は次のとおりです。
1. トリガーのシナリオを特定します。
2. アクティビティのログ記録で VS を再起動します。
3. ETW トレースを開始します。
4. もう一度表示される通知をトリガーします。
5. ETW トレースを停止します。
6. 遅延の ID を取得するアクティビティ ログを調べます
7. 手順 6 からの遅延の ID を使用して、ETW トレースを分析します。

次のセクションでが、これらの手順の詳細について経由します。

## <a name="identify-the-trigger-scenario"></a>トリガーのシナリオを特定します。

UI の遅延を診断するには、まず、どのような (アクションのシーケンス) が原因で、通知を表示する Visual Studio を識別するために必要があります。 これは、ログを有効にして、後で、通知をトリガーするための順序で。

## <a name="restart-vs-with-activity-logging-on"></a>アクティビティのログ記録を VS を再起動します。

Visual Studio は、「アクティビティ ログ」を生成できます問題をデバッグするときに役立つ情報を提供します。 アクティビティの Visual Studio でログ記録をオンにする Visual Studio で使用を開始、`/log`コマンド ライン オプション。 Visual Studio の起動後、アクティビティ ログは、次の場所に格納されます。

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

インスタンス ID で、VS を検索する方法の詳細については、次を参照してください。[を検出すると、Visual Studio インスタンスを管理するためのツール](../install/tools-for-managing-visual-studio-instances.md)します。 このアクティビティ ログは、UI の遅延と関連する通知の詳細を確認する後で使用されます。

## <a name="starting-etw-tracing"></a>ETW トレースの開始

使用することができます[PerfView](https://github.com/Microsoft/perfview/) ETW トレースを収集します。 PerfView は ETW トレースを収集するためと、それを分析するために、使いやすいインターフェイスを提供します。 トレースを収集するのにには、次のコマンドを使用します。

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

これにより、Visual Studio を使用して、UI の遅延通知に関連するイベント プロバイダーである"Microsoft VisualStudio"プロバイダーができます。 PerfView は、生成に使用できるカーネル プロバイダーのキーワードもを指定します、**スレッド時間スタック**ビュー。

## <a name="trigger-the-notification-to-appear-again"></a>もう一度表示される通知をトリガーします。

PerfView トレースの収集が開始されたら、再び表示されるように (手順 1) からの通知のトリガー アクションのシーケンスを使用できます。 通知が表示されると、処理し、出力トレース ファイルを生成する PerfView のトレースの収集を停止できます。

## <a name="stop-etw-tracing"></a>ETW トレースを停止します。

トレースの収集を停止するには、使用、**コレクションの停止**PerfView ウィンドウのボタン。 トレースの収集を停止した後、PerfView は ETW イベントが自動的に処理し、トレースの出力ファイルを生成します。

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>遅延の ID を取得するアクティビティ ログを調べます

前述のように、アクティビティ ログには見つかります *%APPDATA%\Microsoft\VisualStudio\<vs_instance_id > \ActivityLog.xml*します。 アクティビティ ログ ファイルにノードを書き込みますが Visual Studio は、UI の遅延の拡張機能が検出されるたびに`UIDelayNotifications`ソースとして。 このノードには、4 つ UI の遅延についての情報にはが含まれています。

- UI の遅延の ID、VS のセッションで、UI の遅延を一意に識別する連続番号
- 開始から閉じるまで、Visual Studio セッションを一意に識別するセッション ID
- UI の遅延の通知が表示されたかどうか
- おそらく UI の遅延の原因となった拡張機能

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
> 通知をすべての UI の遅延が発生します。 そのため、必ずチェック、**通知が表示されるでしょうか。** 適切な UI の遅延を正しく識別する値。

アクティビティ ログで、適切な UI の遅延を見つけたら、ノードで指定された UI の遅延の ID を書き留めます。 次の手順で、対応する ETW イベントを探すには、ID を使用します。

## <a name="analyze-the-etw-trace"></a>ETW トレースを分析します。

次に、トレース ファイルを開きます。 PerfView のまたは新しいインスタンスを起動して、左ウィンドウのトレース ファイルの場所で、現在のフォルダー パスを設定して、同じインスタンスを使用してこれが実行できます。

![Perfview で、フォルダーのパスを設定します。](media/perfview-set-path.png)

次に、左側のウィンドウで、トレース ファイルを選択しを選択して開きます**開く**右クリックまたはコンテキスト メニューから。

> [!NOTE]
> 既定では、PerfView は、Zip アーカイブを出力します。 開く*trace.zip*、自動的にアーカイブの圧縮を解除し、トレースが表示されます。 これをスキップするにはオフにすると、 **Zip**トレースの収集中にボックス。 ただし、転送し、別のコンピューター間でのトレースの使用を計画している場合強くお勧めしますをオフにすると、 **Zip**ボックス。 このオプションを指定せず、必要なアセンブリの Ngen Pdb がトレースに付属し、移行先コンピューターはそのためする Ngen アセンブリからのシンボルが解決しません。 (を参照してください[このブログの投稿](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/)アセンブリの Ngen Pdb の詳細についてはします)。 

PerfView を処理し、トレースを開くには数分かかることができます。 トレースが開いたら、その下にあるさまざまな「ビュー」の一覧が表示されます。

![PerfView トレースの概要ビュー](media/perfview-summary-view-events-selected.png)

使用して、**イベント**UI の遅延の時間範囲を取得するビュー。

1. 開く、**イベント**ビューを選択して`Events`、トレースの下のノードを選択して**オープン**右クリックまたはコンテキスト メニューから。
2. 選択"`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`"左側のウィンドウでします。
3. Enter キーを押します

選択範囲を適用し、すべて`ExtensionUIUnresponsiveness`右側のウィンドウでイベントが表示されます。

![イベント ビューでイベントを選択します。](media/perfview-event-selection.png)

右側のウィンドウ内の各行は、UI の遅延に対応します。 イベントには、手順 6 からのアクティビティ ログに遅延 ID に一致する必要があります"遅延 ID"値が含まれています。 `ExtensionUIUnresponsiveness`が発生したイベントのタイムスタンプ、UI の遅延の最後に (ほぼ) マーク UI の遅延の終了時刻。 イベントには、遅延の期間も含まれています。 UI の遅延の開始時のタイムスタンプを取得する終了のタイムスタンプから期間を引くことができます。

![UI の遅延の時間範囲を計算します。](media/ui-delay-time-range.png)

たとえば、前のスクリーン ショットでは、イベントのタイムスタンプが 12,125.679 と遅延期間が 6,143.085 (ミリ秒)。 したがって
* 開始を遅らせるは 12,125.679 6,143.085 5,982.594 を = です。
* UI の遅延時間の範囲は、5,982.594 に 12,125.679 です。

うち、時間の範囲取得したら、閉じてもかまいません、**イベント**表示し、開く、**スレッドの時間 (StartStop アクティビティ) をスタック**ビュー。 このビューは、多くの場合、UI スレッドをブロックしている拡張子は、他のスレッド上で、I/O バインド操作だけで待機しているため、特に便利です。 つまり、 **CPU スタック**ビューで、ほとんどの場合、移動するオプションがある可能性があります、スレッドがブロック期間中に、CPU を使用しないために要する時間をキャプチャしません。 **スレッド時間スタック**正しくブロックが表示された時間でこの問題を解決します。

![PerfView の概要ビューでスレッドの時間 (StartStop アクティビティ) をスタック ノード](media/perfview-thread-time-with-startstop-activities-stacks.png)

開いているときに**スレッド時間スタック**ビューで、選択、 **devenv**分析を開始するプロセス。

![スレッドの UI の遅延の分析のための時間の履歴ビュー](media/ui-delay-thread-time-stacks.png)

**スレッド時間スタック**ビューで、ページの一番上、左で設定できる時間の範囲の計算値を前の手順とキーを押して **」と入力**のため、スタックは、その時間の範囲に合わせて調整されます。

> [!NOTE]
> どのスレッドが UI を確認する (スタートアップ) スレッドは直感に反する後、Visual Studio が既に開いているトレースの収集が開始できます。 ただし、(起動) を UI スレッドのスタックには、最初の要素は最も可能性が常にオペレーティング システムの Dll (*ntdll.dll*と*kernel32.dll*) 続けて`devenv!?`し`msenv!?`. このシーケンスは、UI スレッドを特定できます。

 ![スタートアップのスレッドを識別します。](media/ui-delay-startup-thread.png)

このビューはのみ、パッケージのモジュールが含まれているスタックを含めることによってもさらにフィルターできます。

* 設定**GroupPats**を空のテキストを既定で追加されたすべてのグループ化を削除します。
* 設定**IncPats**を既存のプロセス フィルターだけでなく、アセンブリ名の一部を含めます。 この場合、必要がある**devenv;UIDelayR2**します。

![GroupPath と IncPath 時間スタックのスレッド ビューで設定](media/perfview-tts-group-path-inc-path.png)

PerfView でのガイダンスの詳細は、**ヘルプ** メニューのコードでパフォーマンスのボトルネックを識別するために使用することができます。 さらに、次のリンクは、スレッド処理 Api、コードを最適化するために Visual Studio を利用する方法の詳細についてを提供します。

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

拡張機能の新しい Visual Studio の静的アナライザーを使用することもできます (NuGet パッケージ[ここ](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers))、効率的な拡張機能を記述するためのベスト プラクティスに関するガイダンスを提供します。 一覧を参照してください。 [VS SDK アナライザー](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md)と[アナライザーをスレッド](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md)します。

> [!NOTE]
> 依存関係が無応答に対処されない場合がないコントロール経由で (たとえば、拡張機能は、UI スレッドで同期の VS サービスを呼び出すに) 場合、それについて認識したいです。 Visual Studio パートナー プログラムのメンバーの場合は、developer サポートの要求を送信で依頼することができます。 それ以外の場合、問題の報告ツールを使用して、フィードバックを送信し、含める`"Extension UI Delay Notifications"`タイトルにします。 また、分析の詳細な説明を含めてください。
