---
title: IDebugPendingBreakpoint2::GetBreakpointRequest |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 49e83eb882388ca69fac1da1ae43f488345fe141
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113358"
---
# <a name="idebugpendingbreakpoint2getbreakpointrequest"></a>IDebugPendingBreakpoint2::GetBreakpointRequest
この保留中のブレークポイントの作成に使用されたブレークポイント要求を取得します。  
  
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
 [out]返します、 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)この保留中のブレークポイントの作成に使用されたブレークポイント要求を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`場合は、ブレークポイントが削除されました。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)