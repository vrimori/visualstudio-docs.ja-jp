---
title: IDebugObject2::GetAlias |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetAlias
helpviewer_keywords:
- IDebugObject2::GetAlias method
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 756f1249fc2adad9cdfa217c3f8fdd05eaa945d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889752"
---
# <a name="idebugobject2getalias"></a>IDebugObject2::GetAlias
存在する場合、このオブジェクトに関連付けられているエイリアスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppAlias`  
 [out]返します、 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)をこのオブジェクトの別名を表すオブジェクト。 それ以外の場合、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 呼び出して、オブジェクトのエイリアスが作成、 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)