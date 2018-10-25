---
title: IDebugPendingBreakpoint2::GetBreakpointRequest |Microsoft Docs
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
ms.openlocfilehash: db1553295e3b8827330c78c1f6f35c21f1380cb4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921003"
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