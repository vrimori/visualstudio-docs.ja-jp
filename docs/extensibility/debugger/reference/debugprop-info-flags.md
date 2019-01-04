---
title: DEBUGPROP_INFO_FLAGS |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9046ab771ab4b0c2734c125f2ba17b86f57a09f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987467"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
デバッグ プロパティ オブジェクトを取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
typedef DWORD DEBUGPROP_INFO_FLAGS;  
```  
  
```csharp  
public enum enum_DEBUGPROP_INFO_FLAGS {   
   DEBUGPROP_INFO_FULLNAME          = 0x00000001,  
   DEBUGPROP_INFO_NAME              = 0x00000002,  
   DEBUGPROP_INFO_TYPE              = 0x00000004,  
   DEBUGPROP_INFO_VALUE             = 0x00000008,  
   DEBUGPROP_INFO_ATTRIB            = 0x00000010,  
   DEBUGPROP_INFO_PROP              = 0x00000020,  
   DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,  
   DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,  
   DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,  
   DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000  
   DEBUGPROP_INFO_NONE              = 0x00000000,  
   DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |  
                                      DEBUGPROP_INFO_NAME |  
                                      DEBUGPROP_INFO_TYPE |  
                                      DEBUGPROP_INFO_VALUE,  
   DEBUGPROP_INFO_ALL               = 0xffffffff  
};  
```  
  
## <a name="members"></a>メンバー  
 DEBUGPROP_INFO_FULLNAME  
 初期化/使用、`bstrFullName`フィールド。  
  
 DEBUGPROP_INFO_NAME  
 初期化/使用、`bstrName`フィールド。  
  
 DEBUGPROP_INFO_TYPE  
 初期化/使用、`bstrType`フィールド。  
  
 DEBUGPROP_INFO_VALUE  
 初期化/使用、`bstrValue`フィールド。  
  
 DEBUGPROP_INFO_ATTRIB  
 初期化/使用、`dwAttrib`フィールド。  
  
 DEBUGPROP_INFO_PROP、  
 初期化/使用、`pProperty`フィールドを含む、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)インターフェイス。  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 [値] フィールドは、この種類のオブジェクトの使用可能な場合は、自動拡張値を含める必要がありますを指定します。  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 非推奨。  
  
 DEBUGPROP_INFO_VALUE_RAW  
 任意の見た目を整理できます値またはメンバーを返さない (つまり、値はフォーマットされません)。  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 特別な合成された値は返されません (たとえば、呼び出さないでください`ToString()`値を生成するオブジェクト)。  
  
 DEBUGPROP_INFO_NONE  
 フラグが設定されていないことを指定します。  
  
 DEBUGPROP_INFO_STANDARD  
 初期化/使用、 `dwAttrib`、 `bstrName`、 `bstrType`、および`bstrValue`フィールド。  
  
 DEBUGPROP_INFO_All  
 すべてのフラグのマスクを示します。  
  
## <a name="remarks"></a>Remarks  
 これらの値を渡す、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)、および[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)メソッドを初期化するフィールドを示すために、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体。  
  
 これらの値の使用も、`dwFields`のメンバー、`DEBUG_PROPERTY_INFO`構造が返される構造体のフィールドが使用し、有効なときは、構造体。  
  
 これらの値は、演算と組み合わせることがあります`OR`します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)