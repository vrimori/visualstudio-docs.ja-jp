---
title: IDebugCanStopEvent2::GetReason |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b67c619e81eea903ddc7ceca8781517ab5641e55
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842561"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

なぜデバッグ エンジン (DE) を停止する必要がある理由を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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

