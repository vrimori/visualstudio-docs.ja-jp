---
title: インターフェイスのコア |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 45521c0db16ac892d2e0e43e34c4b030075f7be2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108012"
---
# <a name="core-interfaces"></a>コア インターフェイス
次のインターフェイスは、コア インターフェイスを使用してデバッガーを拡張するため、[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]です。  
  
## <a name="discussion"></a>説明  
 これらのインターフェイスは、デバッグ エンジン (DE) を作成する、主に使用されます。 編成されたここでカテゴリ別。  
  
-   [ブレークポイント](#Breakpoints)  
  
-   [コンテキスト](#Contexts)  
  
-   [Server core](#CoreServer)  
  
-   [デバッグ エンジン](#DebugEngines)  
  
-   [ドキュメント](#Documents)  
  
-   [イベント](#Events)  
  
-   [式](#Expressions)  
  
-   [メモリ](#Memory)  
  
-   [モジュール](#Modules)  
  
-   [ポート](#Ports)  
  
-   [プロセス](#Processes)  
  
-   [プログラム](#Programs)  
  
-   [プロパティ](#Properties)  
  
-   [スタック フレーム](#StackFrames)  
  
-   [スレッド](#Threads)  
  
-   [ビジュアライザーの型](#TypeVisualizers)  
  
 インターフェイスを実装できるエンティティは次のとおりです。  
  
-   デバッグ エンジン (DE)  
  
-   ポート Supplier (PS)。  
  
-   式エバリュエーター (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> ブレークポイント  
 これらのインターフェイスが関連する実装およびブレークポイントの追跡にします。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|メモリの場所にバインドされているブレークポイントを表します。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|メモリ位置にブレークポイントがバインドされている場合は、DE によって送信されます。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|ブレークポイントの要求のチェックサムをドキュメントを表します。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|メモリの場所にバインドされているブレークポイントが失敗した場合に、DE によって送信されます。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに達したときに、DE によって送信されます。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|ブレークポイントを設定する要求を表します保留中のブレークポイントの作成に使用します。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|ブレークポイントを設定する要求を表します保留中のブレークポイントの作成に使用します。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|ブレークポイントをバインドするための情報を表します。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|メモリ位置からブレークポイントのバインドがない場合に、DE によって送信されます。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|無効なブレークポイントを表します (によって返される`IDebugBreakpointErrorEvent2`)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|無効なブレークポイントに関する解決策情報を表します。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|ブレークポイントが設定されている関数内の位置を表します。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|バインドされる以外はブレークポイントを表しますバインドされたブレークポイントの作成に使用します。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|バインドされたブレークポイントのセットに対して列挙を表します。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|メモリ位置へバインドできませんでしたブレークポイントのセットに対して列挙を表します。|  
  
##  <a name="Contexts"></a> コンテキスト  
 これらのインターフェイスは、さまざまな種類のデバッグ中のプログラム内でコンテキストを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|コードの命令の開始位置を表します。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|拡張、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)インターフェイス モジュールとプロセスのインターフェイスの取得を有効にします。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|ドキュメント内の位置を表します。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式を評価するコンテキストを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|一連のバイトのメモリ内の開始位置を表します。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|コードのコンテキストのセットに対して列挙を表します。|  
  
##  <a name="CoreServer"></a> Server core  
 これらのインターフェイスは、プログラムをデバッグ中のコンピューターを表します。 によって実装されて[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッグ エンジンに呼び出すことができますが、します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|ポートとポートの仕入先だけでなく、コンピューターに関する情報へのアクセスを提供します。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表す、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)リモート デバッグをサポートします。|  
  
##  <a name="DebugEngines"></a> デバッグ エンジン  
 これらのインターフェイスは、デバッグ エンジンと、関連するイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|カスタム デバッグ エンジンを表します。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|シンボル、JustMyCode、および例外の読み込みをサポートするカスタム デバッグ エンジンを表します。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|デバッグ タスクを処理する準備があることを示す、DE の新しいインスタンスによって送信されます。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|起動プログラムをサポートするカスタム デバッグ エンジンを表します。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|複数のデバッグ エンジンを処理するプログラム ノードを表します。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|SDM スレッド、プログラム、またはスタック フレームからデバッグ エンジンにインターフェイスを取得するための手段を提供します。|  
  
##  <a name="Documents"></a> ドキュメント  
 これらのインターフェイスは、ドキュメント (ソース ファイル) とそれらに関連付けられている要素を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|開かれるドキュメントを要求する、DE によって送信されます。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|逆アセンブルされた命令ドキュメントからのストリームを表します。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS、DE|名前とクラス ID (CLSID) を指定する、DE、によって提供されるドキュメントを表します。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE、EE|デバッグ ドキュメントのチェックサムを表し、コンポーネント間で、チェックサムをやり取りできるようにします。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|ドキュメントのコンテキストでは、特定のステートメントとコード コンテキストに対応するドキュメント内の位置を表します。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS、DE|ドキュメント内での一般的な位置を表します。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|ソース ファイル内の文字オフセットとしての位置を表します。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS、DE|デによって提供されるテキスト ドキュメントを表します (から派生した[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md))、実際のテキストを指定します。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリ内にあるソース ファイルへの変更を指定する、DE によって送信されます。|  
  
##  <a name="Events"></a> イベント  
 これらのインターフェイスは、DE およびセッション デバッグ マネージャー (SDM) の間で送信されるすべてのイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|開かれるドキュメントを要求する、DE によって送信されます。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|デバッグ エンジン (DE) は、シンボルの読み込み中にバーのメッセージをセッション デバッグ マネージャーの状態を設定するには、(SDM) のこのインターフェイスを送信します。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|プログラムの中断が完了したときに、デによって送信されます。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|ブレークポイントがバインドされている場合は、DE によって送信されます。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|ブレークポイントがバインドに失敗した場合は、DE によって送信されます。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに達したときに、DE によって送信されます。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|ブレークポイントがバインド解除されるときに、デから送信されます。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|特定の位置で停止するかどうかを決定する、DE によって送信されます。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリ内にあるソース ファイルへの変更を指定する、DE によって送信されます。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|デバッグ タスクを処理する準備があることを示す、DE の新しいインスタンスによって送信されます。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|デバッグ中のプログラムは、最初の命令を実行できる状態を示すために、DE によって送信されます。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|人間が判読できるエラー メッセージを提供するその他のイベント インターフェイス、エラーを返す場合があります、によって使用されるインターフェイスです。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE、PS|その他のすべてのイベント インターフェイスが派生する基本インターフェイスです。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|(特定のイベント インターフェイスを実装するオブジェクトで表されます) のイベントが送信される SDM によって実装されるインターフェイスを表します。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|デバッグ中のプログラムで例外が発生した場合は、DE によって送信されます。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期の式の評価が完了すると、DE によって送信されます。|  
|IDebugFindSymbolEvent2||互換性のために残されています。 使用しないでください。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|受信済みの例外の処理が完了したときに、デによって送信されます。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|プログラムには、読み込みが完了したら、DE によって送信されます。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|ユーザーに情報メッセージを IDE 表示 DE で送信します。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールがロードまたはアンロードされるときに、デから送信されます。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|信号、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッガーの UI をシンボルことができない、起動した実行可能ファイルのあるユーザーに警告します。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|任意の文字列を IDE 表示 DE によって送信されます。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS、DE|ポート イベントをリスナーに通信するためにポートが送信されます。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、PS|プロセスが作成されたときに、DE またはポートから送信されます。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、PS|プロセスが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、PS|プログラムが作成されたときに、DE またはポートから送信されます。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、PS|プログラムが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|既定の動作をオーバーライドするデバッグ エンジンを有効に、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI デバッグ セッションを終了するとします。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|プログラムの名前が変更されたときに、セッション デバッグ マネージャー (SDM) にデバッグ エンジン (DE) から送信されます。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|ときに、新しいプロパティ DE によって送信された (によって表される、`IDebugProperty2`インターフェイス) が作成されました。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときに、DE によって送信されます。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|戻り値が正しく表示されるように、または、この関数をステップ実行時に、DE によって送信されます。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|デバッグを有効にメトリックの設定を読み取るエンジンでのリモートです。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|内外に命令の手順が完了したときに、デから送信されます。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|モジュールのシンボルの読み込みの成否を示すために、DE によって送信されます。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されたときに、デから送信されます。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときに、DE によって送信されます。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドには、その名前が変更されたときに、デから送信されます。|  
  
##  <a name="Expressions"></a> 式  
 これらのインターフェイスは、特定のコンテキストで評価される式を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|評価される式を表します。 取得した、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイスです。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式が評価されるコンテキストを表します。 取得した、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)インターフェイスです。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期の式の評価が完了すると、DE によって送信されます。|  
  
##  <a name="Memory"></a> メモリ  
 これらのインターフェイスは、メモリ内のバイトのシーケンスを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|読み取るまたは書き込むことができるメモリ内のバイト シーケンスを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトのシーケンスのメモリ内の場所を表します。|  
  
##  <a name="Modules"></a> モジュール  
 これらのインターフェイスを表す、モジュールは、実行可能ファイルに対応していますか。DLL ファイルです。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|1 つの実行可能ファイルまたは DLL を表します。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表す、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)シンボルをサポートします。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールがロードまたはアンロードされるときに、デから送信されます。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB ファイルに含まれているソース サーバー情報を表します。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|認識されているモジュールのセットに対して列挙を表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)です。|  
  
##  <a name="Ports"></a> ポート  
 これらのインターフェイスは、ポートとポートのサプライヤーを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS、PS|ローカル コンピューター上の既定のポートを表します。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|DCOM を使用するように依頼するデバッグ エンジンを有効に、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI をファイアウォールをリモート デバッグするブロックはしないことを確認してください。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS、PS|ポートを表します。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|ポート イベントをリスナーに通信するためにポートが送信されます。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|起動し、プロセスを終了するポートを表します。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|登録および; ポートとプログラムを登録解除するために使用現在デバッグ中のプログラムを追跡するためにポートを使用できます。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|ポートを選択するためには、カスタマイズした UI を表します。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|新しいポートの作成または配置の元のポートの要求を表します。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|ポートの業者を表します。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|永続化できるポートの業者を表します (ディスクに保存) ポートについては、新たに作成します。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|により、[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]内のテキストを表示するための UI、**トランスポート情報**のセクションで、**プロセスにアタッチする** ダイアログ ボックス。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|対象のコンピュータに関する情報の照会を許可します。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS、PS|ポートのセットに対して列挙を表します。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|ポートのサプライヤーのセットに対して列挙を表します。|  
  
##  <a name="Processes"></a> プロセス  
 これらのインターフェイスは、プロセス、1 つまたは複数のプログラムを含む単一の実行可能ファイルを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS、DE|コンピューターで実行されているプロセスを表します。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS、DE|積極的にサポートしているプロセスを表すデバッグ (続けるとでメソッドの実行手順を置き換えるための、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、PS|プロセスが作成されたときに、DE またはポートから送信されます。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、PS|プロセスが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|どのセッションに接続して追跡する必要があるプロセスを表します。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|ポート上のプロセスのセットの列挙体を表します。|  
  
##  <a name="Programs"></a> プログラム  
 これらのインターフェイスは、プログラム、必ずしも物理的な実行可能ファイルまたはモジュールに対応していない、実行の論理単位を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)同時にデバッグされている他のプログラムと連携する必要があります。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE、PS|実行の論理単位を表します。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、PS|プログラムが作成されたときに、DE またはポートから送信されます。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、PS|プログラムが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|表す、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)を複数のデバッグ エンジンで処理できます。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)をセッションに接続して管理できる必要があります。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE、PS|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)が実行されているプロセスに関する情報を返すことができます。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE、PS|デバッグ可能なプログラムを表します。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE、PS|プログラム ノードが関連付けられているプログラムにアタッチしようとする通知を許可します。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM その DE によって制御されるプログラムについて DE を照会するための手段を提供します。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|SDM を表示して、デバッグ中にプログラムを登録する DEs によって使用されます。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE、PS|表す、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)スレッドまたはプロセスの境界を越えてインターフェイスをマーシャ リングすることができます。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE、PS|プログラムのセットの列挙体を表します。|  
  
##  <a name="Properties"></a> プロパティ  
 これらのインターフェイスは、プロパティ、式の評価の結果では通常、特定のコンテキストに関連付けられている値を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)独自の方法でその値を表示することができます。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|スタック フレーム、ドキュメント、または式の評価の結果の値を表します。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)任意の長さの文字列をサポートします。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|ときに、新しいプロパティ DE によって送信された (によって表される、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)インターフェイス) が作成されました。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときに、DE によって送信されます。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|任意の特定のスタック フレームの外側にあるプロパティへの参照を表します。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|セットに対して列挙を表す[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)変数、レジスタ、パラメーター、および式を記述する構造体。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|セットに対して列挙を表す[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体。|  
  
##  <a name="StackFrames"></a> スタック フレーム  
 これらのインターフェイスを表すコンテキストのスタック フレームで、ブレークポイントまたは例外が発生しました。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|コンテキストを表しますでブレークポイントまたは例外が発生しました。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表す、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)例外をインターセプト処理することができます。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|セットに対して列挙を表す[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)関数を指定する構造体呼び出しシーケンスの特定のスタック フレームに到達するために使用します。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|セットに対して列挙を表す[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体は、スタック フレームを説明します。|  
  
##  <a name="Threads"></a>スレッド  
 これらのインターフェイスは、スレッドと、関連するイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|実行のスレッドを表します。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されたときに、デから送信されます。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときに、DE によって送信されます。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドには、その名前が変更されたときに、デから送信されます。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|スレッドのセットに対する列挙体を表します。|  
  
##  <a name="TypeVisualizers"></a> ビジュアライザーの型  
 これらのインターフェイスは、ビジュアライザーの型のサポートを提供します。 これらのインターフェイスは、通常、式エバリュエーターで実装します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|型のビジュアライザーに表示する対象のバイト配列を表します。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|型のビジュアライザーに渡されるデータへのアクセスを取得するためのメソッドを提供します。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|アクセスを提供するプロパティを表す[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)実装します。|  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [カスタム デバッグ エンジンの作成](../../../extensibility/debugger/creating-a-custom-debug-engine.md)