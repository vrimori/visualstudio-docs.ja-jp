---
title: IDebugBinder::GetFunctionObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ed1a94fbd9abba9482d13d00e8c5c000063b276
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921070"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
このメソッドは、取得、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)関数のパラメーターを作成するために使用するオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppFunction`  
 [out]返します、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)関数パラメーターの作成に使用されるインターフェイス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)