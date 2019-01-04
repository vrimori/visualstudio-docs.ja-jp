---
title: DEBUG_ADDRESS_UNION |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUG_ADDRESS_UNION
helpviewer_keywords:
- DEBUG_ADDRESS_UNION union
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a6a9ddc8806bdbba5a583e16657c3c5126a8992
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947206"
---
# <a name="debugaddressunion"></a>DEBUG_ADDRESS_UNION
アドレスのさまざまな種類をについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS_UNION {  
   ADDRESS_KIND dwKind;  
   union {  
      NATIVE_ADDRESS                  addrNative;  
      UNMANAGED_ADDRESS_THIS_RELATIVE addrThisRel;  
      UNMANAGED_ADDRESS_PHYSICAL      addrUPhysical;  
      METADATA_ADDRESS_METHOD         addrMethod;  
      METADATA_ADDRESS_FIELD          addrField;  
      METADATA_ADDRESS_LOCAL          addrLocal;  
      METADATA_ADDRESS_PARAM          addrParam;  
      METADATA_ADDRESS_ARRAYELEM      addrArrayElem;  
      METADATA_ADDRESS_RETVAL         addrRetVal;  
      DWORD                           unused;  
   } addr;  
} DEBUG_ADDRESS_UNION;  
```  
  
```csharp  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## <a name="terms"></a>用語  
 dwKind  
 値、 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)列挙体、共用体を解釈する方法を指定します。  
  
 addr.addrNative  
 [C++ のみ]含まれています、 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)場合構造体`dwKind`ADDRESS_KIND_NATIVE を = です。  
  
 addr.addrThisRel  
 [C++ のみ]含まれています、[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)場合構造体`dwKind`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE を = です。  
  
 addr.addUPhysical  
 [C++ のみ]含まれています、[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)場合構造体`dwKind`ADDRESS_KIND_UNMANAGED_PHYSICAL を = です。  
  
 addr.addrMethod  
 [C++ のみ]含まれています、[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)場合構造体`dwKind`ADDRESS_KIND_METHOD を = です。  
  
 addr.addrField  
 [C++ のみ]含まれています、[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)場合構造体`dwKind`ADDRESS_KIND_FIELD を = です。  
  
 addr.addrLocal  
 [C++ のみ]含まれています、[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)場合構造体`dwKind`ADDRESS_KIND_LOCAL を = です。  
  
 addr.addrParam  
 [C++ のみ]含まれています、[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)場合構造体`dwKind`ADDRESS_KIND_PARAM を = です。  
  
 addr.addrArrayElem  
 [C++ のみ]含まれています、[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)場合構造体`dwKind`ADDRESS_KIND_ARRAYELEM を = です。  
  
 addr.addrRetVal  
 [C++ のみ]含まれています、[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)場合構造体`dwKind`ADDRESS_KIND_RETVAL を = です。  
  
 addr.unused  
 [C++ のみ] のパディングです。  
  
 Addr  
 [C++ のみ]共用体の名前。  
  
 unionmember  
 [C#のみ]この値に基づいて、適切な構造体の型にマーシャ リングする必要がある`dwKind`します。 間の関連付けは、「解説」を参照してください`dwKind`と共用体の解釈します。  
  
## <a name="remarks"></a>Remarks  
 この構造体の一部は、 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)構造体し、さまざまな種類のアドレスの数のいずれかを表します (、`DEBUG_ADDRESS`構造体への呼び出しによって入力されます、 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)メソッド)。  
  
 [C#のみ]次の表を解釈する方法を示しています、`unionmember`アドレスの種類ごとのメンバー。 この例では、1 つの種類のアドレスにこれを行う方法を示します。  
  
|`dwKind`|`unionmember` として解釈されます。|  
|--------------|----------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## <a name="example"></a>例  
 この例は、1 つの種類のアドレスを解釈する方法を示しています (`METADATA_ADDRESS_ARRAYELEM`) の`DEBUG_ADDRESS_UNION`構造 (C#)。 残りの要素は、まったく同じ方法で解釈できます。  
  
```csharp  
using System;  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace MyPackage  
{  
    public class MyClass  
    {  
        public void Interpret(DEBUG_ADDRESS_UNION dau)  
        {  
            if (dau.dwKind == (uint)enum_ADDRESS_KIND.ADDRESS_KIND_METADATA_ARRAYELEM)  
            {  
                 METADATA_ADDRESS_ARRAYELEM arrayElem =  
                     (METADATA_ADDRESS_ARRAYELEM)Marshal.PtrToStructure(dau.unionmember,  
                                 typeof(METADATA_ADDRESS_ARRAYELEM));  
            }  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)