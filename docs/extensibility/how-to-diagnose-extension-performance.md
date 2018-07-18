---
title: '方法: 拡張機能のパフォーマンスの診断 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/08/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: 60a7d1c3178d0fd74983d3f1096d01e578a49a00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133272"
---
# <a name="measuring-extension-impact-in-startup"></a>スタートアップの拡張機能への影響を測定

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>拡張機能のパフォーマンスを Visual Studio 2017 にフォーカスします。

お客様のフィードバックに基づいて、Visual Studio 2017 リリースの対象領域のいずれかのされましたスタートアップとソリューションの読み込みのパフォーマンス。 一方、Visual Studio プラットフォーム チームは、扱っています通常スタートアップとソリューションの読み込みのパフォーマンスを向上させることに、当社製品利用統計情報は、インストールされた拡張機能は、そのようなシナリオに大きな影響を与えるをこともできますを提案します。

ユーザーがこの影響を理解するために、低速の拡張機能のユーザーに通知する Visual Studio での新機能を追加します。 Visual Studio では、ソリューションの読み込みまたは起動時のパフォーマンスの低下は、新しい拡張機能を検出すると、ユーザーは、新しい「Visual Studio のパフォーマンスの管理」ダイアログをポイントして、IDE で通知が表示されます。 このダイアログ ボックスは、以前に検出された拡張機能を参照する [ヘルプ] メニューからも常にアクセスできます。

![Visual Studio のパフォーマンスを管理します。](media/manage-performance.png)

このドキュメントでは、開発者に役立つ拡張機能で拡張機能への影響を計算する方法およびどのように分析できますローカルで拡張機能がパフォーマンスに影響する拡張機能として表示される場合にテストを記述する目的としています。

> [!NOTE]
> このドキュメントは、スタートアップおよびソリューションの読み込み時に拡張機能の影響について説明します。 拡張機能が応答しなくなる UI が発生したときにも Visual Studio のパフォーマンスに影響します。 詳細については、次を参照してください。[する方法: 診断 UI による遅延のための拡張機能](how-to-diagnose-ui-delays-caused-by-extensions.md)します。

## <a name="how-extensions-can-impact-startup"></a>拡張機能がスタートアップに影響を与える

起動時のパフォーマンスに影響する拡張機能を最も一般的な方法の 1 つは、自動読み込み NoSolutionExists ShellInitialized など既知のスタートアップの UI コンテキストのいずれかを選択してです。 起動中にアクティブにならないような UI コンテキストとそれらのコンテキストにその定義に"ProvideAutoLoad"属性が含まれるすべてのパッケージが読み込まれ、その時点で初期化します。

拡張機能の影響を測定、ときに、主にについて説明上記のコンテキストでの自動読み込みを行う選択される、拡張機能で費やされた時間。 測定される時間がかかりますが含まれますに限定されません。

* 同期のパッケージの拡張機能アセンブリの読み込み
* 同期のパッケージのパッケージ クラスのコンス トラクターに費やされた時間
* 同期のパッケージのパッケージの初期化 (または SetSite) メソッドに費やされた時間
* 非同期のパッケージの上記の操作がバック グラウンド スレッド上で実行し、そのため、監視から除外されます。
* メイン スレッドで実行するパッケージの初期化中にスケジュールされた非同期作業に費やした時間
* 具体的には初期化シェル コンテキスト ライセンス認証またはシェル ゾンビ状態の変更のイベント ハンドラーに費やされた時間
* Visual Studio 2017 Update 3 以降もまずシェルが初期化される前に、アイドル状態の呼び出しで費やされた時間を監視します。 アイドル状態のハンドラーで長時間の操作も応答していない IDE とのユーザーによって認識される起動時に影響します。

自動読み込みを行うパッケージを必要と役立ちますが、ユーザーがある、確実に拡張機能を使用または読み込むときに、拡張機能の影響の削減に複数の特定のケースに負荷を延期する Visual Studio 2015 から複数の機能を追加しました自動的に。

これらの機能の詳細については、次のドキュメントでご覧ください。

[ルール ベースの UI コンテキスト](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): 構築されています。 UI コンテキスト高度な規則ベース エンジンを使用すると、プロジェクトの種類、フレーバー、および機能に基づいてカスタムのコンテキストを作成します。 これらのカスタム コンテキストはスタートアップ; の代わりに特定の機能を持つプロジェクトが存在するなどの具体的なシナリオ中に、パッケージの読み込みに使用できます。許可または[コマンドの可視性は、カスタムのコンテキストに関係を](visibilityconstraints-element.md)コマンドの状態のクエリのハンドラーを登録するには、プロジェクトの機能またはパッケージを読み込む必要があるので使用可能なその他の条項に基づいて。

[非同期のパッケージのサポート](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio 2015 で新しい AsyncPackage の基本クラスでは、読み込まれるバック グラウンドで非同期的にパッケージの読み込みが自動負荷属性または非同期サービス クエリによって要求された場合、Visual Studio パッケージを使用できます. このバック グラウンドで読み込まないは、拡張機能は、バック グラウンドで初期化され、スタートアップとソリューションの読み込みと同様に、重要なシナリオが影響を受けることはありません、応答性を維持するための IDE を使用できます。

[非同期サービス](how-to-provide-an-asynchronous-visual-studio-service.md): 非同期パッケージのサポートはもサポートが追加サービスを非同期で照会すると、非同期のサービスを登録できることです。 さらに重要な非同期クエリの処理の大部分がバック グラウンド スレッドで発生するように、非同期クエリをサポートするためにコア Visual Studio のサービスへの変換に取り組んでいます。 SComponentModel (Visual Studio MEF ホスト) は、今すぐ完全に非同期読み込みをサポートする拡張機能を許可する非同期クエリをサポートする主要なサービスの 1 つです。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>拡張機能を読み込むの自動への影響の削減

パッケージは、起動時に読み込まれた自動である必要がある場合、は、スタートアップに影響を与えず、拡張機能の可能性を低減するパッケージの初期化中に実行された作業を最小限に抑える必要があります。

高コストであるパッケージの初期化を引き起こす可能性のあるいくつかの例は次のとおりです。

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>非同期のパッケージの読み込みではなく同期パッケージの読み込みの使用

同期のパッケージが読み込まれるため、メイン スレッドで既定では、前述の代わりに、非同期のパッケージの基本クラスを使用して自動読み込まれたパッケージがある拡張機能の所有者お勧めします。 非同期読み込みをサポートするために自動の読み込まれたパッケージを変更もやすくなりますを以下に示すその他の問題を解決します。

### <a name="synchronous-filenetwork-io-requests"></a>同期ファイル/ネットワーク IO 要求

理想的には、同期したファイルまたはネットワークの IO 要求避ける必要があります、メイン スレッドで影響はマシンの状態に依存し、場合によっては長期間をブロックすることができます。

非同期のパッケージの読み込みと非同期 IO Api を使用して、パッケージの初期化はこのような場合、メイン スレッドをブロックしないことと、ユーザーは引き続きバック グラウンドでの I/O 要求が発生するときに、Visual Studio との対話を確認します。

### <a name="early-initialization-of-services-components"></a>サービス、コンポーネントの初期化

によって使用されるか、パッケージ コンス トラクターまたは初期化メソッドでは、そのパッケージによって提供されるサービスを初期化するためにパッケージの初期化で一般的なパターンの 1 つです。 これにより、サービスが使用できるように、中にそれらのサービスがすぐに使用されていない場合の読み込みをパッケージに不要なコストも追加できます。 代わりにパッケージの初期化で行われた作業を最小限に抑えるに要求時にこのようなサービスを初期化する必要があります。

グローバル サービスのパッケージによって提供される場合は遅延コンポーネントから要求される場合にのみサービスを初期化するために関数を受け取り AddService メソッドを使用できます。 パッケージ内で使用されるサービスでは、遅延を利用できます<T>または AsyncLazy<T> services が初回使用時に初期化/クエリを確認します。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>アクティビティ ログを使用して拡張機能を読み込むの自動への影響を測定

Visual Studio 2017 Update 3 以降では、Visual Studio のアクティビティ ログは今すぐエントリを含むパッケージのパフォーマンスが低下するスタートアップとソリューションの読み込み中に。 これらの測定値を確認するためにする必要がある/log スイッチで Visual Studio を起動し、ActivityLog.xml ファイルを開きます。

アクティビティ ログのエントリが「Visual Studio のパフォーマンスの管理」ソースの下になり、次のようになります。

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

これは、Visual Studio のスタートアップでの 2008 ms に費やされた"GUID"3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c でそのパッケージを意味します。 そのパッケージの拡張機能を無効にすると、savigs ユーザーが、パッケージの影響を計算するを参照してくださいときに、Visual Studio がプライマリの数と最上位レベルのコストを考慮することに注意してください。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView を使用して拡張機能を読み込むの自動への影響を測定

パッケージ初期化速度が低下するコード パスを識別するには、コード分析が役に立つは、Visual Studio のスタートアップでのパッケージの読み込みの影響を理解 PerfView のようなアプリケーションを使用してトレースを利用することもできます。

PerfView は、アプリケーション、CPU 使用率またはシステム コールをブロックするためのホット パスの理解を支援するシステム全体のトレース ツールです。 使用可能な PerfView を使用して拡張機能のサンプルを分析することに簡単な例を次に示します、 [Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/details.aspx?id=28567)です。

**コード例:**

この例は、サンプルに基づいて下のコードを表示するよう設計されていますがいくつかの一般的な遅延原因の場合します。

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**PerfView でトレースを記録します。**

インストールされている拡張機能と Visual Studio の環境を設定すると、PerfView、「収集」メニューから収集するダイアログを開きスタートアップのトレースを記録できます。

![perfview 収集メニュー](media/perfview-collect-menu.png)

既定のオプションでは、呼び出し履歴の CPU 消費量が、ここではブロッキング時間も後も有効にしてください「スレッド時間」スタック。 設定が準備完了「コレクションの開始」をクリックし、録画を開始するには、Visual Studio を起動できます。

コレクションを停止する前に、Visual Studio が完全に初期化されて、メイン ウィンドウが完全に表示されて、および拡張機能に自動的に表示する任意の UI 部分がある場合も表示されるかどうかを確認します。 Visual Studio が完全に読み込まれると、拡張機能が初期化されて、トレースを分析する記録を停止できます。

**PerfView でトレースを分析するには。**

記録が完了した後 PerfView は自動的にトレースを開いてオプション を展開します。

この例の目的で、主にでは見つけることができます「高度なグループ」の下にある「時間スタックのスレッド」ビュー。 このビューには、CPU 時間およびディスク IO またはハンドルを待機しているなどのブロック時間の両方を含むメソッドによって、スレッドで費やされた時間の合計が表示されます。

 ![スレッドの時間履歴](media/perfview-thread-time-stacks.png)

 「にスタックのスレッド」ビューを開くときに、分析を開始する"devenv"プロセスを選択してください。

PerfView はより詳細な分析のための独自のヘルプ] メニューの [時間履歴スレッドを読み取る方法に関するガイダンスを詳しく説明します。 この例の目的でのみ、パッケージのモジュール名とスタートアップ スレッドのスタックを含めることによってさらに、このビューをフィルター処理することができます。

1. 既定では追加、グループ化を削除する空のテキストに"GroupPats"を設定します。
2. セットに、アセンブリ名の一部を含めるには、"IncPats"とスレッドのスタートアップ プロセスの既存のフィルターだけでなくです。 この場合、"devenv; である必要があります。スタートアップ スレッドです。MakeVsSlowExtension"です。

これで、ビューは、拡張機能に関連するアセンブリに関連付けられているコストをのみ表示されます。 このビューでは、スタートアップ スレッドの"Inc"(包含的コスト) 列の下に表示される、時間は、フィルター選択された拡張機能に関連するし、スタートアップを受けています。

いくつか興味深い呼び出し上記の例のスタックになります。

1. System.IO クラスを使用する IO を: これらのフレームの包括的なコストをトレースに非常に不経済できない可能性がありますが問題の可能性がありますので、コンピューターからコンピューターにファイル IO の速度によって異なります。

  ![システムの io フレーム](media/perfview-system-io-frames.png)

2. その他の非同期作業を待機している呼び出しをブロック: ここでは包括時間は非同期作業の完了時に、メイン スレッドがブロックされる時間を表します。

  ![ブロッキング呼び出しフレーム](media/perfview-blocking-call-frames.png)

影響を判断する役に立つ、トレース内の他のビューのいずれかを「イメージ読み込みのスタックは、」となります。 「にスタックのスレッド」ビューに適用されると、同じフィルターを適用し、自動読み込まれたパッケージによって実行されるコードのために読み込まれるすべてのアセンブリを検索できます。

追加のアセンブリがかなり低速のマシンで スタートアップの速度が低下することができますが、追加のディスク I/O を必要に応じてパッケージの初期化ルーチン内の読み込まれたアセンブリの数を最小限に抑えるには重要です。

## <a name="summary"></a>まとめ

Visual Studio の起動で継続的にフィードバックを取得して、領域のいずれかを指定しました。 前述の目標はすべてのユーザーに対して発生するコンポーネントと、インストールされている拡張機能に関係なく一貫したスタートアップしたいし、思います所有者がその目標を達成するために役立つ拡張機能を使用します。 挙げたガイダンスは、スタートアップ、拡張機能への影響を理解するか、負荷を自動またはユーザーの生産性への影響を最小限に抑えるに非同期的にロードする必要を回避したりするために便利にする必要があります。
