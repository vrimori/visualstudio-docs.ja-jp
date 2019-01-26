---
title: '方法: 拡張機能のパフォーマンス診断 |Microsoft Docs'
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: jillfra
ms.workload:
- bertaygu
ms.openlocfilehash: 94a4febb30e2c476230bd038c014a1d4604a89d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955233"
---
# <a name="measuring-extension-impact-in-startup"></a>スタートアップの拡張機能への影響を測定します。

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017 で拡張機能のパフォーマンスに注目します。

お客様からのフィードバックに基づき、Visual Studio 2017 のリリースの対象領域の 1 つの起動とソリューションの読み込みパフォーマンスでしたが。 Visual Studio プラットフォーム チームとして扱っています起動とソリューションの読み込みのパフォーマンスの向上に。 一般に、この測定値には、インストールされた拡張機能は、そのようなシナリオに多大な影響をこともできますがお勧めします。

ユーザーがこの影響を理解するために、低速の拡張機能のユーザーに通知する Visual Studio で新しい機能を追加しました。 場合によっては、Visual Studio は、ソリューションの読み込みまたは起動が遅く、新しい拡張機能を検出します。 速度が低下が検出されると、新しい"Visual Studio のパフォーマンスの管理 ダイアログをポイントしている IDE に通知が表示されます。 このダイアログ ボックスは、以前検出された拡張機能の参照に [ヘルプ] メニューでも常にアクセスできます。

![Visual Studio のパフォーマンスを管理します。](media/manage-performance.png)

このドキュメントでは、拡張機能への影響を計算する方法を記述することで拡張機能の開発者を支援する目的としています。 このドキュメントでは、拡張機能への影響をローカルで分析する方法についても説明します。 拡張機能による影響の分析をローカルでかどうかは、拡張機能が拡張機能に影響を与えるパフォーマンスとして表示可能性がありますが決定されます。

> [!NOTE]
> このドキュメントでは、起動とソリューションの読み込みでの拡張機能への影響に重点を置いています。 拡張機能では、UI が応答しなくなる原因となるときに Visual Studio のパフォーマンスも影響します。 詳細については、このトピックでは、次を参照してください。[方法。UI の診断拡張機能によって遅延が発生](how-to-diagnose-ui-delays-caused-by-extensions.md)します。

## <a name="how-extensions-can-impact-startup"></a>拡張機能が起動に影響を与える

起動時のパフォーマンスに影響する拡張機能の最も一般的な方法の 1 つは、自動読み込み NoSolutionExists ShellInitialized などの既知のスタートアップ UI コンテキストのいずれかを選択してです。 これらの UI コンテキストは起動中にアクティブ化します。 すべてのパッケージが含まれる、`ProvideAutoLoad`これらのコンテキストでそれらの定義内の属性が読み込まれその時点で初期化します。

拡張機能の影響を測定、ときに主に焦点を上記のコンテキストでの自動読み込みを選択するこれらの拡張機能によって費やされた時間。 測定時間が含まれますに限定されません。

* 同期のパッケージの拡張機能アセンブリの読み込み
* 同期パッケージのパッケージ クラスのコンス トラクターに費やされた時間
* 同期のパッケージのパッケージの初期化 (または SetSite) メソッドに費やされた時間
* 非同期のパッケージで、上述の操作はバック グラウンド スレッドで実行します。  そのため、操作は、監視から除外されます。
* メイン スレッドで実行するパッケージの初期化中にスケジュールされた非同期作業に費やされた時間
* 具体的にはシェルの初期化のコンテキスト アクティブ化またはシェル ゾンビ状態の変更は、イベント ハンドラーに費やされた時間
* Visual Studio 2017 Update 3 以降もまずシェルが初期化される前に、アイドル状態の呼び出しで費やされた時間を監視します。 ハンドラーがアイドル状態で長時間の操作も IDE の応答が発生し、ユーザーによって認識される起動時の時間に影響します。

Visual Studio 2015 から多くの機能を追加しました。 これらの機能は、自動読み込みを行うパッケージの必要性を削除することをによりします。 機能より特定のケースに読み込むパッケージの必要性も延期します。 このような場合に、ユーザーができる、確実に、拡張機能を使用して、自動的に読み込むときに、拡張機能への影響を軽減または場所の例が含まれます。

これらの機能の詳細については、次のドキュメントにあります。

[ルール ベースの UI コンテキスト](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md):UI コンテキスト中心に構築された高度なルール ベース エンジンを使用すると、プロジェクトの種類、種類、および属性に基づくカスタム コンテキストを作成できます。 具体的なシナリオの中にパッケージを読み込むには、カスタムのコンテキストを使用できます。 これらの特定のシナリオには、スタートアップではなく特定の機能を持つプロジェクトの存在が含まれます。 カスタムのコンテキストを使っても[コマンドの可視性をカスタムのコンテキストに関連付けられる](visibilityconstraints-element.md)プロジェクト コンポーネントまたはその他の使用可能な条件に基づいて。 この機能では、コマンドの状態のクエリのハンドラーを登録するためのパッケージを読み込む必要があります。

[パッケージの非同期サポート](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md):Visual Studio 2015 で新しい AsyncPackage の基本クラスは、Visual Studio パッケージ ロードするバック グラウンドで非同期的にパッケージの読み込みを自動読み込み属性または非同期サービス クエリによって要求されたかどうかを使用できます。 このバック グラウンド読み込みは、応答性を維持するための IDE を使用できます。 IDE が応答して場合でも、拡張機能は、バック グラウンドで初期化され、起動とソリューションの読み込みなど、重要なシナリオが影響を受けることはありません。

[非同期サービス](how-to-provide-an-asynchronous-visual-studio-service.md):非同期パッケージ サポートにより、サポート サービスのクエリを非同期的に実行すると、非同期のサービスを登録することも追加されます。 さらに、非同期クエリでの作業の大半がバック グラウンド スレッドで発生するように、非同期クエリをサポートするために Visual Studio サービスのコアを変換に取り組んでいます。 SComponentModel (Visual Studio MEF ホスト) では、非同期クエリを完全に非同期読み込みをサポートする拡張機能を許可するようになりましたが、主要なサービスの 1 つです。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>読み込まれる拡張機能の自動の影響を軽減

パッケージは、起動時に読み込まれた自動にする必要がある場合、は、パッケージの初期化中に行われる作業を最小限に抑える必要があります。 パッケージの初期化作業を最小限に抑えるには、拡張機能の起動に影響を与える可能性が軽減されます。

高価 package の初期化を引き起こす可能性のあるいくつかの例は次のとおりです。

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>非同期のパッケージの読み込みではなく同期パッケージの読み込みの使用

同期パッケージが読み込まれるため、メイン スレッドで既定では、前述の代わりに、非同期のパッケージの基本クラスを使用するパッケージを自動的に読み込まれますがある拡張機能の所有者お勧めします。 非同期読み込みをサポートするために読み込まれたパッケージを自動に変更はも容易にできるように以下に示すその他の問題を解決するのには。

### <a name="synchronous-filenetwork-io-requests"></a>同期のファイル/ネットワーク IO 要求

理想的には、メイン スレッドですべての同期ファイルまたはネットワーク IO 要求を避ける必要があります。 影響はマシンの状態に依存し、場合によっては長期間をブロックできます。

非同期のパッケージの読み込みと非同期の IO Api を使用してもパッケージ初期化は、このような場合、メイン スレッドをブロックしないことを確認してください。 また、ユーザーはバック グラウンドで発生する I/O 要求中に Visual Studio の対話を継続できます。

### <a name="early-initialization-of-services-components"></a>サービス、コンポーネントの初期化

使用されるか、パッケージには、そのパッケージで提供されるサービスを初期化するためにパッケージの初期化で一般的なパターンの 1 つは`constructor`または`initialize`メソッド。 これにより、サービスがすぐに使用できますが、中にそれらのサービスがすぐに使用しない場合の読み込みをパッケージ化する不要なコストも追加できます。 代わりにこのようなサービスを初期化して、オンデマンド パッケージの初期化で実行された作業を最小限に抑える必要があります。

パッケージによって提供されるグローバル サービスで使用することができます`AddService`コンポーネントによって要求される場合にのみサービスを遅延初期化関数を受け取るメソッド。 非同期 (lazy) を使用するサービスは、パッケージ内で使用される、<T>または AsyncLazy<T>サービスは、初回使用時に初期化/照会するかどうかを確認します。

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>アクティビティ ログを使用して拡張機能が読み込まれる自動の影響を測定します。

Visual Studio 2017 Update 3 以降では、Visual Studio のアクティビティ ログはようになりましたエントリを含むパッケージのパフォーマンスに与える影響の起動とソリューションの読み込み中に。 これらの測定値を確認するためには、/log スイッチで Visual Studio を起動して開く必要がある*ActivityLog.xml*ファイル。

アクティビティ ログでは、エントリは 「Visual Studio のパフォーマンスの管理」のソースになり、次の例のようになります。

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

この例では、GUID"3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c"を使用してパッケージが Visual Studio のスタートアップで 2008 ms に費やされたことを示します。 そのパッケージの拡張機能を無効にした場合に節約ユーザーに表示されるよう、パッケージの影響を計算するときに、Visual Studio がプライマリ数として最上位レベルのコストを考慮することに注意してください。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView を使用して拡張機能が読み込まれる自動の影響を測定します。

パッケージの初期化が遅くなるコード パスを識別するには、コード分析が際に役立つ、Visual Studio の起動でパッケージの読み込みの影響を理解する PerfView などのアプリケーションを使用してトレースも利用できます。

PerfView は、システム全体のトレース ツールです。 このツールを使用すると、CPU 使用率またはシステム コールをブロックしているため、アプリケーションでのホット パスを理解できます。 分析で使用可能な PerfView を使用してサンプル拡張機能に関する簡単な例を次に示します、 [Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/details.aspx?id=28567)します。

**コード例:**

この例は、サンプルに基づいて次のコードを表示するために設計は、一般的な遅延の原因の場合します。

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

**PerfView でのトレースを記録します。**

PerfView、開きスタートアップのトレースを記録するには、拡張機能のインストールで、Visual Studio 環境を設定すると、**収集**ダイアログから、**収集**メニュー。

![perfview 収集メニュー](media/perfview-collect-menu.png)

既定のオプションは、CPU 使用量を呼び出し履歴を提供するが、ブロック時間も私たちは、以降も有効にしてください**スレッド時間**スタック。 クリックすることができます、設定が整ったら**収集を開始**の記録が開始されると、Visual Studio を起動するとします。

コレクションを停止する前に、Visual Studio を完全に初期化、メイン ウィンドウが完全に表示されると、拡張機能に自動的に表示する任意の UI 部分がある場合も表示されるかどうかを確認します。 Visual Studio が完全に読み込まれると、拡張機能が初期化されて、トレースを分析する記録を停止できます。

**PerfView でのトレースを分析するには。**

記録が完了すると PerfView は自動的にトレースを開きし、オプションを展開します。

この例のためには、主に関心が、**スレッド時間スタック**ビューで表示できる**Advanced Group**。 このビューには、CPU 時間およびディスク IO やハンドルを待機しているなどのブロック時間の両方を含むメソッドによって、スレッドで費やされた時間の合計が表示されます。

 ![スレッド スタックの時間](media/perfview-thread-time-stacks.png)

 開いているときに**スレッド時間スタック**表示、選択する必要があります、 **devenv**分析を開始するプロセス。

PerfView はスレッドのより詳細な分析のための独自のヘルプ] メニューの [時間の履歴を読み取る方法に関するガイダンスを詳しく説明します。 この例のために、のみ、パッケージのモジュール名とスタートアップ スレッドのスタックを含めることによってさらに、このビューをフィルター処理を対象します。

1. 設定**GroupPats**を空のテキストを既定で追加されたすべてのグループ化を削除します。
2. 設定**IncPats**既存プロセスのフィルターだけでなく、アセンブリ名とスレッドのスタートアップのパーツを含めます。 この場合、必要がある**devenv;スタートアップのスレッドMakeVsSlowExtension**します。

現在ビューは拡張機能に関連するアセンブリに関連付けられているコストのみを表示します。 このビューでは、いつでも表示、 **Inc (包括的なコスト)** スタートアップ スレッドの列がフィルター選択された拡張機能に関連して、スタートアップを受けています。

いくつかの興味深い呼び出し上記の例のスタックになります。

1. IO を使用して`System.IO`クラス。これらのフレームの包括的なコストをトレースにコストが高すぎることができない可能性があります、コンピューターからコンピューターにファイル IO の速度によって異なりますので、潜在的な問題の原因が、します。

   ![システム io フレーム](media/perfview-system-io-frames.png)

2. 他の作業を非同期に待機している呼び出しをブロックします。この場合は、包括時間は、非同期操作の完了時にメイン スレッドがブロックされている時間を表します。

   ![ブロッキング呼び出しフレーム](media/perfview-blocking-call-frames.png)

影響を判断で役に立つトレース内の他のビューの 1 つでは、**イメージ読み込みスタック**します。 同じフィルターを適用するに適用される**スレッド時間スタック**を表示し、自動の読み込まれたパッケージによって実行されるコードのために読み込まれたすべてのアセンブリを見つけます。

追加のアセンブリは、かなり低速のマシンの起動が遅くなる余分なディスク I/O、パッケージの初期化ルーチン内で読み込まれたアセンブリの数を最小限に抑えるには重要です。

## <a name="summary"></a>まとめ

Visual Studio の起動には、継続的にフィードバックを得る領域のいずれかを指定しました。 前述の目標は、すべてのユーザーに対して一貫性のあるスタートアップ コンポーネントと、インストールされている拡張機能に関係なく発生するのです。 今回はその目標を達成するために拡張機能の所有者を使用します。 上記のガイダンスは、スタートアップ、拡張機能への影響を理解し、負荷を自動またはユーザーの生産性に影響を最小限に抑えるためには、非同期的にロードする必要を回避するか、わかるでしょう。
