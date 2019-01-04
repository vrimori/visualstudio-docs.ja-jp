---
title: FIELD_INFO |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- FIELD_INFO
helpviewer_keywords:
- FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d473c153b2487f2063e965cbcc3818befc1e2aa5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896527"
---
# <a name="fieldinfo"></a>FIELD_INFO
この構造体には、ローカル変数、パラメーター、またはその他のフィールドについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwFields  
 フラグの組み合わせ、 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)のどのメンバーが入力を指定する列挙体。  
  
 bstrFullName  
 フィールドの完全名。  
  
 bstrName  
 フィールドの短い名前。  
  
 bstrType  
 フィールドの型。  
  
 dwModifiers  
 フラグの組み合わせ、 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)フィールドを表す列挙体。  
  
## <a name="remarks"></a>Remarks  
 この構造体に渡される、 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)メソッドでいっぱいになった場所。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)