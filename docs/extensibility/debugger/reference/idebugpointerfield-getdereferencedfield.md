---
title: IDebugPointerField::GetDereferencedField |Microsoft Docs
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
ms.openlocfilehash: 685499cae556a50a5e98e8fe32e8104098cc79e6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933249"
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 例については、場合、 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)オブジェクトが、整数を指す、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)このメソッドによって返される型が整数型について説明します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)