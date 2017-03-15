---
title: "DEBUGPROP_INFO_FLAGS |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c5b749cffbc05fcc3fa6c533dc4bb3bdcd1ad1c0
ms.lasthandoff: 02/22/2017

---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Debug プロパティ オブジェクトの概要を取得するには、どのような情報を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
  
```c#  
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
 指定値 フィールドには、この型のオブジェクトで使用可能な場合は、自動拡張値を含める必要があります。  
  
 DEBUGPROP_INFO_VALUE_NOFUNCEVAL  
 使用しないでください。  
  
 DEBUGPROP_INFO_VALUE_RAW  
 値の見た目を整理やメンバーは返されません (つまり、値はフォーマットされません)。  
  
 DEBUGPROP_INFO_VALUE_NO_TOSTRING  
 特殊な合成された値が返されません (たとえば、呼び出す必要はありません`ToString()`値を生成するオブジェクト)。  
  
 DEBUGPROP_INFO_NONE  
 フラグが設定されていないことを指定します。  
  
 DEBUGPROP_INFO_STANDARD  
 初期化/を使用して、 `dwAttrib`、 `bstrName`、 `bstrType`、および`bstrValue`フィールドです。  
  
 DEBUGPROP_INFO_All  
 すべてのフラグのマスクを示します。  
  
## <a name="remarks"></a>コメント  
 これらの値が渡される、 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)、 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)、および[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)メソッドを初期化するフィールドを示す、 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)構造体。  
  
 これらの値がの使用も、`dwFields`のメンバー、`DEBUG_PROPERTY_INFO`構造体、構造体が返される構造体のフィールドが使用し、有効なことを示します。  
  
 これらの値は、演算と組み合わせることも`OR`です。  
  
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
