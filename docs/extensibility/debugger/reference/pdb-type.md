---
title: "PDB_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PDB_TYPE"
helpviewer_keywords: 
  - "PDB_TYPE 構造体"
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# PDB_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この構造体にはPDB ファイルのシンボルから取得したフィールドの種類についての情報を指定します。  
  
## 構文  
  
```cpp#  
typedef struct _tagTYPE_PDB {  
   ULONG32 ulAppDomainID;  
   GUID    guidModule;  
   DWORD   symid;  
} PDB_TYPE;  
```  
  
```c#  
public struct PDB_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public uint symid;  
};  
```  
  
#### パラメーター  
 ulAppDomainID  
 シンボルがアプリケーションの ID。  これはアプリケーションのインスタンスを識別するために使用されます。  
  
 guidModule  
 このフィールドを含むモジュールの GUID。  
  
 symid  
 このフィールドに対応するシンボル ID。  
  
## 解説  
 この構造は [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) の構造の共用体の一部として `TYPE_INFO` の構造体の `dwKind` のフィールドが `TYPE_KIND_PDB` \([dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) の列挙値\) に設定すると表示されます。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE\_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)