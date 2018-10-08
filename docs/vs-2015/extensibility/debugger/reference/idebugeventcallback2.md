---
title: IDebugEventCallback2 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a140d5f0ecc2b250a8db4a2b78bfcc6544afd728
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537907"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugEventCallback2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugeventcallback2)します。  
  
このインターフェイスは、デバッグ イベントをセッション デバッグ マネージャー (SDM) に送信するデバッグ エンジン (DE) によって使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] デバッグ エンジンからイベントを受信するには、このインターフェイスを実装します。  
  
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
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [添付](../../../extensibility/debugger/reference/idebugengine2-attach.md)

