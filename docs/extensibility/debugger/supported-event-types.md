---
title: "サポートされているイベントの種類 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] をデバッグするには、イベントをサポート"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# サポートされているイベントの種類
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

現在デバッグ中の Visual Studio は次のイベントの種類をサポートします :  
  
-   非同期イベント  
  
     デバッグ対象のアプリケーションの状態が変更中のセッションのデバッグ マネージャー \(SDM\) および IDE を通知します。  これらのイベントは SDMIDE の暇をされる処理されます。  応答はデバッグ エンジン \(DE\) にイベントが処理される場合は送信されません。  [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) と [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) のインターフェイスは非同期イベントの例です。  
  
-   同期イベント  
  
     アプリケーションのデバッグ状態を変更する SDMIDE を通知します。  これらの非同期イベントとイベントの唯一の違いは応答が [ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) のメソッドによって返されます。  
  
     同期イベントを使用するとde\-DE を受け取って処理するイベントを IDE の後に処理を続行する必要がある場合に便利です。  
  
-   イベントを停止またはイベントを停止する同期  
  
     デバッグするアプリケーションがコードの実行を停止するとSDMIDE を通知します。  メソッド [イベント](../../extensibility/debugger/reference/idebugeventcallback2-event.md) によって停止のイベントを送信すると[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) のパラメーターは必須です。  停止してイベントは次の例のメソッドを呼び出すことです :  
  
    -   [実行](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [ステップ](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [続行](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     インターフェイス [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) と [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) はイベントを停止する例です。  
  
    > [!NOTE]
    >  イベントを停止する非同期はサポートされていません。  これは非同期停止イベントを送信エラーです。  
  
## 説明  
 イベントの実際の実装は de\-DE の設計によって異なります。  送信設定されている属性によって各イベントの種類は de\-DE をデザイン時に決定されます。  たとえば1 は de\-DE 非同期イベントとして別のが停止のイベントとして送信する可能性が [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) を送信する場合があります。  
  
 イベントイベントの種類にプログラムとスレッドのパラメーターが必要かを次の表に指定されています。  同期されたイベントはです。  イベントは同期する必要はありません。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) のインターフェイスはすべてのイベントに必要です。  
  
|Event|IDebugProgram2|IDebugThread2|イベントの停止|  
|-----------|--------------------|-------------------|-------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Required|Required|○|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Required|Required|○|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Required|Required|Ｘ|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|不可|不可|Ｘ|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|不可|不可|Ｘ|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Required|Required|○|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|割り当てが必須|割り当てが必須|指定できます。|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Required|Required|○|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|割り当てが必須|割り当てが必須|指定できます。|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Required|Required|○|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Required|Required|○|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|割り当てが必須|割り当てが必須|指定できます。|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Required|割り当てが必須|Ｘ|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Required|割り当てが必須|Ｘ|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Required|割り当てが必須|Ｘ|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Required|割り当てが必須|Ｘ|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Required|割り当てが必須|Ｘ|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|IDebugStopCompleteEvent2|Required|Required|○|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Required|Required|○|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Required|Required|Ｘ|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Required|Required|Ｘ|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|割り当てが必須|割り当てが必須|Ｘ|  
  
## 参照  
 [イベントを送信します。](../../extensibility/debugger/sending-events.md)