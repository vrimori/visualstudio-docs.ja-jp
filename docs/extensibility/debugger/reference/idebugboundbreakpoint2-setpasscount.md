---
title: IDebugBoundBreakpoint2::SetPassCount |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f0ee22a1fe94836ac61dad2c98b69b02d63dbc69
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952194"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
設定またはバインドされたこのブレークポイントに関連付けられているパスの数を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bpPassCount`  
 [in][BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)パスの数を指定する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`にバインドされたブレークポイント オブジェクトの状態が設定されてかどうか`BPS_DELETED`(の一部、 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列挙型)。  
  
## <a name="remarks"></a>Remarks  
 パスの数は、ブレークポイントの発生タイミングを決定します。 現在のパスまたはヒット カウントを呼び出すことによって取得できます、 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)メソッド。  
  
 以前、このブレークポイントに関連付けられていたパスの数が失われます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)