---
title: ADDRESS_KIND |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 65e4c103884da28bedfd221e26b159e9e8f98e55
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867424"
---
# <a name="addresskind"></a>ADDRESS_KIND
アドレスの種類を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>用語  
 ADDRESS_KIND_NATIVE  
 によって表される、ネイティブのアドレス、 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)構造体。  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 基準とする非管理対象のアドレスを`this`(`Me` Visual Basic で) ポインターによって表されると、 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)構造体。  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 によって表される、管理されていない物理アドレス、 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)構造体。  
  
 ADDRESS_KIND_METHOD  
 によって表されるクラスのメソッド、 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)構造体。  
  
 ADDRESS_KIND_FIELD  
 によって表されるクラスのフィールド、 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)構造体。  
  
 ADDRESS_KIND_LOCAL  
 アドレスのローカル変数し、で表される、 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)構造体。  
  
 ADDRESS_KIND_PARAM  
 によって表される、メソッドまたは関数パラメーター、 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)構造体。  
  
 ADDRESS_KIND_ARRAYELEM  
 配列の要素によって表される、 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)構造体。  
  
 ADDRESS_KIND_RETVAL  
 によって表される、戻り値、 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)構造体。  
  
## <a name="remarks"></a>Remarks  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)メソッドが返す、 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 、可能な構造体の和集合を含む構造体、 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)構造体。 `dwKind`のフィールド、`DEBUG_ADDRESS_UNION`の保留を構造体、`ADDRESS_KIND`値し、共用体のフィールドを解釈する方法について説明します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)