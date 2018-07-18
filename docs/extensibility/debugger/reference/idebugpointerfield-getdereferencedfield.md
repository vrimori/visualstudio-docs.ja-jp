---
title: IDebugPointerField::GetDereferencedField |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77af1428dbdd0ea9f84000bda34ea8608b17cc24
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118610"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
このメソッドは、このポインター オブジェクトが指すオブジェクトの型を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppField`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)ターゲット オブジェクトの型を記述します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 例については、場合、 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)オブジェクトが、整数を指す、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)このメソッドによって返される型は、その整数型を記述します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)