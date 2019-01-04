---
title: IDebugBinder::Bind |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72beca1ede38b310e34edfaabce0ee02e8fb52cc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865207"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
このメソッドは、メモリのコンテキストまたはシンボルの現在の値を格納しているオブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pContainer`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)によって参照されている子を格納している`pField`します。  
  
 `pField`  
 [in][IDebugField](../../../extensibility/debugger/reference/idebugfield.md)シンボルを表します。  
  
 `ppObject`  
 [out]返します、`IDebugObject`シンボルのインスタンスを表します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)