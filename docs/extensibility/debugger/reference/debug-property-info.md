---
title: "DEBUG_PROPERTY_INFO |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 3c1ce8a931ca8687056fcf161d78b7e40260e15f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
デバッグのプロパティに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct tagDEBUG_PROPERTY_INFO {   
   DEBUGPROP_INFO_FLAGS dwValidFields;  
   BSTR                 bstrFullName;  
   BSTR                 bstrName;  
   BSTR                 bstrType;  
   BSTR                 bstrValue;  
   IDebugProperty2*     pProperty;  
   DBG_ATTRIB_FLAGS     dwAttrib;  
} DEBUG_PROPERTY_INFO;  
```  
  
```csharp  
public struct DEBUG_PROPERTY_INFO {   
   public uint            dwValidFields;  
   public string          bstrFullName;  
   public string          bstrName;  
   public string          bstrType;  
   public string          bstrValue;  
   public IDebugProperty2 pProperty;  
   public ulong           dwAttrib;  
};  
```  
  
## <a name="members"></a>メンバー  
 dwValidFields  
 フラグの組み合わせ、 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)のどのフィールドが入力を指定する列挙です。  
  
 bstrFullName  
 プロパティの完全名。  
  
 bstrName  
 コンテキスト内でプロパティ名。  
  
 bstrType  
 書式設定された文字列としてプロパティの型。  
  
 bstrValue  
 書式設定された文字列としてプロパティ値です。  
  
 プロパティ  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)この構造体で記述するオブジェクト。  
  
 dwAttrib  
 フラグの組み合わせ、 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)このプロパティの属性を説明する列挙です。  
  
## <a name="remarks"></a>コメント  
 プロパティは、名前、型、および値を持つ階層的な性質のオブジェクトです。 たとえば、プロパティには、ローカル変数、パラメーター、変数のウォッチと式、およびレジスタを記述できます。  
  
 この構造体に渡される、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)で塗り分けはメソッドです。 この構造体がこの構造体からのリストの一部としても返されます、 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)インターフェイス、さらへの呼び出しから返される、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)と[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
