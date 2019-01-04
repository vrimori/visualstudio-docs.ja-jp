---
title: IDebugObject::IsReadOnly |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5920e4804218d97c51ef7477f31a90556e8c7a3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53956037"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
このオブジェクトは読み取り専用のかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfIsReadOnly`  
 [out]0 以外を返します (`TRUE`) 場合、このオブジェクトは、読み取り専用である、それ以外の場合は、0 を返します (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 読み取り専用オブジェクトでは、その値は、作成後に変更を含めることはできません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)