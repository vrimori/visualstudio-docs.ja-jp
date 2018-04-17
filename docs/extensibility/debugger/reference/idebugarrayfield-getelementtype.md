---
title: IDebugArrayField::GetElementType |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c2eb6009eacd40081be28cc5945310d7a00fc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
配列の要素の型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppType`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)要素の型を記述するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)オブジェクトは、配列のすべての要素が同じ型であると仮定します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)