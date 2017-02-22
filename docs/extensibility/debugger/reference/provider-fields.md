---
title: "PROVIDER_FIELDS | Microsoft Docs"
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
  - "PROVIDER_FIELDS"
helpviewer_keywords: 
  - "PROVIDER_FIELDS 列挙型"
ms.assetid: 39631545-2b0e-45b4-978b-d63656484b02
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# PROVIDER_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プログラムのプロバイダーに関連付けられたプロパティを指定します。  
  
## 構文  
  
```cpp#  
enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
typedef DWORD PROVIDER_FIELDS;  
```  
  
```c#  
public enum enum_PROVIDER_FIELDS {  
   PFIELD_PROGRAM_NODES       = 0x01,  
   PFIELD_IS_DEBUGGER_PRESENT = 0x02  
};  
```  
  
## メンバー  
 PFIELD\_PROGRAM\_NODES  
 `ProgramNodes` のフィールドが有効です。  
  
 PFIELD\_IS\_DEBUGGER\_PRESENT  
 `fIsDebuggerPresent` のフィールドが有効です。  
  
## 解説  
 これらの値は [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md) の構造体のメンバーで `Fields` 構造体のフィールドが明示的に設定したかを返します。  
  
 これらの値はビットごと `OR` にまとめることができます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)