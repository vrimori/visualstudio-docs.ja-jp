---
title: サポートされているイベントの種類 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6b308aabacf5a82f4ea630ccae256c56526f793
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supported-event-types"></a>サポートされているイベントの種類
Visual Studio デバッグでは、次のイベントの種類現在サポートされています。  
  
-   非同期イベント  
  
     セッション デバッグ マネージャー (SDM) に通知し、デバッグ中のアプリケーションの状態が変更された IDE です。 これらのイベントは、都合のよい、SDM および IDE のタイミングで処理されます。 コンソール アプリケーションは、イベントが処理されたら、デバッグ エンジン (DE) に、応答は送信されません。 [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)と[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)インターフェイスは非同期のイベントの例を示します。  
  
-   同期イベント  
  
     SDM とデバッグ中のアプリケーションの状態が変更された IDE に通知します。 これらのイベントおよび非同期のイベントの唯一の違いは、により、応答が送信される、 [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)メソッドです。  
  
     同期イベントを送信することは、DE、IDE を受信して、イベントを処理した後に処理を続行する必要がある場合に便利です。  
  
-   同期の停止イベント、または停止イベント  
  
     デバッグ中のアプリケーションのコードの実行が停止されたこと、SDM と、IDE に通知します。 メソッドを使用して停止イベントを送信する場合[イベント](../../extensibility/debugger/reference/idebugeventcallback2-event.md)、 [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)パラメーターが必要です。 次の方法のいずれかへの呼び出しによって停止イベントが継続します。  
  
    -   [実行します。](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     インターフェイス[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)と[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)停止イベントの例を示します。  
  
    > [!NOTE]
    >  非同期の停止イベントはサポートされていません。 非同期の停止イベントを送信するとエラーにすることをお勧めします。  
  
## <a name="discussion"></a>説明  
 イベントの実際の実装は、DE の設計に依存します。 送信の各イベントの種類はデを設計するときに設定されている、この属性によって決定されます。 たとえば、1 つ DE が送信可能性があります、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)停止イベントとして送信することがあります別中に、非同期のイベントとして。  
  
 次の表では、どのプログラムおよびスレッド パラメーターはどのイベントと、イベントの種類を指定します。 任意のイベントは同期していることができます。 イベントを同期している必要はありません。  
  
> [!NOTE]
>  [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)インターフェイスは、すべてのイベントに必要です。  
  
|event|IDebugProgram2|IDebugThread2|イベントを停止しています|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|必須|必須|[はい]|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|必須|必須|[はい]|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|必須|必須|×|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|許可されていません|許可されていません|×|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|許可されていません|許可されていません|×|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|必須|必須|[はい]|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|シリアル化|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|必須|必須|[はい]|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|シリアル化|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|必須|必須|[はい]|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|必須|必須|[はい]|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|シリアル化|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|必須|許可された場合は必要ありません。|×|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|必須|許可された場合は必要ありません。|×|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|必須|許可された場合は必要ありません。|×|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|必須|許可された場合は必要ありません。|×|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|必須|許可された場合は必要ありません。|×|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|IDebugStopCompleteEvent2|必須|必須|[はい]|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|必須|必須|[はい]|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|必須|必須|×|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|必須|必須|×|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|許可された場合は必要ありません。|許可された場合は必要ありません。|×|  
  
## <a name="see-also"></a>関連項目  
 [イベントの送信](../../extensibility/debugger/sending-events.md)