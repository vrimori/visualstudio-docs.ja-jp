---
title: IDebugExpressionEvaluator2::SetIDebugIDECallback |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 148d18f86ee88190aa1cf2a5a89807eb343c5d94
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903485"
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
式エバリュエーターを初期化中にコールバックを渡すデバッグ エンジンを有効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```csharp  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pCallback`  
 [in]コールバックのインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)