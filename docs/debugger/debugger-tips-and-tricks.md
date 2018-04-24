---
title: ヒントし、コツについて、Visual Studio デバッガーで |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/15/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 729ea8e59f0b6efd6006308719cba19fbc8b5690
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio のデバッガー用の生産性に関するヒントと秘訣を理解します。

Visual Studio デバッガーは、いくつかの生産性に関するヒントとテクニックを学習するには、このトピックを読みます。 デバッガーの基本的な機能については、次を参照してください。[デバッガーの機能のツアー](../debugger/debugger-feature-tour.md)です。 このトピックでは、機能のツアーに含まれていない一部の領域を取り上げます。

## <a name="pin-data-tips"></a>暗証番号 (pin) のデータのヒント

場合は頻繁に合わせるとデータのヒントのデバッグ中に、クイック アクセスを自分自身に付与するための変数のデータのヒントをピン留めすることがあります。 変数はまだ再起動後もピン留めされました。 データのヒントをピン留めするには、そのポインターを置いたときに暗証番号 (pin) アイコンをクリックします。 複数の変数をピン留めすることができます。

![データのヒントをピン留め](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>コードのエディット コンティニュのデバッグ (c#、VB、C++)

Visual Studio でサポートされている多くの言語では、デバッグ セッションの途中でコードを編集し、デバッグを続行できます。 デバッガー、make 編集し、一時停止中にカーソルを合わせ、コードをクリックしてこの機能を使用する**f5 キーを押して**、 **f10 キーを押して**、または**F11**デバッグを続行します。

![エディット コンティニュ デバッグ](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

機能を使用して機能の制限の詳細については、次を参照してください。[エディット コンティニュ](../debugger/edit-and-continue.md)です。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>再現が困難な問題をデバッグします。

困難またはアプリ内の特定の状態を再作成に時間がかかる場合がある場合は、条件付きブレークポイントの使用が役立つかどうかを検討してください。 使用することができます[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)およびが壊れないように、アプリ コードに、アプリが不適切なデータ変数を格納する状態) などの目的の状態になるまでのブレークポイントをフィルター処理します。 式、フィルター、ヒット カウント、およびなどを使用して、条件を設定することができます。

#### <a name="to-create-a-conditional-breakpoint"></a>条件付きブレークポイントを作成するには

1. ブレークポイント アイコン (赤い丸) を右クリックして選択**条件**です。

2. **ブレークポイントの設定**ウィンドウで、式を入力します。

    ![条件付きブレークポイント](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 別の種類の条件の興味のあるを場合は、選択**フィルター**の代わりに**条件式**で、**ブレークポイントの設定** ダイアログ ボックスと、次のフィルターのヒント。

## <a name="change-the-execution-flow"></a>実行フローを変更します。

デバッガーでは、コードの行で一時停止して、マウスを使用して、左側の黄色の矢印のポインターを取得します。 コードの実行パス内のさまざまな位置に黄色の矢印のポインターを移動します。 F5 キーまたはステップ コマンドを使用して、アプリの実行を続行します。

![実行ポインターを移動](../debugger/media/dbg-tour-move-the-execution-pointer.gif "実行ポインターを移動")

実行フローを変更すると、別のコードの実行パスをテストまたはデバッガーを再起動しなくてもコードを再実行などの処理を行うことができます。

> [!WARNING]
> 多くの場合、この機能を使用するように注意する必要があり、ツールヒントに警告を参照してください。 その他の警告がすぎる表示可能性があります。 ポインターを移動すると、アプリ、以前のアプリケーション状態に戻すことはできません。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>範囲外のオブジェクト (c#、Visual Basic) を追跡します。

などのデバッガー ウィンドウを使用して変数を表示するは簡単、**ウォッチ**ウィンドウです。 変数がスコープ外になると、ただし、**ウォッチ** ウィンドウに気付くかもしれません、淡色表示にします。一部のアプリ シナリオでは、変数の値変更する可能性であっても、変数がスコープ外と緊密に監視することができます (たとえば、変数可能性があります取得ガベージ コレクション)。 オブジェクト ID を作成することで、変数を追跡することができます、**ウォッチ**ウィンドウです。

#### <a name="to-create-an-object-id"></a>オブジェクト ID を作成するには

1.  追跡する変数の近くのブレークポイントを設定します。

2.  デバッガーを起動 (**f5 キーを押して**) し、ブレークポイントで停止します。

3. 内の変数を検索、**ローカル**ウィンドウ (**デバッグ > Windows > [ローカル]**) を変数を右クリックし、**オブジェクト ID の作成**です。

    ![オブジェクト ID の作成](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  **$** ウィンドウに、 **[ローカル]** ウィンドウを閉じます。 この変数は、オブジェクト id です。
  
5.  オブジェクト ID 変数を右クリックして選択**ウォッチ式の追加**です。

詳細については、次を参照してください。[オブジェクト ID の作成](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)です。

## <a name="view-return-values-for-functions"></a>関数の戻り値の表示

表示するには、関数の戻り値を見てで表示される機能、 **[自動変数]**ウィンドウは、コードをステップ実行するときにします。 関数の戻り値を表示するには、興味のある関数が既に実行されていることを確認します (キーを押して**F10**関数呼び出しの現在停止している場合に 1 回)。 使用して、ウィンドウを閉じる場合**デバッグ > Windows > [自動変数]**を開くには、 **[自動変数]**ウィンドウです。

![[自動変数] ウィンドウ](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

さらに、内の関数を入力することができます、**イミディ エイト**戻り値を表示するウィンドウです。 (を使用して開く**デバッグ > Windows > イミディ エイト**)。

![イミディ エイト ウィンドウ](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

使用することも[擬似変数](../debugger/pseudovariables.md)で、**ウォッチ**と**イミディ エイト** ウィンドウなど`$ReturnValue`です。

## <a name="string_visualizer"></a>ビジュアライザーで文字列を検査します。

文字列を使用する場合は、全体の書式設定された文字列を表示すると役立つができます。 プレーン テキスト、XML、HTML、または JSON 文字列を表示するには、虫眼鏡アイコンをクリックして![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")文字列値を含む変数の上にマウス中にします。

![文字列ビジュアライザーを開く](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

文字列ビジュアライザーは、文字列が文字列の種類に応じて、形式が正しくないかどうかを確認するのに役立ちます。 たとえば、空白**値**フィールドは、文字列は、ビジュアライザーの型によって認識されないことを示します。 詳細については、次を参照してください。 [String ビジュアライザー ダイアログ ボックス](../debugger/string-visualizer-dialog-box.md)です。

![JSON 文字列ビジュアライザー](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

他のいくつかの種類などのデバッガー ウィンドウに表示されている WPF オブジェクトでは、ビジュアライザーを開くこともできます。

## <a name="break-into-code-on-handled-exceptions"></a>処理済みの例外でコードを中断します。

デバッガーは、未処理の例外でのコードに分割します。 ただし、例外の処理 (内で発生する例外など、`try/catch`ブロック) のバグのソースをすることもでき、発生するタイミングを調査することもできます。 オプションを構成することによって処理された例外およびのコードを中断するデバッガーを構成することができます、**例外設定** ダイアログ ボックス。 このダイアログ ボックスを選択して開く**デバッグ > Windows > 例外設定**です。

**例外設定** ダイアログ ボックスでは、特定の例外に対してコードを中断する、デバッガーに指示することができます。 次の図に、デバッガーがコードに中断されるたびに、`System.NullReferenceException`に発生します。 詳細については、次を参照してください。[例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)です。

![例外設定 ダイアログ ボックス](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>デッドロックや競合状態をデバッグします。

マルチ スレッド アプリに共通する問題の種類をデバッグする場合は、多くの場合、デバッグ中のスレッドの場所を表示するのに役立ちます。 これを行う簡単を使用して、**ソース内のスレッドを表示**ボタンをクリックします。

#### <a name="to-show-threads-in-your-source-code"></a>ソース コードのスレッドを表示するには

1.  デバッグ中をクリックして、**ソース内のスレッドを表示**ボタン![ソース内のスレッドを表示](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")で、**デバッグ**ツールバー。
  
2.  ウィンドウ左端の余白に注目します。 この行の表示、*スレッド マーカー*アイコン![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")布の 2 つのスレッドと類似しています。 スレッド マーカーは、スレッドが停止している位置を示します。

    スレッド マーカーを部分的にブレークポイントによって隠さ可能性がありますに注意してください。
  
3.  スレッド マーカーの上にポインターを置きます。 DataTip が表示されます。 データヒントは、停止したスレッドごとに名前とスレッド ID 番号を表示します。

    内のスレッドの場所を表示することも、[並列スタック ウィンドウ](../debugger/get-started-debugging-multithreaded-apps.md)します。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web サービスとネットワーク リソース (UWP) のペイロードを調べる

UWP アプリでは、ネットワーク操作を使用して実行を分析することができます、 `Windows.Web.Http` API です。 このツールを使用すると、web サービスとネットワーク リソースのデバッグを支援します。 ツールを使用するには選択**デバッグ > パフォーマンス プロファイラー**です。 選択**ネットワーク**を選択し**開始**です。 アプリで、`Windows.Web.Http` を使用するシナリオを実行し、**[コレクションの停止]** を選択してレポートを生成します。

![ネットワークの使用率ツールをプロファイリング](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

概要ビューで操作を選択すると、詳細が表示されます。

![詳細については、ネットワーク使用量ツールで](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

詳細については、「[ネットワーク使用率](../profiling/network-usage.md)」を参照してください。

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>デバッガーをアプリにアタッチする方法をより理解を深める

実行中のアプリに接続するには、デバッガーは、デバッグしようとしているアプリの正確な同じビルドに対して生成されるシンボル (.pdb) ファイルを読み込みます。 一部のシナリオでシンボル ファイルの少しの知識が役に立ちます。 Visual Studio がシンボルを使用してファイルを読み込む方法を調べることができます、**モジュール**ウィンドウです。

開く、**モジュール**を選択すると、デバッグ中にウィンドウ**デバッグ > Windows > モジュール**です。 **モジュール**ウィンドウわかります、デバッガーは、ユーザー コードとして扱う方法、どのようなモジュールまたは[*マイ コード*](../debugger/just-my-code.md)、およびモジュールの状態を読み込んでシンボル。 ほとんどのシナリオで、デバッガーは、ユーザー コードのシンボル ファイルを自動的に検出が、追加の手順が適正なシンボル ファイルを入手するために必要な .NET framework コードをシステム コード、またはサード パーティ製のライブラリ コードをステップ イン (またはデバッグ) する場合は、します。

![[モジュール] ウィンドウで、シンボル情報を表示](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

直接のシンボル情報を読み込むことができます、**モジュール**を右クリックしてウィンドウ**シンボルの読み込み**です。

場合によっては、アプリの開発者は、ファイルがない場合、一致するシンボル (、フット プリントを削減)、後でリリースされたバージョンをデバッグできるようにビルドのファイルが一致するシンボルのコピーを維持するが、アプリを出荷します。

デバッガーがユーザー コードとしてコードを分類する方法については、次を参照してください。[マイ コードのみ](../debugger/just-my-code.md)です。 シンボル ファイルの詳細についてを参照してください。[シンボル (.pdb) とソース ファイルを指定して、Visual Studio デバッガーで](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)です。

## <a name="learn-more"></a>詳細情報

その他のヒントとテクニックとより詳細な情報は、次のブログ投稿を参照してください。

- [Visual Studio でデバッグするために 7 のいずれか小さいほう既知ハッキング](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio での 7 の非表示 gems](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>関連項目
[キーボード ショートカット](../ide/tips-and-tricks-for-visual-studio.md)
