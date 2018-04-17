---
title: DEBUGPROP_INFO_FLAGS |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 1d9ecaab348ca69a792c39a8cb74e998d8f3a6aa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Debug プロパティ オブジェクトの概要を取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_DEBUGPROP_INFO_FLAGS {   
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
public enum enum_DEBUGPROP_INFO_FLAGS {   
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
 初期化/を使用して、`bstrFullName`フィールドです。  
  
 DEBUGPROP_INFO_NAME  
 初期化/を使用して、`bstrName`フィールドです。  
  
 DEBUGPROP_INFO_TYPE  
 初期化/を使用して、`bstrType`フィールドです。  
  
 DEBUGPROP_INFO_VALUE  
 初期化/を使用して、`bstrValue`フィールドです。  
  
 DEBUGPROP_INFO_ATTRIB  
 初期化/を使用して、`dwAttrib`フィールドです。  
  
 DEBUGPROP_INFO_PROP、  
 初期化/を使用して、`pProperty`を含むフィールドを[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスです。  
  
 DEBUGPROP_INFO_VALUE_AUTOEXPAND  
 [値] フィールドは、この種類のオブジェクトの使用可能な場合は、自動拡張値を含める必要がありますを指定します。  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 使用しないでください。  
  
 DEBUGPROP_INFO_VALUE_RAW  
 Beautified 値やメンバーは返しません (つまり、値はフォーマットされません)。  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 任意の特殊な合成された値を返さない (たとえば、呼び出す必要はありません`ToString()`値を生成するオブジェクトに)。  
  
 DEBUGPROP_INFO_NONE  
 フラグが設定されていないことを指定します。  
  
 DEBUGPROP_INFO_STANDARD  
 初期化/を使用して、 `dwAttrib`、 `bstrName`、 `bstrType`、および`bstrValue`フィールドです。  
  
 DEBUGPROP_INFO_All  
 すべてのフラグのマスクを示します。  
  
## <a name="remarks"></a>コメント  
 これらの値が渡される、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)、および[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)することを示すフィールドを初期化するメソッド、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体。  
  
 これらの値がの使用も、`dwFields`のメンバー、`DEBUG_PROPERTY_INFO`を示すために、構造体のフィールドに使用されると有効な構造が返される構造体。  
  
 これらの値は、ビットごとと組み合わせること`OR`です。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)   
 [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)