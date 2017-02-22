---
title: "ADDRESS_KIND | Microsoft Docs"
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
  - "ADDRESS_KIND"
helpviewer_keywords: 
  - "ADDRESS_KIND 列挙型"
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

アドレスの種類を指定します。  
  
## 構文  
  
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
  
```c#  
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
  
## 用語  
 ADDRESS\_KIND\_NATIVE  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md) の構造によって表されるネイティブ アドレス。  
  
 ADDRESS\_KIND\_UNMANAGED\_THIS\_RELATIVE  
 アンマネージのアドレス `this` \(Visual Basic では\)`Me` のポインターを基準とする [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) の構造体によって表される。  
  
 ADDRESS\_KIND\_UNMANAGED\_PHYSICAL  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) の構造によって表されるアンマネージの物理アドレス。  
  
 ADDRESS\_KIND\_METHOD  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) の構造によって表されるクラスのメソッド。  
  
 ADDRESS\_KIND\_FIELD  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) の構造で表されるクラスのフィールド。  
  
 ADDRESS\_KIND\_LOCAL  
 アドレスはローカル変数の場合[METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) の構造体によって表されます。  
  
 ADDRESS\_KIND\_PARAM  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) の構造によって表されるメソッドまたは関数パラメーター。  
  
 ADDRESS\_KIND\_ARRAYELEM  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) の構造によって表される配列要素。  
  
 ADDRESS\_KIND\_RETVAL  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) の構造によって表される返します。  
  
## 解説  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) のメソッドできる構造体の共用体を含む構造体の [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)[DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) の構造体。  `DEBUG_ADDRESS_UNION` の構造体の `dwKind` のフィールドは `ADDRESS_KIND` の値を保持し共用体のフィールドを解釈する方法について説明します。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)