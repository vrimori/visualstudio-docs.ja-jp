---
title: "IDebugBoundBreakpoint2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2
helpviewer_keywords: IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2322b548106a7cbfff5ca4d96d7fc2d317308b10
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
このインターフェイスは、コードの場所にバインドされているブレークポイントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、ブレークポイントのサポートの一部としてこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)このインターフェイスを作成します。 呼び出す[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)と[次](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)も、このインターフェイスを取得できます。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugBoundBreakpoint2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|指定したバインドされたブレークポイントの作成元の保留中のブレークポイントを取得します。|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|このバインドされたブレークポイントの状態を取得します。|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|このバインドされたブレークポイントの現在のヒット カウントを取得します。|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|このブレークポイントを説明するブレークポイントの解像度を取得します。|  
|[有効にします。](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|有効または、ブレークポイントを無効にします。|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|このバインドされたブレークポイントのヒット カウントを設定します。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|設定またはこのバインドされたブレークポイントに関連付けられている条件を変更します。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|このバインドされたブレークポイントに関連付けられたパスの数の変更または設定します。|  
|[削除](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|ブレークポイントを削除します。|  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [次に](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)