---
title: "UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs"
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
  - "UNMANAGED_ADDRESS_PHYSICAL"
helpviewer_keywords: 
  - "UNMANAGED_ADDRESS_PHYSICAL 構造体"
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# UNMANAGED_ADDRESS_PHYSICAL
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体には物理アドレスを表します。  
  
## 構文  
  
```cpp  
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {  
   ULONGLONG offset;  
} UNMANAGED_ADDRESS_PHYSICAL;  
```  
  
```c#  
public struct UNMANAGED_ADDRESS_PHYSICAL {  
   public ulong offset;  
}  
```  
  
## 用語  
 オフセット  
 物理アドレス空間への 64 ビットのオフセット。  
  
## 解説  
 この構造は `DEBUG_ADDRESS_UNION` の構造体の `dwKind` のフィールドが `ADDRESS_KIND_UNMANAGED_PHYSICAL` \([ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) の列挙値\) に設定されている場合 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) の構造の共用体の一部です。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)