---
title: IDebugPendingBreakpoint2::GetBreakpointRequest |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest
helpviewer_keywords:
- IDebugPendingBreakpoint2::GetBreakpointRequest method
- GetBreakpointRequest method
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 051c2f3f9c25eebbfbf686587652df1b830806f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927117"
---
# <a name="idebugpendingbreakpoint2getbreakpointrequest"></a>IDebugPendingBreakpoint2::GetBreakpointRequest
この保留中のブレークポイントの作成に使用されたブレークポイントの要求を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetBreakpointRequest(   
   IDebugBreakpointRequest2** ppBPRequest  
);  
```  
  
```csharp  
int GetBreakpointRequest(   
   out IDebugBreakpointRequest2 ppBPRequest  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppBPRequest`  
 [out]返します、 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)この保留中のブレークポイントの作成に使用されたブレークポイントの要求を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`ブレークポイントが削除されている場合。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)