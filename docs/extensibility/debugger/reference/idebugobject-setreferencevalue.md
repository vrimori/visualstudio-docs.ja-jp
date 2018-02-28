---
title: "IDebugObject::SetReferenceValue |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8045ef99ae500dac5baf2371d84c0503630dcc68
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
このオブジェクトの参照値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pObject`  
 [in][IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)新しい参照値を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、この[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクトで指定されたオブジェクトの値への参照、`pObject`パラメーター、以前のすべての参照を廃棄します。 注この`IDebugObject`オブジェクトには、参照型が既にあります。  
  
## <a name="see-also"></a>参照  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)