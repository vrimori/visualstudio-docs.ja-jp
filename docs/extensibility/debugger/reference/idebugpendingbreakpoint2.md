---
title: "IDebugPendingBreakpoint2 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ef986bd657a080c08fd0ebb85908ba59757bf207
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
このインターフェイスは、コードの場所にバインドする準備が整っているブレークポイントを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 デバッグ エンジン (DE) では、ブレークポイントのサポートの一部としてこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出し[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)から保留中のブレークポイントを作成、 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)インターフェイスです。 呼び出し[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)を作成、`IDebugBreakpoint2`をプログラムでバインドされたブレークポイントを表すインターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugPendingBreakpoint2`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|この保留中のブレークポイントをコードの場所にバインドできるかどうかを判断します。|  
|[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|1 つまたは複数のコードの場所にこの保留中のブレークポイントをバインドします。|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|保留中のブレークポイントの状態を取得します。|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|この保留中のブレークポイントの作成に使用されたブレークポイント要求を取得します。|  
|[仮想化します。](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|ブレークポイントの保留中の仮想化された状態を切り替えます。|  
|[有効にします。](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|保留中のブレークポイントの有効な状態を切り替えます。|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|設定または保留中のブレークポイントに関連付けられた条件を変更します。|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|設定または保留中のブレークポイントに関連付けられたパスの数を変更します。|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|この保留中のブレークポイントからバインドされているすべてのブレークポイントを列挙します。|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|この保留中のブレークポイントから生成されるすべてのエラー ブレークポイントを列挙します。|  
|[削除](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|この保留中のブレークポイントとそこからバインドされているすべてのブレークポイントを削除します。|  
  
## <a name="remarks"></a>コメント  
 `IDebugPendingBreakpoint2`1 つまたは複数のプログラムを適用できるコードにブレークポイントをバインドするために必要なすべての必要な情報のプロバイダーとしての考えることができます。  
  
 保留中のブレークポイントは、バインドされた 2 つ以上のブレークポイントを生成可能性があることができます。 など、C++ スタイル テンプレート内のブレークポイントは、そのテンプレートの一意のインスタンスごとにバインドされたブレークポイントを生成する可能性があります。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>参照  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)