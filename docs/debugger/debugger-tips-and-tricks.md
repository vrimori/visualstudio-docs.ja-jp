---
title: ヒントし、テクニックでは、Visual Studio デバッガー
description: Visual Studio デバッガーでサポートされている、あまり知られていない機能の一部について説明します
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
ms.openlocfilehash: 7e2a9acf315541dcf231d774fdb37e4c82649a4c
ms.sourcegitcommit: 7bb0225e1fd45999ce09e0b49c2cfae515c27e11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2018
ms.locfileid: "45612728"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Visual Studio のデバッガーの生産性に関するヒントと秘訣を学習します。

Visual Studio デバッガーのいくつかの生産性に関するヒントとテクニックを学習するには、このトピックを読みます。 デバッガーの基本機能については、次を参照してください。[デバッガー機能ツアー](../debugger/debugger-feature-tour.md)します。 このトピックでは、機能ツアーに含まれていない一部の領域について説明します。

## <a name="pin-data-tips"></a>データヒントのピン留めします。

頻繁に合わせるとデータのヒントのデバッグ中に場合、クイック アクセスできるようにするための変数のデータのヒントをピン留めすることがあります。 変数は、再起動後もピン留めされたままです。 データのヒントをピン留めするには、上にカーソルを合わせたとき、ピン アイコンをクリックします。 複数の変数をピン留めすることができます。

![データのヒントをピン留め](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>コードをエディット コンティニュ デバッグ (c#、VB、C++)

Visual Studio でサポートされているほとんどの言語では、デバッグ セッションの途中でコードを編集し、デバッグを続行します。 この機能を使用するデバッガー、make の編集、およびキーを押してで一時停止中に、カーソルでコードにクリックします。 **F5**、 **F10**、または**F11**デバッグを続行します。

![エディット コンティニュ デバッグ](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

機能を使用して機能の制限の詳細については、次を参照してください。[エディット コンティニュ](../debugger/edit-and-continue.md)します。

## <a name="debug-issues-that-are-hard-to-reproduce"></a>再現が難しい問題をデバッグします。

困難またはアプリの特定の状態を再作成に時間がかかり、条件付きブレークポイントの使用に役立つかどうかを検討してください。 使用することができます[条件付きブレークポイント](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression)と、アプリが (不適切なデータ変数は、格納する状態) などの目的の状態になるまで、アプリのコードに分割を回避するためにブレークポイントをフィルター処理します。 式、フィルター、ヒット カウントを使用して条件を設定することができます。

#### <a name="to-create-a-conditional-breakpoint"></a>条件付きブレークポイントを作成するには

1. ブレークポイントのアイコン (赤い丸) を右クリックし **条件**します。

2. **ブレークポイントの設定**ウィンドウで、式の型。

    ![条件付きブレークポイント](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. 別の種類の条件に関心がある場合は、選択**フィルター**の代わりに**条件式**で、**ブレークポイントの設定** ダイアログ ボックスと、次のフィルターのヒント。

## <a name="change-the-execution-flow"></a>実行フローを変更します。

デバッガーでのコード行で一時停止、マウスを使用して、左側の黄色の矢印のポインターを取得します。 コードの実行パスの別のポイントには、黄色の矢印のポインターを移動します。 F5 キーまたはステップのコマンドを使用して、アプリの実行を続行します。

![実行ポインターを移動](../debugger/media/dbg-tour-move-the-execution-pointer.gif "実行ポインターを移動")

実行フローを変更するには、別のコードの実行パスをテストまたはデバッガーを再起動しなくてもコードを再実行などの処理を行うことができます。

> [!WARNING]
> 多くの場合、この機能により、注意する必要があり、ツールヒントに警告を表示します。 すぎて他の警告を表示可能性があります。 ポインターを移動すると、アプリを以前のアプリケーション状態を元に戻すことはできません。

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>(C#、Visual Basic) の範囲外のオブジェクトを追跡します。

などのデバッガー ウィンドウを使用して変数を表示するは簡単、**ウォッチ**ウィンドウ。 ただし、ときに、変数がスコープ外で、**ウォッチ**ウィンドウ、お気付き、淡色表示にします。変数の値の一部のアプリのシナリオでも変数がスコープ外と緊密に監視したい場合があります変更可能性があります (get など)、変数がガベージ コレクション)。 オブジェクト ID を作成して、変数を追跡することができます、**ウォッチ**ウィンドウ。

#### <a name="to-create-an-object-id"></a>オブジェクト ID を作成するには

1.  追跡する変数の近くのブレークポイントを設定します。

2.  デバッガーを起動 (**F5**) し、ブレークポイントで停止します。

3. 変数を見つけて、**ローカル**ウィンドウ (**デバッグ > Windows > [ローカル]**) では、変数を右クリックし、選択**オブジェクト ID の作成**です。

    ![オブジェクト ID の作成](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  **$** ウィンドウに、 **[ローカル]** ウィンドウを閉じます。 この変数はオブジェクト ID です。
  
5.  オブジェクト ID の変数を右クリックし **ウォッチ式の追加**します。

詳細については、次を参照してください。[オブジェクト ID の作成](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds)です。

## <a name="view-return-values-for-functions"></a>関数の戻り値の表示

関数の表示を見て、関数の戻り値を表示するには、 **[自動変数]** ウィンドウ、コードのステップ実行中にします。 関数の戻り値を表示するには、興味のある関数が既に実行されていることを確認します (キーを押して**F10**関数呼び出しの現在停止している場合に 1 回)。 ウィンドウが閉じている場合を使用して、**デバッグ > Windows > [自動変数]** を開く、 **[自動変数]** ウィンドウ。

![[自動変数] ウィンドウ](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

さらに、内の関数を入力することができます、**イミディ エイト**戻り値を表示するウィンドウ。 (を使用して開く**デバッグ > Windows > イミディ エイト**)。

![イミディ エイト ウィンドウ](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

使用することもできます[擬似変数](../debugger/pseudovariables.md)で、**ウォッチ**と**イミディ エイト**ウィンドウなど`$ReturnValue`します。

## <a name="string_visualizer"></a>ビジュアライザーで文字列を検査します。

文字列を使用する場合は、全体の書式設定された文字列を表示、ことができます。 プレーン テキスト、XML、HTML、または JSON 文字列を表示するには、虫眼鏡アイコンをクリックします。 ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "ビジュアライザー アイコン")文字列値を含む変数を合わせたとき。

![文字列ビジュアライザーを開く](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

文字列のビジュアライザーを使用する文字列が文字列の種類に応じて、形式が正しくないかどうかを確認できます。 たとえば、空白を**値**フィールドは、ビジュアライザーの型では、文字列は認識されないことを示します。 詳細については、次を参照してください。[文字列ビジュアライザー ダイアログ ボックス](../debugger/string-visualizer-dialog-box.md)します。

![JSON 文字列ビジュアライザー](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

他のいくつかの種類など、デバッガー ウィンドウに表示する WPF オブジェクトでは、ビジュアライザーも開くことができます。

## <a name="break-into-code-on-handled-exceptions"></a>処理済みの例外でコードを中断します。

ハンドルされない例外で、コードに、デバッガーが中断されます。 ただし、例外の処理 (内で発生する例外など、`try/catch`ブロック) バグの原因をすることもでき、発生するタイミングを調査したい場合があります。 処理済み例外およびコードのオプションを構成することで中断するデバッガーを構成することができます、**例外設定** ダイアログ ボックス。 このダイアログ ボックスを選択して開く**デバッグ > Windows > 例外設定**します。

**例外設定** ダイアログ ボックスでは、特定の例外に対してコードを中断するようにデバッガーできます。 次の図で、デバッガーがコードに中断されるたびに、`System.NullReferenceException`に発生します。 詳細については、次を参照してください。[例外を管理する](../debugger/managing-exceptions-with-the-debugger.md)します。

![例外設定 ダイアログ ボックス](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>デッドロックや競合状態をデバッグします。

マルチ スレッド アプリケーションに共通する問題の種類をデバッグする必要がある場合は、デバッグ中のスレッドの場所を表示、多くの場合で役立ちます。 これを行うを使用して簡単に、**ソース スレッドを表示**ボタンをクリックします。

#### <a name="to-show-threads-in-your-source-code"></a>ソース コードのスレッドを表示するには

1.  デバッグ中に、をクリックして、**ソース スレッドを表示**ボタン![ソース スレッドを表示](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker")で、**デバッグ**ツールバー。
  
2.  ウィンドウ左端の余白に注目します。 この行で表示、*スレッド マーカー*アイコン![スレッド マーカー](../debugger/media/dbg-thread-marker.png "ThreadMarker")布の 2 つのスレッドと類似しています。 スレッド マーカーは、スレッドが停止している位置を示します。

    スレッド マーカーを部分的にブレークポイントによって隠さ可能性がありますに注意してください。
  
3.  スレッド マーカーの上にポインターを置きます。 DataTip が表示されます。 データヒントは、停止したスレッドごとに名前とスレッド ID 番号を表示します。

    内のスレッドの場所を表示することも、[並列スタック ウィンドウ](../debugger/get-started-debugging-multithreaded-apps.md)します。

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Web サービスとネットワーク リソース (UWP) のペイロードを調べる

UWP アプリを使用して実行されたネットワーク操作を分析することができます、 `Windows.Web.Http` API。 Web サービスとネットワーク リソースをデバッグする際に、このツールを使用することができます。 ツールを使用して、次のように選択します。**デバッグ > パフォーマンス Profiler**します。 選択**ネットワーク**を選び、**開始**します。 アプリで、`Windows.Web.Http` を使用するシナリオを実行し、**[コレクションの停止]** を選択してレポートを生成します。

![ネットワーク使用率プロファイリング ツール](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

概要ビューで操作を選択すると、詳細が表示されます。

![詳細については、ネットワーク使用率ツールで](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

詳細については、「[ネットワーク使用率](../profiling/network-usage.md)」を参照してください。

## <a name="modules_window"></a> アプリにデバッガーのアタッチをより理解を深める

実行中のアプリに接続するには、デバッガーは、シンボル (.pdb) ファイルをデバッグしようとするアプリの正確な同じビルドの生成を読み込みます。 一部のシナリオでシンボル ファイルの少しの知識が役に立ちます。 Visual Studio がシンボルを使用してファイルを読み込む方法を調べることができます、**モジュール**ウィンドウ。

開く、**モジュール**を選択してデバッグ中にウィンドウ**デバッグ > Windows > モジュール**します。 **モジュール**ウィンドウを確認する、デバッガーは、ユーザー コードとして扱うモジュールまたは[*マイ コード*](../debugger/just-my-code.md)、およびモジュールの状態を読み込んでシンボル。 ほとんどのシナリオで、デバッガーが自動的にユーザー コードのシンボル ファイルを検索しますが、追加の手順が正しいシンボル ファイルを入手するために必要な .NET framework コード、システム コード、またはサード パーティ製のライブラリ コードをステップ イン (またはデバッグ) する場合は、します。

![[モジュール] ウィンドウで、シンボル情報を表示](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

直接シンボル情報を読み込むことができます、**モジュール**を右クリックし、選択ウィンドウ**シンボルの読み込み**します。

場合によっては、アプリ開発者は、ファイルがない場合、一致するシンボル (をフット プリントを減らすため)、後でリリースされたバージョンをデバッグできるように、ビルドのファイルの一致するシンボルのコピーを維持するが、アプリを出荷します。

デバッガーはユーザー コードとしてコードを分類する方法についてを参照してください。[マイ コードのみ](../debugger/just-my-code.md)します。 シンボル ファイルの詳細についてを参照してください。 [Visual Studio デバッガーでシンボル (.pdb) ファイルとソース ファイルの指定](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)します。

## <a name="learn-more"></a>詳細情報

その他のヒントとテクニックとより詳細な情報は、次のブログ投稿を参照してください。

- [Visual Studio でのデバッグの 7 の小さい既知ハック](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [Visual Studio で非表示 gem の 7](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>関連項目
[キーボード ショートカット](../ide/tips-and-tricks-for-visual-studio.md)
