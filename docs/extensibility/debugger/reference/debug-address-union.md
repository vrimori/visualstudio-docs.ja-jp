---
title: "DEBUG_ADDRESS_UNION | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEBUG_ADDRESS_UNION"
helpviewer_keywords: 
  - "DEBUG_ADDRESS_UNION 共用体"
ms.assetid: e3d11aab-de0d-4109-b5dc-11e07e64382d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS_UNION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

アドレスの種類について説明します。  
  
## 構文  
  
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
  
```c#  
public struct DEBUG_ADDRESS_UNION {  
   public ADDRESS_KIND dwKind;  
   public IntPtr       unionmember;  
}  
```  
  
## 用語  
 dwKind  
 指定する [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) の列挙値の共用体を解釈する方法を示します。  
  
 addr.addrNative  
 \[C\+\+\] [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_NATIVE 含まれています。  
  
 addr.addrThisRel  
 \[C\+\+\][UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE 含まれています。  
  
 addr.addUPhysical  
 \[C\+\+\][UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_UNMANAGED\_PHYSICAL 含まれています。  
  
 addr.addrMethod  
 \[C\+\+\][METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_METHOD 含まれています。  
  
 addr.addrField  
 \[C\+\+\][METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_FIELD 含まれています。  
  
 addr.addrLocal  
 \[C\+\+\][METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_LOCAL 含まれています。  
  
 addr.addrParam  
 \[C\+\+\][METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_PARAM 含まれています。  
  
 addr.addrArrayElem  
 \[C\+\+\][METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_ARRAYELEM 含まれています。  
  
 addr.addrRetVal  
 \[C\+\+\][METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) のみの構造を `dwKind` \= `dwKind``dwKind` ADDRESS\_KIND\_RETVAL 含まれています。  
  
 addr.unused  
 \[C\+\+\] " だけです。  
  
 アドレス  
 \[C\+\+\] のみ共用体の名前。  
  
 unionmember  
 \[C\#\] `dwKind` この値はのみに基づいて適切な構造体の型にマーシャリングする必要があります。  共用体の `dwKind` と解釈間の関連付けについては" 解説 " を参照してください。  
  
## 解説  
 この構造は [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) の構造の一部でありアドレスの一部の 1 を表します \(`DEBUG_ADDRESS` の構造は [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) メソッドの呼び出しによって入力されます\)。  
  
 \[C\# のみそれぞれのアドレスの `unionmember` のメンバーを解釈する方法\] 次の表に示します。  これは1 種類のアドレス用にする方法の例に示します。  
  
|`dwKind`|`unionmember` は型として解釈します|  
|--------------|------------------------------|  
|`ADDRESS_KIND_NATIVE`|[NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)|  
|`ADDRESS_KIND_UNMANAGED_THIS_RELATIVE`|[UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)|  
|`ADDRESS_KIND_UNMANAGED_PHYSICAL`|[UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)|  
|`ADDRESS_KIND_METHOD`|[METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)|  
|`ADDRESS_KIND_FIELD`|[METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)|  
|`ADDRESS_KIND_LOCAL`|[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)|  
|`ADDRESS_KIND_PARAM`|[METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)|  
|`ADDRESS_KIND_ARRAYELEM`|[METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)|  
|`ADDRESS_KIND_RETVAL`|[METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)|  
  
## 使用例  
 この例では1 種類の C\# `DEBUG_ADDRESS_UNION` の構造体のアドレス \(`METADATA_ADDRESS_ARRAYELEM`\) をデコードする方法を示します。  残りの要素は同じように解釈できます。  
  
```c#  
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
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)