---
title: IDebugEventCallback2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdc20711d168a25ee28dde04849369a752fdb74a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54988091"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
このインターフェイスは、デバッグ イベントをセッション デバッグ マネージャー (SDM) に送信するデバッグ エンジン (DE) によって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] デバッグ エンジンからイベントを受信するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デバッグ エンジンが通常、SDM を呼び出すときにこのインターフェイスが受信[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)、または[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)します。 デバッグ エンジンは、呼び出すことによって、SDM にイベントを送信[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEventCallback2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|デバッグ、SDM をイベントの通知を送信します。|  
  
## <a name="remarks"></a>Remarks  
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)と[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)には、指定、`IDebugEventCallback2`インターフェイス、そうでないし、インターフェイス ポインターが null 値を必ずします。 代わりに、デバッグ エンジンを使用する必要があります、`IDebugEventCallback2`インターフェイスへの呼び出しで受け取った[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)、または[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)します。  
  
 パッケージを実装している場合[IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md)マネージ コードで強くお勧めする<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>に渡されるさまざまなインターフェイスで呼び出される[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)