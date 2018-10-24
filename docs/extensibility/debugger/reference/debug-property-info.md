---
title: DEBUG_PROPERTY_INFO |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- DEBUG_PROPERTY_INFO
helpviewer_keywords:
- DEBUG_PROPERTY_INFO structure
ms.assetid: 5a085d18-62c6-4740-b9e9-3f5db6bfdf7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612865d08142a56b2908707839ad66b60ea2de9f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847098"
---
# <a name="debugpropertyinfo"></a>DEBUG_PROPERTY_INFO
デバッグ プロパティについてを説明します。  
  
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
 フラグの組み合わせ、 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)どのフィールドに入力を指定する列挙体。  
  
 bstrFullName  
 プロパティの完全名。  
  
 bstrName  
 コンテキスト内でプロパティ名。  
  
 bstrType  
 書式設定された文字列としてプロパティの型。  
  
 bstrValue  
 書式設定された文字列としてプロパティ値です。  
  
 プロパティ  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)この構造体で表されるオブジェクト。  
  
 dwAttrib  
 フラグの組み合わせ、 [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)このプロパティの属性を説明する列挙です。  
  
## <a name="remarks"></a>Remarks  
 プロパティは、名前、型、および値を持つ階層的な性質のオブジェクトです。 たとえば、プロパティには、ローカル変数、パラメーター、ウォッチ変数と式、およびレジスタを記述できます。  
  
 この構造体に渡される、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッドでいっぱいになった場所。 この構造体がこの構造体からの一覧の一部としても返されます、 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)インターフェイスをさらへの呼び出しから返される、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)と[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
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