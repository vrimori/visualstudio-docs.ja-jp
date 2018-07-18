---
title: IDebugArrayObject::GetElements |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae1d22af6796c2de72c763137c8f96feb7885407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099816"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
すべての要素の配列の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```csharp  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]返します、 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)により、すべての要素を列挙するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 代わりに、使用、 [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)と[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)要素を反復処理するメソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)