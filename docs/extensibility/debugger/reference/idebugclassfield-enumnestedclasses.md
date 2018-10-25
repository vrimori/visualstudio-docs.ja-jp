---
title: IDebugClassField::EnumNestedClasses |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a313e27c3dcbca0136b00bfb789e444174474369
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937531"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
このクラスに入れ子になったクラスの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]返します、 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)入れ子になったクラスの一覧を表すオブジェクト。 入れ子になったクラスがない場合は、null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合は S_OK を返します。 または入れ子になったクラスがない場合は S_FALSE を返します。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 列挙体の各要素は、 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)入れ子になったクラスを記述するオブジェクト。  
  
 入れ子になったクラスは、別のクラス内で定義されたクラスです。 例えば:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)列挙型を表すオブジェクトの 1 つが含まれます、`NestedClass`クラス。  
  
## <a name="see-also"></a>関連項目  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)