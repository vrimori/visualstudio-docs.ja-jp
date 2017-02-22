---
title: "dwTYPE_KIND | Microsoft Docs"
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
  - "dwTYPE_KIND"
helpviewer_keywords: 
  - "dwTYPE_KIND 列挙型"
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[IDebugField](../../../extensibility/debugger/reference/idebugfield.md) のオブジェクト型を解釈する方法を指定します。  
  
## 構文  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```c#  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### パラメーター  
 TYPE\_KIND\_METADATA  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) の共用体は [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md) の構造として解釈されます。  
  
 TYPE\_KIND\_PDB  
 `TYPE_INFO` の共用体は [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md) の構造として解釈されます。  
  
 TYPE\_KIND\_BUILT  
 `TYPE_INFO` の共用体は [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md) の構造として解釈されます。  
  
## 解説  
 この列挙体の値は [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) の構造体の `dwKind` のフィールドに表示され確認するには `type` のクラスを解釈する方法を使用します。  `TYPE_INFO` の構造は [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) メソッドの呼び出しによって返されます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)