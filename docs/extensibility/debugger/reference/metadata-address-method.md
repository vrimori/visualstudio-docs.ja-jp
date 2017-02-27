---
title: "METADATA_ADDRESS_METHOD | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "METADATA_ADDRESS_METHOD"
helpviewer_keywords: 
  - "METADATA_ADDRESS_METHOD 構造体"
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# METADATA_ADDRESS_METHOD
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体はクラスのメソッドのアドレスを表します。  
  
## 構文  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```c#  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## 用語  
 tokMethod  
 メソッドの ID。  
  
 \[C\+\+\] `_mdToken` は32 ビット `int` の `typedef` です。  
  
 dwOffset  
 クラスの先頭からこのメソッドへのオフセット。オブジェクトの vtable へのオフセットを表すことができます。  
  
 dwVersion  
 メソッドのバージョン \(この値はシンボルのプロバイダーによって異なります\)。  
  
## 解説  
 この構造は `DEBUG_ADDRESS_UNION` の構造体の `dwKind` のフィールドが `ADDRESS_KIND_METHOD` \([ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) の列挙値\) に設定されている場合 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) の構造の共用体の一部です。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)