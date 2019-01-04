---
title: IDebugBoundBreakpoint2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d745bfb4682f92995145cc28967e416baaec35a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950844"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
このインターフェイスは、コードの場所にバインドされているブレークポイントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) は、ブレークポイントのサポートの一部として、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)このインターフェイスを作成します。 呼び出し[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)と[次](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)このインターフェイスを取得することもできます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugBoundBreakpoint2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|指定されたバインドされたブレークポイントの作成元となる保留中のブレークポイントを取得します。|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|このバインドされたブレークポイントの状態を取得します。|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|このバインドされたブレークポイントの現在のヒット カウントを取得します。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|このブレークポイントを表すブレークポイント解像度を取得します。|  
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|有効または、ブレークポイントを無効にします。|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|このバインドされたブレークポイントのヒット カウントを設定します。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設定またはバインドされたこのブレークポイントに関連付けられている条件を変更します。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|このバインドされたブレークポイントに関連付けられているパスの数を変更または設定します。|  
|[削除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|ブレークポイントを削除します。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)