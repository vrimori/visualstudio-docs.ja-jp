---
title: IDebugCanStopEvent2::GetReason |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6b58e1a7a1f3595084a92f8db41d13875e47c0d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041777"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
なぜデバッグ エンジン (DE) を停止する必要がある理由を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcr`  
 [out]値を返します、 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)このイベントの理由を説明する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドの呼び出しの前に通常、 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)メソッドの呼び出し元は、0 以外を渡すかどうかを判断できるように (`TRUE`) に、`IDebugCanStopEvent2::CanStop`メソッド。  
  
 停止の理由には、いずれかを指定できる`CANSTOP_ENTRYPOINT`、エントリ ポイントに達した、DE つまりまたは`CANSTOP_STEPIN`関数にステップ インは、DE つまりします。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)