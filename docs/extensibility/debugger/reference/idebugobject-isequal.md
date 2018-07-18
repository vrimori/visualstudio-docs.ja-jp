---
title: IDebugObject::IsEqual |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cccce3a530aa1871e093ce5a4ab9187f1ce9d4b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122393"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
このオブジェクトを持つオブジェクトを比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pObject`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)と比較するオブジェクトを表すオブジェクト。  
  
 `pfIsEqual`  
 [out]0 以外を返します (`TRUE`) のオブジェクトの値がそれ以外の場合は 0 を返します (`FALSE`)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 通常、このメソッドはによって表される値のアドレスを比較できます、`pObject`パラメーターが、これ[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクト以外の場合は、アドレスが等しいか、し、オブジェクトが等しいと見なすかどうかです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)