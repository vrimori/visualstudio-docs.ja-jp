---
title: IDebugCustomAttribute::GetAttributeTypeField |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5447539cba2d336a21d9a55a833418185dc4a34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938102"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
カスタム属性クラスの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetAttributeTypeField(   
   IDebugClassField** ppCAType  
);  
```  
  
```csharp  
int GetAttributeTypeField(  
   out IDebugClassField ppCAType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppCAType`  
 [out]返します、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)カスタム属性がインスタンス クラスを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 カスタム属性は、常にクラスです。 このメソッドへのアクセスを提供する、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)そのクラスを記述するオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)