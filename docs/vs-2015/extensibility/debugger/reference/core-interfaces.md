---
title: インターフェイスのコア |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2223059344c8f3d15eb94edc0dc2d2d1dc6fa336
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544374"
---
# <a name="core-interfaces"></a>コア インターフェイス
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Core インターフェイス](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/core-interfaces)します。  
  
次のインターフェイスは、コア インターフェイスを使用してデバッガーを拡張するため、[!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)]します。  
  
## <a name="discussion"></a>説明  
 これらのインターフェイスは主に、デバッグ エンジン (DE) の作成に使用します。 カテゴリがここで分類されます。  
  
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
  
-   [型のビジュアライザー](#TypeVisualizers)  
  
 インターフェイスを実装できるエンティティは次のとおりです。  
  
-   デバッグ エンジン (DE)  
  
-   ポート サプライヤー (PS)  
  
-   式エバリュエーター (EE)  
  
-   Visual Studio (VS)  
  
##  <a name="Breakpoints"></a> ブレークポイント  
 これらのインターフェイスが関連する実装およびブレークポイントの追跡。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|メモリの場所にバインドされているブレークポイントを表します。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|メモリ位置にブレークポイントがバインドされると、DE によって送信されます。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|ブレークポイント要求のチェックサムをドキュメントを表します。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|メモリの場所にバインドするブレークポイントが失敗したときに、DE によって送信されます。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに達すると、DE によって送信されます。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|ブレークポイント; の要求を表します保留中のブレークポイントの作成に使用します。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|ブレークポイント; の要求を表します保留中のブレークポイントの作成に使用します。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|ブレークポイントをバインドするための情報を表します。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|メモリの場所からブレークポイントがバインドされているとき、DE によって送信されます。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|無効なブレークポイントを表します (によって返される`IDebugBreakpointErrorEvent2`)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|解決の無効なブレークポイント情報を表します。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|ブレークポイントが設定されている関数内の位置を表します。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|バインドされる; ブレークポイントを表しますバインドされたブレークポイントの作成に使用します。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|バインドされたブレークポイントのセットを列挙体を表します。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|メモリの場所にバインドできませんでしたブレークポイントのセットを列挙体を表します。|  
  
##  <a name="Contexts"></a> コンテキスト  
 これらのインターフェイスは、さまざまな種類のデバッグ中のプログラム内でコンテキストを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|コードの命令の開始位置を表します。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|拡張、 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)モジュールとプロセスのインターフェイスの取得を有効にするインターフェイス。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|ドキュメント内の位置を表します。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式を評価するコンテキストを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトのコレクションのメモリ内の開始位置を表します。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|ブレークポイントまたは例外のスタック フレームのコンテキストを表します。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|コード コンテキストのセットに対して列挙体を表します。|  
  
##  <a name="CoreServer"></a> Server core  
 これらのインターフェイスは、プログラムがデバッグされているコンピューターを表します。 これらは実装によって[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]デバッグ エンジンを呼び出すことができますが、します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|ポートとポート サプライヤーだけでなく、コンピューターに関する情報へのアクセスを提供します。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表す、 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)リモート デバッグをサポートします。|  
  
##  <a name="DebugEngines"></a> デバッグ エンジン  
 これらのインターフェイスは、デバッグ エンジンと、関連するイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|カスタム デバッグ エンジンを表します。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|シンボル、JustMyCode、および例外の読み込みをサポートするカスタム デバッグ エンジンを表します。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|デバッグ タスクを処理する準備があることを示す、DE の新しいインスタンスによって送信されます。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|起動プログラムをサポートするカスタム デバッグ エンジンを表します。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|複数のデバッグ エンジンを処理するプログラムのノードを表します。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|スレッド、プログラム、またはスタック フレームからデバッグ エンジンにインターフェイスの取得に SDM を提供します。|  
  
##  <a name="Documents"></a> ドキュメント  
 これらのインターフェイスは、ドキュメント (ソース ファイル) とそれに関連付けられている要素を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|開かれているドキュメントを要求する、DE によって送信されます。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|逆アセンブルした命令ドキュメントからのストリームを表します。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS、DE|名前とクラス ID (CLSID) を指定する、DE によって提供されるドキュメントを表します。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE、EE|デバッグ ドキュメントのチェックサムを表し、コンポーネント間のチェックサムを渡すことができます。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS、DE|ドキュメントのコンテキストでは、特定のステートメントとコードのコンテキストに対応するドキュメント内の位置を表します。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS、DE|ドキュメント内の [全般] の位置を表します。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|文字のオフセットとしてソース ファイル内の位置を表します。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS、DE|デによって提供されるテキスト ドキュメントを表します (から派生した[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md))、実際のテキストを指定します。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリ内にあるソース ファイルへの変更を指定する、DE によって送信されます。|  
  
##  <a name="Events"></a> イベント  
 これらのインターフェイスは、DE およびセッション デバッグ マネージャー (SDM) の間で送信されるすべてのイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|開かれているドキュメントを要求する、DE によって送信されます。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|デバッグ エンジン (DE) は、シンボルの読み込み中にメッセージ バー セッション デバッグ マネージャーの状態を設定するには、(SDM) のこのインターフェイスを送信します。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|プログラムの中断が完了したときに、DE によって送信されます。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|ブレークポイントがバインドされている場合、DE によって送信されます。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|ブレークポイントがバインドに失敗した場合、DE によって送信されます。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|ブレークポイントに達すると、DE によって送信されます。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|ブレークポイントがバインドされている場合に、DE によって送信されます。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|特定の場所で停止したかどうかを判断する、DE によって送信されます。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|メモリ内にあるソース ファイルへの変更を指定する、DE によって送信されます。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|デバッグ タスクを処理する準備があることを示す、DE の新しいインスタンスによって送信されます。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|デバッグ中のプログラムが最初の命令を実行できる状態を示す、DE によって送信されます。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|人間が判読できるエラー メッセージを提供するエラーを返す可能性のある他のイベント インターフェイスで使用されるインターフェイスです。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE、PS|その他のすべてのイベント インターフェイスが派生する基本インターフェイスです。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|(特定のイベント インターフェイスを実装するオブジェクトとして表されます) のイベントが送信される SDM によって実装されるインターフェイスを表します。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|デバッグ中のプログラムで例外が発生したときに、DE によって送信されます。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期の式の評価が完了すると、DE によって送信されます。|  
|IDebugFindSymbolEvent2||互換性のために残されています。 使用しないでください。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|インターセプトの例外の処理が完了したときに、DE によって送信されます。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|プログラムの読み込みが完了したら、DE によって送信されます。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|ユーザーに情報メッセージを IDE の表示が DE で送信されます。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールがロードまたはアンロードされるときに、DE によって送信されます。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|信号、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]デバッガーの UI をユーザーに警告シンボルが起動した実行可能ファイルを見つけることできませんでした。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|任意の文字列を IDE の表示が DE によって送信されます。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS、DE|すべてのリスナー ポート イベントとの通信にポートが送信されます。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、PS|プロセスが作成されると、DE またはポートによって送信されます。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、PS|プロセスが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、PS|プログラムが作成されると、DE またはポートによって送信されます。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、PS|プログラムが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|既定の動作をオーバーライドするデバッグ エンジンを有効、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] UI のデバッグ セッションを終了するとします。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|プログラムの名前が変更されたときに、セッション デバッグ マネージャー (SDM) デバッグ エンジン (DE) から送信されます。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|ときに新しいプロパティ DE によって送信された (によって表される、`IDebugProperty2`インターフェイス) が作成されました。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときに、DE によって送信されます。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|戻り値を正しく表示できるように、または関数に対するをステップするとき、DE によって送信されます。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|デバッグを有効にメトリックの設定を読み取るエンジン リモートです。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|または不足命令の手順が完了したときに、DE によって送信されます。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|成功した場合またはモジュールのシンボルの読み込みの失敗を示す、DE によって送信されます。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されると、DE によって送信されます。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときに、DE によって送信されます。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドには、その名前が変更されたとき、DE によって送信されます。|  
  
##  <a name="Expressions"></a> 式  
 これらのインターフェイスは、特定のコンテキストで評価される式を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|評価される式を表します。 取得した、 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|式が評価されるコンテキストを表します。 取得した、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)インターフェイス。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|非同期の式の評価が完了すると、DE によって送信されます。|  
  
##  <a name="Memory"></a> メモリ  
 これらのインターフェイスは、メモリ内のバイトのシーケンスを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|読み取るまたは書き込むできるメモリ内のバイト シーケンスを表します。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|バイトのシーケンスのメモリ内の場所を表します。|  
  
##  <a name="Modules"></a> モジュール  
 これらのインターフェイスは、実行可能ファイルに対応するモジュールの場合またはします。DLL ファイルです。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|1 つの実行可能ファイルまたは DLL を表します。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表す、 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)シンボルをサポートします。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|モジュールがロードまたはアンロードされるときに、DE によって送信されます。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB ファイルに含まれるソース サーバーの情報を表します。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|認識されているモジュールのセットに対して列挙体を表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)します。|  
  
##  <a name="Ports"></a> ポート  
 これらのインターフェイスは、ポートとポート サプライヤーを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS、PS|ローカル コンピューターの既定のポートを表します。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|要求に DCOM を使用するデバッグ エンジンを有効、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]ファイアウォールをリモート デバッグするブロックはしないことを確認するための UI。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS、PS|ポートを表します。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|すべてのリスナー ポート イベントとの通信にポートが送信されます。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|起動したり、プロセスを終了するポートを表します。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|登録して、ポートを使用してプログラムの登録を解除するために使用現在デバッグ中のプログラムを追跡するためにポートを許可します。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|ポートを選択するためには、カスタマイズした UI を表します。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|新しいポートの作成または配置の元のポートの要求を表します。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|ポートのサプライヤーを表します。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|永続化できるポートのサプライヤーを表します (ディスクに保存) ポートについては、新たに作成します。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|により、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]内のテキストを表示する UI、**トランスポート情報**のセクション、**プロセスにアタッチ** ダイアログ ボックス。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|対象のコンピュータに関する情報の照会を許可します。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS、PS|ポートのセットに対して列挙体を表します。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|ポート サプライヤーのセットに対して列挙体を表します。|  
  
##  <a name="Processes"></a> プロセス  
 これらのインターフェイスは、プロセス、1 つまたは複数のプログラムを含む 1 つの実行可能ファイルを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS、DE|コンピューターで実行されているプロセスを表します。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS、DE|アクティブにサポートしているプロセスを表すデバッグ (ステップを置き換えるために使用を続けるには、メソッドをおよび実行で、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)インターフェイス)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE、PS|プロセスが作成されると、DE またはポートによって送信されます。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE、PS|プロセスが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|どのセッションに接続して追跡する必要があるプロセスを表します。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|ポート上のプロセスの一連の列挙体を表します。|  
  
##  <a name="Programs"></a> プログラム  
 これらのインターフェイスは、プログラム、物理的な実行可能ファイルまたはモジュールに必ずしも対応しませんが、実行の論理ユニットを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)を同時にデバッグされている他のアプリケーションと連携する必要があります。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE、PS|実行の論理単位を表します。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE、PS|プログラムが作成されると、DE またはポートによって送信されます。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE、PS|プログラムが破棄されたときに、DE またはポートによって送信されます。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE、PS|表す、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)を複数のデバッグ エンジンで処理できます。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)をセッションに接続して追跡できる必要があります。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE、PS|表す、 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)が実行されているプロセスに関する情報を返すことができます。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE、PS|デバッグ可能なプログラムを表します。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE、PS|プログラム ノードが関連付けられているプログラムにアタッチしようとすると、通知を許可します。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|その DE によって制御されるプログラムについての DE を照会する SDM の方法を提供します。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs でプログラムを表示して、デバッグ中に SDM を登録するために使用します。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE、PS|表す、 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)スレッドまたはプロセスの境界を越えてインターフェイスをマーシャ リングすることができます。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE、PS|プログラムのセットの列挙体を表します。|  
  
##  <a name="Properties"></a> プロパティ  
 これらのインターフェイスは、プロパティ、式の評価の結果は、通常、特定のコンテキストに関連付けられている値を表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)独自の方法でその値を表示することができます。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|スタック フレーム、ドキュメント、または、式の評価の結果の値を表します。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表す、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)任意の長さの文字列をサポートします。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|ときに新しいプロパティ DE によって送信された (によって表される、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)インターフェイス) が作成されました。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|プロパティが破棄されたときに、DE によって送信されます。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|任意の特定のスタック フレームの外側にあるプロパティへの参照を表します。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|一連の列挙体を表します[DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)変数、レジスタ、パラメーター、および式を記述する構造体。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|一連の列挙体を表します[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)構造体。|  
  
##  <a name="StackFrames"></a> スタック フレーム  
 これらのインターフェイスは、スタック フレームのコンテキストで、ブレークポイントまたは例外が発生しました。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|コンテキストを表しますでブレークポイントまたは例外が発生しました。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表す、 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)例外をインターセプトして処理することができます。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|セットに対して列挙体を表す[CODE_PATH](../../../extensibility/debugger/reference/code-path.md)関数を指定する構造体の呼び出しシーケンスの特定のスタック フレームに到達するために使用します。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|一連の列挙体を表します[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)構造体は、スタック フレームをについて説明します。|  
  
##  <a name="Threads"></a>スレッド  
 これらのインターフェイスは、スレッドと、関連するイベントを表します。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|実行のスレッドを表します。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|スレッドが作成されると、DE によって送信されます。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|スレッドが破棄されたときに、DE によって送信されます。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|スレッドには、その名前が変更されたとき、DE によって送信されます。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|スレッドのセットを列挙体を表します。|  
  
##  <a name="TypeVisualizers"></a> 型のビジュアライザー  
 これらのインターフェイスは、型のビジュアライザーのサポートを提供します。 通常、これらのインターフェイスは、式エバリュエーターによって実装されます。  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|型のビジュアライザーに表示するバイトの配列を表します。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|型のビジュアライザーに渡されるデータへのアクセスを取得するためのメソッドを提供します。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|アクセスを提供するプロパティを表す[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)実装します。|  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [カスタム デバッグ エンジンの作成](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

