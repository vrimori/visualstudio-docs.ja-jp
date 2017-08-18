---
title: "JavaScript ランタイムのホスト | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="hosting-the-javascript-runtime"></a>JavaScript ランタイムのホスト
JavaScript ランタイム (JsRT) API は、Windows オペレーティング システム上で実行するデスクトップ、Windows ストア、およびサーバー側アプリケーションで、Microsoft Edge や Internet Explorer でも使用されている標準ベースの Chakra JavaScript エンジンを使用することによりアプリケーションにスクリプト機能を追加するための方法を提供するものです。 これらの API は、コンピューターに Internet Explorer Version 11.0  がインストールされている Windows 10 および Windows オペレーティング システムの任意のバージョンで使用できます。 詳細については、「 [Reference (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)」を参照してください。 Windows ストア アプリでの JsRT の使用方法については、「 [JsRT and the Universal Windows Platform](#Windows)」を参照してください。  
  
> [!NOTE]
>  このドキュメントは、JavaScript の言語機能の一般的な知識を持つ読者を対象としています。  
  
## <a name="concepts"></a>概念  
 JsRT API を使用して JavaScript エンジンをホストする方法を理解するには、2 つの主要な概念 (ランタイムおよび実行コンテキスト) が必要になります。  
  
 *ランタイムは* 完全な JavaScript 実行環境を表します。 作成する各ランタイムには、独自の分離ガベージ コレクションのヒープ、および既定では独自の just-in-time (JIT) コンパイラ スレッドとガベージ コレクター (GC) スレッドがあります。 *実行コンテキスト* は、他のすべての実行コンテキストとは異なる独自の JavaScript グローバル オブジェクトを持つ JavaScript 環境を表しています。 1 つのランタイムには、複数の実行コンテキストを含めることができます。その場合は、すべての実行コンテキストがランタイムに関連付けられた JIT コンパイラおよび GC スレッドを共有します。  
  
 ランタイムは、実行シングル スレッドを表します。 特定のスレッドでは同時に 1 つのランタイムのみをアクティブにでき、またランタイムは同時に 1 つのスレッド上でのみアクティブにできます。 ランタイムはレンタル スレッドであるため、スレッド上で現在アクティブでないランタイム (つまり、JavaScript コードを実行していないか、またはホストからの呼び出しに応答しないランタイム) は、アクティブなランタイムをまだ持たない任意のスレッド上で使用できます。  
  
 実行コンテキストは、特定のランタイムに関連付けられ、そのランタイム内でコードを実行します。 ランタイムとは異なり、複数の実行コンテキストは、スレッド上で同時にアクティブにできます。 このためホストは、実行コンテキストを呼び出すことができ、その実行コンテキストがホストにコールバックして、ホストが別の実行コンテキストを呼び出すことができます。  
  
 ![複数の実行コンテキスト](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 実際には、ホストが分離された環境でコードを実行する必要がない場合は、単一の実行コンテキストを使用できます。 同様に、ホストが複数のコードを同時に実行する必要がない場合は、単一のランタイムで十分です。  
  
## <a name="memory-management"></a>メモリ管理  
 JavaScript は、ガベージ コレクション言語であるため、別の言語から JsRT API を使用する場合、考慮する必要があるいくつかの注意点があります。  
  
 主な注意点は、JavaScript ガベージ コレクターがランタイムのヒープとスタックの 2 か所の値のみを参照できることです。 したがって、別の JavaScript 値、またはスタック上のローカル変数に格納された JavaScript 値へのガベージ コレクターによる参照は常に可能です。 ただし、ホストまたはシステムによって管理されたヒープなど、他の場所に格納された参照はガベージ コレクターによって参照されず、ホストでまだ使用されている値のコレクションの中断につながる可能性があります。  
  
> [!IMPORTANT]
>  一部の言語コンパイラ (Visual Studio C++ コンパイラなど) は、可能な場合はローカル変数を最適化により除去します。 該当する値が引き続きアクティブであることが予想される場合は、JavaScript 値を参照するローカル変数がスタック上にあることを確認する必要があります。  
  
 JavaScript 値に対する参照がガベージ コレクターから認識できない場所に格納されている場合、ホストは JsRT API を使用して手動で参照を追加および削除する必要があります。  
  
## <a name="exception-handling"></a>例外処理  
 スクリプトの実行中に JavaScript 例外が発生した場合、それを含むランタイムは例外状態になります。 例外状態では、コードは実行できず、ホストが `JsErrorInExceptionState` API を使用して例外を取得およびクリアするまで、すべての API 呼び出しがエラー コード `JsGetAndClearException` で失敗します。 ホストが例外状態のランタイムをクリアせずに JavaScript コールバックから戻った場合、コントロールが JavaScript エンジンに返却されるとすぐに JavaScript 例外が再スローされます。 またこれによってホスト コールバックは、ランタイムを例外状態に設定した後、ホスト コールバックから戻ることにより、JavaScript 例外を "スロー" できます。  
  
 ホストでは、ホスト コールバックをまたがって独自の内部例外を反映させることはできません。コールバック メソッドは、ランタイムにコントロールを返す前にすべてのホスト例外をキャッチする必要があります。  
  
## <a name="runtime-resource-usage"></a>ランタイムのリソースの使用  
 JsRT API では、ランタイムがリソースを使用する方法を監視および変更するためのさまざまな手段が公開されています。 これらは、一般に次のカテゴリに分類されます。  
  
-   **スレッドの使用法**。 既定では各ランタイムは、専用の JIT コンパイラ スレッドと、そのランタイムを処理する専用の GC スレッドを作成します。 ランタイムが `JsRuntimeAttributeDisableBackgroundWork` フラグによって作成された場合、JIT および GC の作業はそれぞれの個別のバックグラウンド スレッドではなく、ランタイム スレッド自体で実行されます。 またホストは、 `JsCreateRuntime` の呼び出しに対してスレッド サービス コールバックを提供できます。これによってホストは、最適と思われる任意の方法で JIT および GC の作業のスケジュールを設定できます。  
  
-   **メモリ使用状況**。 ランタイムのメモリ使用量を監視し、変更する方法はいくつかあります。 ランタイムが長時間実行している場合、ホストはランタイムの作成時に `JsRuntimeAttributeEnableIdleProcessing` フラグを指定した後、ホストがアイドル状態であるときに `JsIdle` を呼び出すことができます。 これによってエンジンは、アイドル時間までメモリ クリーンアップおよびブックキーピングの作業を延期できます。  
  
     ホストは `JsSetRuntimeBeforeCollectCallback`を呼び出すことで、ガベージ コレクションを監視できます。 また、 `JsSetRuntimeMemoryAllocationCallback`を呼び出すことで、ヒープによる割り当てを監視できます。 この API は、JavaScript の割り当てごとにコールバックせず、ランタイムのヒープで割り当てる追加領域が必要になった場合にのみコールバックすることに注意してください。 メモリ割り当てのコールバックではこの要求を拒否でき、これによってガベージ コレクションがトリガーされ、メモリが使用できない場合にはランタイムでメモリ不足エラーになります。  
  
     ホストはまた、ランタイムで使用できるメモリに制限を設定するために、 `JsSetRuntimeMemoryLimit` を呼び出すことができます。 ランタイムは制限に達すると、ガベージ コレクションをトリガーし、メモリが使用できない場合にはメモリ不足エラーがランタイムによりスローされます。  
  
-   **スクリプトの割り込みおよび評価**。 ホストは、ランタイム内の実行を終了するために `JsDisableRuntimeExecution` を呼び出すことができます。 この呼び出しは、いつでも任意のスレッドから行うことができます。 スクリプトの終了は、コードに挿入されたガード ポイントに達したかどうかに左右されるため、スクリプトは正確な該当時点で終了しない場合もありますが、その後すぐに終了します。 既定では、終了ガード ポイントは生成されたコード内に控えめに配置され、無限ループのようなすべての状況に対応するとは限りません。 `JsRuntimeAttributeAllowScriptInterrupt` フラグによりランタイムを作成すると、多くの場合に若干のパフォーマンスのオーバーヘッドにより、ランタイムで無限ループに対する追加チェックが挿入されます。  
  
     ホストが JIT コンパイラによるネイティブ コードの生成を許可しない場合は、 `JsRuntimeAttributeDisableNativeCodeGeneration` フラグを指定できます。 ホストはまた、 `JsRuntimeAttributeDisableEval` フラグを指定することにより、スクリプトによるスクリプト自体の動的な実行を不許可にできます。  
  
## <a name="debugging-and-profiling"></a>アプリケーションのデバッグとプロファイリング  
 JsRT API は、アクティブ スクリプト テクノロジによってデバッグおよびプロファイルをサポートします。  
  
 Windows 10 以降、Chakra JavaScript エンジンでレガシ エンジンとエッジ エンジンがサポートされるようになり、JsRT でいずれかを対象にすることができます (詳細については、[エッジ エンジンとレガシ エンジンの対象化](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)に関するページを参照してください)。 Visual Studio でのスクリプトのデバッグの機能は、レガシ エンジンとエッジ エンジンで異なります。 レガシ エンジンでは、ホストは、[IProcessDebugManager インターフェイス](../winscript/reference/iprocessdebugmanager-interface.md) インスタンスから取得できる [IDebugApplication インターフェイス](../winscript/reference/idebugapplication-interface.md) ポインターを提供する必要があります。 エッジ エンジンでは `IDebugApplication` は推奨されておらず、Chakra エンジンは Visual Studio デバッガーによるネイティブ デバッグ機能とスクリプト デバッグ機能を有効にします。その際、ユーザーからの `IDebugApplication` の実装は不要です。  
  
 実行コンテキスト内のスクリプトをデバッグできるようにするには、Chakra エンジンがそれほど効率的でないコード実行メソッドの使用に切り替える必要があります。 このために、デバッグ可能なコードは通常、デバッグ不可能なコードよりも低速です。 したがってレガシ エンジンでは、ホストは、 `IDebugApplication` から `JsCreateContext`ポインターを提供することにより最初から事前に実行コンテキスト内でデバッグを開始することもできますし、デバッグが必要になるまで待ってから `JsStartDebugging`を呼び出すこともできます。 エッジ エンジンでは、 `JsCreateContext` は `IDebugApplication` パラメーターを取らないため、スクリプトは `JsStartDebugging` が呼び出された後でのみデバッグ可能になります。 Visual Studio を使用してデバッグする場合は、"スクリプト" デバッガー オプションを有効にする必要があります。  
  
 実行コンテキスト内の JavaScript コードは、次の 2 つの方法のいずれかでプロファイルできます。 Windows 8.1 以上のバージョンでは、コマンド ラインの Visual Studio プロファイラーである vsperf.exe を /js スイッチと共に使用して、アプリケーションで実行される JavaScript コードを対象としたレポートを生成できます。 またホストは、 `JsStartProfiling` および `JsStopProfiling` を直接呼び出し、自身をプロファイルするためのコールバックを提供できます。 ホストはまた、 `JsEnumerateHeap`を呼び出すことによって、ガベージ コレクション ヒープの状態を調べることができます。 JsRT でのプロファイルは、レガシ エンジンとエッジ エンジンの間で同じように機能します。 ただし、JsRT のプロファイリング API (`JsStartProfiling`、 `JsStopProfiling`、 `JsEnumerateHeap`、および `JsIsEnumeratingHeap`) はユニバーサル Windows アプリでは使用できません。  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>JsRT and the Universal Windows Platform  
 JsRT API を使用すると、ユニバーサル Windows アプリにスクリプト機能を追加することができます。 JsRT API を使用するユニバーサル Windows アプリはエッジ JSRT API を対象とする必要があり、エッジ JSRT API はエッジ Chakra エンジンを対象とする必要があります。 詳細については、[エッジ エンジンとレガシ エンジンの対象化](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)に関するページを参照してください。 完全な JsRT API をユニバーサル Windows アプリで使用できます。ただし、プロファイルとヒープ列挙サポートは例外です (`JsStartProfiling`、 `JsStopProfiling`、 `JsEnumerateHeap`、および `JsIsEnumeratingHeap` はサポートされていません)。  
  
 また、JsRT は、Edge JsRT API [を介して API 名前空間を公開した後、スクリプトが](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) ユニバーサル Windows プラットフォーム (UWP) API `JsProjectWinRTNamespace`にネイティブにアクセスできるようにします。 ユニバーサル Windows アプリケーションは必要な名前空間をプロジェクトすることの他にはセットアップを必要としませんが、クラシックの (Win32) Windows アプリケーションでは、COM の初期化委任ポンピング メカニズムを `JsSetProjectionEnqueueCallback` によって有効にし、イベントおよび非同期 API を有効にする必要があります。 次の Win32 サンプルは、非同期の UWP API を使用して http クライアントを作成し、URI からコンテンツを取得しています。  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>関連項目  
 [JavaScript ランタイムのサンプル アプリ](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [リファレンス (JavaScript ランタイム)](../chakra-hosting/reference-javascript-runtime.md)   
 [JavaScript ランタイムのホスト処理](../chakra-hosting/javascript-runtime-hosting.md)
