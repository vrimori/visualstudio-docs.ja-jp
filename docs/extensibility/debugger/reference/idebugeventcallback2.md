---
title: "IDebugEventCallback2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEventCallback2
helpviewer_keywords: IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 165f973fa9139f281211e6b01167b3d7044166df
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
このインターフェイスは、デバッグ イベントをセッション デバッグ マネージャー (SDM) に送信するデバッグ エンジン (DE) で使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]デバッグ エンジンからイベントを受信するには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 デバッグ エンジンが通常、SDM を呼び出すときにこのインターフェイスが受信[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)、または[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)です。 デバッグ エンジンは、イベントを SDM を呼び出すことによって送信[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugEventCallback2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|デバッグ、SDM にイベントの通知を送信します。|  
  
## <a name="remarks"></a>コメント  
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)と[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)には、指定、`IDebugEventCallback2`インターフェイス、これは、ケースではありませんし、インターフェイス ポインターには、null 値は常になります。 代わりに、デバッグ エンジンを使用する必要があります、`IDebugEventCallback2`インターフェイスへの呼び出しで受け取った[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)、[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)、または[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)です。  
  
 パッケージを実装する場合[IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md)マネージ コードで強くお勧めする<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A>に渡されるさまざまなインターフェイスで呼び出される[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)