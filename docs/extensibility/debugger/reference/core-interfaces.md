---
title: "コア インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] をデバッグするには、中核となるインターフェイスします。"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# コア インターフェイス
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

次のインターフェイスは [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] を使用してデバッガー拡張のコア インターフェイスです。  
  
## 説明  
 これらのインターフェイスは主にデバッグ エンジンを作成するために使用 \(DE\) されます。  ここではカテゴリ別に整理されています :  
  
-   [ブレークポイント](#Breakpoints)  
  
-   [コンテキスト](#Contexts)  
  
-   [コア サーバー](#CoreServer)  
  
-   [デバッグ エンジン](#DebugEngines)  
  
-   [ドキュメント](#Documents)  
  
-   [イベント](#Events)  
  
-   [式](#Expressions)  
  
-   [メモリ](#Memory)  
  
-   [モジュール](#Modules)  
  
-   [ポート](#Ports)  
  
-   [&#91;プロセス&#93;](#Processes)  
  
-   [プログラム](#Programs)  
  
-   [プロパティ](#Properties)  
  
-   [スタック フレーム](#StackFrames)  
  
-   [Threads](#Threads)  
  
-   [ビジュアライザーの型](#TypeVisualizers)  
  
 インターフェイスを実装するエンティティは次のとおりです :  
  
-   デバッグ エンジン \(DE\)  
  
-   ポートのサプライヤー \(PS\)  
  
-   式エバリュエーター \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> ブレークポイント  
 これらのインターフェイスはブレークポイントの実装と追跡に関連しています。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|メモリ位置にバインドされたブレークポイントを表します。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|ブレークポイントがメモリ位置にバインドされたときにが送信します。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|と|ブレークポイントの要求のドキュメントのチェックサムを表します。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|ブレークポイントがメモリ位置にバインドされないときにが送信します。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに到達したときにが送信します。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|と|ブレークポイントの要求を表します ; 保留中のブレークポイントの作成に使用する。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|と|ブレークポイントの要求を表します ; 保留中のブレークポイントの作成に使用する。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|ブレークポイントをバインドするために使用する情報を表します。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|ブレークポイントがメモリ位置から解放したときにが送信します。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|無効なブレークポイントを表します \(`IDebugBreakpointErrorEvent2` によって返される\)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|無効なブレークポイントについての解決方法を表します。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|ブレークポイントが設定されている関数の位置を表します。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|バインドされたブレークポイントを表します ; バインドされたブレークポイントの作成に使用する。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|一連のバインド ブレークポイントに対する列挙型を表します。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|メモリ位置にバインドできなかった一連のブレークポイントに対する列挙型を表します。|  
  
##  <a name="Contexts"></a> コンテキスト  
 これらのインターフェイスはさまざまな種類のデバッグするプログラム内のコンテキストを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|コード命令の開始位置を表します。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) のインターフェイスをモジュールとプロセスのインターフェイスを検索できるように拡張します。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|とde\-DE|ドキュメントの位置を表します。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式を評価するコンテキストを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトのコレクションをメモリ内の開始位置を表します。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|一連のコード コンテキストに対する列挙型を表します。|  
  
##  <a name="CoreServer"></a> コア サーバー  
 これらのインターフェイスはプログラムをデバッグ対象のコンピューターを表します。  これらは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] によって実装されたデバッグ エンジンによって呼び出すことができます。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|と|ポートとポートのサプライヤーへのアクセスとコンピューターに関する情報を提供します。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|と|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) をサポートするリモート デバッグ表します。|  
  
##  <a name="DebugEngines"></a> デバッグ エンジン  
 これらのインターフェイスはデバッグ エンジンと関連イベントを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|カスタムのデバッグ エンジンを表します。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|JustMyCode シンボルおよび例外の読み込みをサポートするカスタムのデバッグ エンジンを表します。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|あることを示す場合はde\-DE の各新しいインスタンスによって非デバッグ タスクを処理できるようになっています。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|カスタム デバッグ エンジンを表します。プログラムを起動サポート|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DEPS|プログラムのノードをそのハンドルの複数のデバッグ エンジンを表します。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|スレッドプログラムまたはスタック フレームのデバッグ エンジンに SDM インターフェイスを取得する方法を提供します。|  
  
##  <a name="Documents"></a> ドキュメント  
 これらのインターフェイスはドキュメント ファイル \(ソース\) と関連する要素を表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|ドキュメントが開かれるように要求するに送信します。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|ドキュメントの逆アセンブル命令ストリームを表します。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|とde\-DE|DE によって提供されるドキュメントを表の名前とクラス ID \(CLSID\) を指定します。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|EEde\-DE|デバッグに関連するドキュメントのチェックサムを表しコンポーネント間のチェックサムの受け渡しを有効にします。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|とde\-DE|特定のステートメントに対応するドキュメント内のドキュメントのコンテキスト位置およびコード コンテキストを表します。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|とde\-DE|ドキュメント内の一般的な位置を表します。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|と|文字のオフセットとしてソース ファイルの位置を表します。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|とde\-DE|実際のテキストを指定するには [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)de\-DE \(から派生\) 指定されたテキスト ドキュメントを表します。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリのソース ファイルへの変更を指定するために送信します。|  
  
##  <a name="Events"></a> イベント  
 これらのインターフェイスは de\-DE とマネージャー \(SDM\) のデバッグ セッション間で送信されるすべてのイベントを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|ドキュメントが開かれるように要求するに送信します。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|デバッグ エンジンはセッション \(DE\) マネージャー \(SDM\) にデバッグ シンボルの読み込み中にステータス バーのメッセージを設定するにはこのインターフェイスを送信します。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|プログラムの中断が完了したときにが送信します。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|ブレークポイントがバインドされたときにが送信します。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|ブレークポイントをバインドしないときにが送信します。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに到達したときにが送信します。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|ブレークポイントは自由なときにが送信します。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|特定の場所で停止するかどうかを判断するためにによって送信します。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリのソース ファイルへの変更を指定するために送信します。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|あることを示す場合はde\-DE の各新しいインスタンスによって非デバッグ タスクを処理できるようになっています。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|デバッグするプログラムを示すためにde\-DE によって送信最初の命令を実行する準備が整いました。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|エラーを返しますが別のイベントによって使用されるインターフェイスは人が判読可能なエラー メッセージを表示するためのインターフェイスです。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DEPS|他のすべてのイベント インターフェイスされる基本インターフェイスを派生させます。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|と|イベント \(特定のイベント インターフェイスを実装するオブジェクトで表現\) 送信 SDM によって実装されたインターフェイスを表します。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|デバッグ対象のプログラムに例外が発生したときにが送信します。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期式の評価が完了したときにが送信します。|  
|IDebugFindSymbolEvent2||互換性のために残されています。  使用しないでください。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|傍受された例外の処理が完了したときにが送信します。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|プログラムに完了の読み込みがあるときにが送信します。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|IDE の表示をユーザーに表示する情報メッセージが送信します。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールの読み込みまたはアンロードされるときにが送信します。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|シンボルが起動する実行可能ファイルに検出できないと [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] デバッガーの UI をユーザーに通知するように通知します。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|IDE の表示を持つようにしますが送信した任意の文字列。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|とde\-DE|リスナーとポートのイベントを通知するためにポートに送信されます。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DEPS|プロセスが作成された日時 \(またはポートに送信します。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DEPS|プロセスが破棄されたときにポートに送信します。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DEPS|プログラムが作成された日時 \(またはポートに送信します。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DEPS|プログラムが破棄されたときにポートに送信します。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|デバッグ セッションを終了時にデバッグ エンジンは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の UI  の既定の動作をオーバーライドできます。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|プログラムの名前が変更されたときにデバッグ エンジン \(DE\) からデバッグ セッションのマネージャー \(SDM\) に送信されます。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|新しいプロパティが \(`IDebugProperty2` のインターフェイスで表現\) を作成したときにが送信します。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときにが送信します。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|この関数の戻り値についてまたはが正しく表示するときにが送信します。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|と|非常設定をリモートで有効なデバッグ エンジン。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|命令に上またはの手順が完了したときにが送信します。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|モジュールのシンボルの読み込みの成功または失敗を示すようにに送信します。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されたときにが送信します。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときにが送信します。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドの名前が変化したときにが送信します。|  
  
##  <a name="Expressions"></a> 式  
 これらのインターフェイスは特定のコンテキストで評価される式を表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|評価される式を表します。  [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) インターフェイスから派生します。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式が評価されるコンテキストを表します。  [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) インターフェイスから派生します。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期式の評価が完了したときにが送信します。|  
  
##  <a name="Memory"></a> メモリ  
 これらのインターフェイスはメモリ内のバイト シーケンスを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|読み取るかメモリに書き込むことのできるバイト シーケンスを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイト シーケンスをメモリ内での位置を表します。|  
  
##  <a name="Modules"></a> モジュール  
 これらのインターフェイスは実行可能ファイルまたは .dll ファイルに対応するモジュールを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|単一の実行可能ファイルまたは DLL を表します。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|この [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) サポートのシンボルを表します。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールの読み込みまたはアンロードされるときにが送信します。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB ファイルに含まれるソース サーバーの情報を表します。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) によって認識される一連のモジュールに対する列挙型を表します。|  
  
##  <a name="Ports"></a> ポート  
 これらのインターフェイスがポートとポートの業者を表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|とPS|ローカル コンピューターの既定のポートを表します。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|と|[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] の UI を呼び出すためにファイアウォールがリモート デバッグをブロックするために DCOM が使用するデバッグ エンジンを有効にします。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|とPS|ポートを表します。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|リスナーとポートのイベントを通知するためにポートに送信されます。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|プロセスを開始および終了するポートを表します。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|ポートでプログラムを登録および登録解除するために使用される ; ポートが現在デバッグ中のプログラムを追跡できるようにします。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|ポートを選択するためのカスタマイズした UI を表します。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|と|新しいポートを作成するか既存のポートの要求を表します。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|ポートの業者を表します。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|\(ディスクに保存\) 作成したポートに関する情報を保持するポートの業者を表します。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI を ENT1ENT \[出力\] ダイアログ ボックスの \[ENT0ENT\] セクション内のテキストを表示できます。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|と|ターゲット コンピューターに関する情報の問い合わせに使用できます。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|とPS|一連のポート経由の列挙型を表します。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|と|一連のポートのサプライヤーに対する列挙型を表します。|  
  
##  <a name="Processes"></a> \[プロセス\]  
 これらのインターフェイスはプロセス一つ以上のプログラムを含む単一の実行可能ファイルを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PSde\-DE|コンピューターで実行されているプロセスを表します。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PSde\-DE|実行時にデバッグをサポートするプロセスを表します \(手順を置き換え[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) してインターフェイスのメソッドを実装するために使用されます\)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DEPS|プロセスが作成された日時 \(またはポートに送信します。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DEPS|プロセスが破棄されたときにポートに送信します。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|すべてのセッションではアタッチされたかを追跡するプロセスを表します。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|一連のポートのプロセスの列挙型を表します。|  
  
##  <a name="Programs"></a> プログラム  
 これらのインターフェイスはプログラム物理的な実行可能ファイルまたはモジュールに必ず対応する実装の論理単位を表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表します [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を同時にデバッグ他のプログラムと連携して動作する必要があります。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DEPS|実行の論理単位を表します。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DEPS|プログラムが作成された日時 \(またはポートに送信します。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DEPS|プログラムが破棄されたときにポートに送信します。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DEPS|複数のデバッグ エンジンで処理できる [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) を表します。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|すべてのセッションではアタッチされたかを追跡する必要がある [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を表します。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DEPS|アプリケーションが実行されているプロセスに関する情報を返すことができます [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) を表します。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DEPS|デバッグするプログラムを表します。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DEPS|プログラムのノードに関連付けられているプログラムにアタッチしようを通知できます。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|その de\-DE によって制御されるプログラムを DE SDM を照会する方法を提供します。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|と|次に示すために SDM のプログラムを登録するために DEs に使用するデバッグします。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DEPS|スレッドまたはプロセスの境界を越えてインターフェイスをマーシャリングできる [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) を表します。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DEPS|一連のプログラムの列挙型を表します。|  
  
##  <a name="Properties"></a> プロパティ  
 これらのインターフェイスはプロパティ特定のコンテキスト通常式の評価結果に関連付けられた値を表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|カスタムの方法で値を表示できる [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) を表します。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|式の評価のスタック フレームやドキュメント結果値を表します。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|この [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) をサポートする任意長い文字列を表します。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|新しいプロパティが \([IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスで表現\) を作成したときにが送信します。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときにが送信します。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|特定のスタック フレームの外側にあるできるプロパティへの参照を表します。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|変数レジスタパラメーターおよび式を記述する一連の [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造上の列挙型を表します。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|一連の [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) の構造上の列挙型を表します。|  
  
##  <a name="StackFrames"></a> スタック フレーム  
 これらのインターフェイスはスタック フレームやブレークポイントまたは例外が発生したコンテキストを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外が発生したコンテキストを表します。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|傍受された例外を処理できる [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) を表します。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|特定のスタック フレームにするために使用される関数呼び出しのシーケンスを指定する [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md) 構造のセットの列挙型を表します。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|スタック フレームを記述する一連の [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) の構造上の列挙型を表します。|  
  
##  <a name="Threads"></a> Threads  
 これらのインターフェイスはスレッドと関連イベントを表します。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|実行中のスレッドを表します。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されたときにが送信します。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときにが送信します。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドの名前が変化したときにが送信します。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|一連のスレッドに対する列挙型を表します。|  
  
##  <a name="TypeVisualizers"></a> ビジュアライザーの型  
 これらのインターフェイスは型のビジュアライザーをサポートします。  これらのインターフェイスは式エバリュエーターによって正常に実行されます。  
  
|Interface|実行する|Description|  
|---------------|----------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|型のビジュアライザーに表示するバイトの配列を表します。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|データへのアクセスを型のビジュアライザーに渡す取得するためのメソッドを提供します。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) の実装へのアクセスを提供するプロパティを表します。|  
  
## 参照  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [カスタム デバッグ エンジンを作成します。](../../../extensibility/debugger/creating-a-custom-debug-engine.md)