---
title: "方法: 拡張機能のパフォーマンスの診断 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
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
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>スタートアップの拡張機能の影響を測定

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Visual Studio 2017 で拡張機能のパフォーマンスに注目します。

お客様のフィードバックに基づき、Visual Studio 2017 リリースの対象領域のいずれかが発生したスタートアップとソリューションの読み込みのパフォーマンス 一方、Visual Studio プラットフォーム チームでは、一般に起動し、ソリューションの読み込みのパフォーマンスを向上させることに処理してきた、当社製品利用統計情報は、インストールされた拡張機能は、そのようなシナリオに多大な影響をもお勧めします。

ユーザーがこの影響を理解するために、低速の拡張機能のユーザーに通知する Visual Studio での新機能を追加します。 Visual Studio では、ソリューションの読み込みまたは起動のいずれかの速度が低下は、新しい拡張機能を検出すると、新しい「Visual Studio のパフォーマンスの管理」 ダイアログ ボックスを示す IDE で通知がユーザーに表示されます。 このダイアログ ボックスは、以前に検出された拡張機能を参照する [ヘルプ] メニューからも常にアクセスできます。

![Visual Studio のパフォーマンスを管理します。](~/docs/extensibility/media/manage-performance.png)

このドキュメントでは、拡張機能への影響を計算する方法と、それが分析される方法ローカルで拡張機能が拡張機能に影響を与えるパフォーマンスとして表示されるかどうかを記述することで拡張機能の開発者を支援を目的としています。

## <a name="how-extensions-can-impact-startup"></a>拡張機能が起動に影響を与える

起動時のパフォーマンスに影響する拡張機能の最も一般的な方法の&1; つは、自動負荷 NoSolutionExists や ShellInitialized などの既知のスタートアップ UI コンテキストのいずれかを選択することによってです。 これらの UI コンテキストの起動中にアクティブ化されると"ProvideAutoLoad"属性でこれらのコンテキストでの定義が含まれているすべてのパッケージが読み込まれ、その時点で初期化します。

拡張機能の影響を測定する場合、主にについて説明し、上記のコンテキストでの自動読み込みされる、拡張機能で費やされた時間。 単位時間がかかりますが含まれますに限定されません。

* 同期のパッケージの拡張機能アセンブリの読み込み
* 同期のパッケージのパッケージ クラスのコンス トラクターに費やされた時間
* 同期のパッケージのパッケージの初期化 (または SetSite) メソッドに費やされた時間
* 非同期パッケージは上記の操作をバック グラウンド スレッドで実行し、そのため、監視から除外されます。
* メイン スレッドで実行するパッケージの初期化中にスケジュールされている非同期の作業に費やした時間
* 具体的にはシェルの初期化のコンテキスト アクティブ化またはシェル ゾンビ状態の変更のイベント ハンドラーに費やされた時間

Visual Studio 2015 の自動読み込みを行うパッケージの削除中に役立ちますが、ユーザーができる、確実に、拡張機能を使用して自動的に読み込む拡張機能への影響を抑えることも、複数の特定のケースにそれらの負荷を延期をから複数の機能を追加しました。

これらの機能の詳細については、次のドキュメントにあります。

[ルール ベースの UI コンテキスト](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): UI コンテキストを中心として構築より豊富なベースのルール エンジンでは、プロジェクトの種類、種類と機能に基づいてカスタムのコンテキストを作成できます。 これらのカスタム コンテキストをスタートアップ; ではなく特定の機能を持つプロジェクトの存在などより具体的なシナリオの中に、パッケージの読み込みに使用できます。許可または[コマンドの表示/非表示にカスタムのコンテキストに関連付けられている](https://msdn.microsoft.com/en-us/library/bb166512.aspx)コマンドの状態のクエリのハンドラーを登録するには、プロジェクトの機能またはパッケージを読み込む必要がなくなります利用可能なその他の条件に基づきます。

[非同期のパッケージのサポート](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Visual Studio 2015 の新しい AsyncPackage の基本クラスは、Visual Studio パッケージ ロードするバック グラウンドで非同期的にパッケージの読み込みが自動読み込み属性または非同期サービス クエリによって要求された場合。 このバック グラウンド読み込みでは、拡張機能は、バック グラウンドで初期化されており、起動とソリューションの読み込みなどの重要なシナリオが影響を受けることはありません、応答性を維持するための IDE。

[非同期サービス](how-to-provide-an-asynchronous-visual-studio-service.md): 非同期パッケージのサポートも追加しましたサービスに非同期的に照会する、非同期のサービスを登録できることをサポートします。 さらに重要なバック グラウンド スレッドで非同期クエリの処理の大部分が発生するように、非同期クエリをサポートするために主要な Visual Studio のサービスに変換する取り組んでいます。 SComponentModel (Visual Studio MEF ホスト) では、非同期の読み込みが完全にサポートする拡張機能を許可するように、非同期クエリをサポートする主要なサービスの&1; つです。

## <a name="reducing-impact-of-auto-loaded-extensions"></a>拡張機能を読み込む自動の影響を軽減

パッケージを自動スタートアップ時に読み込まれる必要があるを場合は、起動に影響を与える、拡張機能の可能性を低減するパッケージの初期化中に実行された作業を最小限に抑える必要があります。

高価パッケージ初期化を引き起こす可能性のあるいくつかの例は次のとおりです。

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>非同期のパッケージの読み込みではなく同期パッケージの読み込みの使用

同期のパッケージが読み込まれるため、メイン スレッドで既定では、前述の代わりに、非同期のパッケージの基本クラスを使用して自動的に読み込まれますパッケージがある拡張機能の所有者をお勧めします。 非同期読み込みをサポートするために自動の読み込まれたパッケージを変更も、簡単にできるように以下に示すその他の問題を解決するのには。

### <a name="synchronous-filenetwork-io-requests"></a>同期ファイル]、[ネットワークの I/O 要求

理想的には任意の同期ファイルやネットワーク IO 要求避ける必要があります、メイン スレッドでの影響はマシンの状態に依存し、場合によっては長期間をブロックすることができます。

非同期のパッケージの読み込みと非同期 IO Api を使用すると、パッケージ初期化は、このような場合、メイン スレッドをブロックしないことと、ユーザーは引き続きバック グラウンドでの I/O 要求が発生するときに Visual Studio の対話を確認してください。

### <a name="early-initialization-of-services-components"></a>サービス、コンポーネントの初期化

使用されるか、パッケージ コンス トラクターまたは初期化メソッドでは、そのパッケージで提供されるサービスを初期化するとパッケージの初期化で一般的なパターンの&1; つです。 これにより、サービスが使用できる状態では、中にそれらのサービスがすぐに使用されていない場合の読み込みをパッケージに不必要なコストも追加できます。 代わりにこのようなサービスは、パッケージの初期化時に実行された作業を最小限に抑えるに要求時に初期化する必要があります。

グローバル サービスのパッケージによって提供される場合は、コンポーネントから要求される場合にのみ、サービスを遅延初期化関数を受け取り AddService メソッドを使用できます。 "遅延"を使用するサービスについては、パッケージ内で使用される、<T>または AsyncLazy<T>サービスは、初回使用時に初期化/照会することを確認します。

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>PerfView を使用して拡張が読み込まれる自動の影響を測定

遅くなるパッケージの初期化コード パスを識別するには、コード分析が役に立つは、Visual Studio の開始時にパッケージの読み込みの影響を理解 PerfView のようなアプリケーションを使用して、トレースを利用することもできます。

PerfView は、システム全体のトレース ツール、CPU 使用率またはシステム コールをブロックするために、アプリケーションのホット パスを理解するのに役立ちますです。 分析で使用可能な PerfView を使用して、サンプル拡張機能に関する簡単な例を次に示します、 [Microsoft ダウンロード センター](https://www.microsoft.com/en-us/download/details.aspx?id=28567)します。

**コード例:**

この例は、サンプルに基づいて次のコードで、表示されている一般的な遅延の原因の場合します。

```c#
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

インストールされている拡張機能を使って Visual Studio 環境をセットアップすると、PerfView を開き、"を収集 メニューから収集する ダイアログを開く起動時のトレースを記録できます。

![perfview 収集メニュー](~/docs/extensibility/media/perfview-collect-menu.png)

既定のオプションでは、呼び出し履歴の CPU 消費量が、ブロック時間もでは、以降も有効にしてください"スレッド Time"スタック。 設定の準備がいったん [コレクションの開始] をクリックし、記録が開始されると、Visual Studio を起動できます。

収集を停止する前に、Visual Studio が完全に初期化される、メイン ウィンドウが完全に表示されて、および拡張機能に自動的に表示する任意の UI 部分がある場合も表示されるかどうかを確認します。 Visual Studio は完全に読み込まれると、拡張機能を初期化、トレースを分析する記録を停止できます。

**PerfView でトレースを分析します。**

記録が完了すると PerfView は自動的にトレースを開きしてオプションを展開します。

この例の目的で、主に重要である「にスタックのスレッド」ビュー「高度なグループ」で見つけることができます。 このビューには、CPU 時間とディスク IO または待機ハンドルのように、ブロック時の両方を含むメソッドによって、スレッドで費やされた時間の合計が表示されます。

 ![スレッドの時刻のスタック](~/docs/extensibility/media/perfview-thread-time-stacks.png)

 「にスタックのスレッド」ビューを開くときに、分析を開始する"devenv"プロセスを選択してください。

PerfView より詳細な分析のための独自のヘルプ] メニューの [時刻のスタックのスレッドを読み取る方法に関するガイダンスを説明します。 この例の目的にのみ、パッケージのモジュール名とスタートアップ スレッドがあるスタックを含めることによってさらに、このビューをフィルター処理してみます。

1. 既定で追加、グループ化を削除する空のテキストに"GroupPats"を設定します。
2. セットをアセンブリ名の一部を含めるには、"IncPats"とスレッドのスタートアップ プロセスの既存のフィルターだけでなく この場合は、"devenv; である必要があります。スタートアップ スレッドです。MakeVsSlowExtension"です。

これで、ビューは、拡張機能に関連するアセンブリに関連付けられているコストをのみ表示されます。 このビューでいつでも スタートアップのスレッドの"Inc"(包括的なコスト) 列に表示がフィルター選択された拡張機能に関連して、スタートアップに影響します。

いくつかの興味深い呼び出し上記の例のスタックになります。

1. System.IO クラスを使用して IO: これらのフレームの包括的なコストはトレースに非常に高価ではないかもしれませんは、潜在的な原因である問題のファイル IO の速度はコンピューターごとに異なりますので。

  ![システムの io フレーム](~/docs/extensibility/media/perfview-system-io-frames.png)

2. その他の非同期操作を待機している呼び出しをブロックします。 包括時間はここでは、非同期操作の完了時にメイン スレッドがブロックされている時間を表します。

  ![ブロッキング呼び出しフレーム](~/docs/extensibility/media/perfview-blocking-call-frames.png)

「画像の読み込みスタック」がある影響を判断する役に立つトレースに他のビューのいずれかです。 「にスタックのスレッド」ビューに適用されると、同じフィルターを適用し、自動読み込まれたパッケージによって実行されるコードがあるため読み込むすべてのアセンブリを検索できます。

追加のアセンブリは、追加のディスク I/O かなり低速のマシン上の起動が遅くなるが、パッケージの初期化ルーチン内で読み込まれたアセンブリ数を最小限に抑えるには重要です。

## <a name="summary"></a>概要

Visual Studio の起動時には、継続的にフィードバックを得る領域の&1; つを指定しました。 私たちの目標は、前に述べたようはすべてのユーザーに対して発生するコンポーネントと、インストールされている拡張機能に関係なく一貫したスタートアップあり、その目標を達成するために拡張機能の所有者を使用したいです。 挙げたガイダンスは、スタートアップ、拡張機能への影響を理解し、自動的にロードまたはユーザーの生産性への影響を最小限に抑えるには非同期的にロードする必要がなく、いずれかに便利にする必要があります。
