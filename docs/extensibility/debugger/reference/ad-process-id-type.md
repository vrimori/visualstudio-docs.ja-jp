---
title: "AD_PROCESS_ID_TYPE | Microsoft Docs"
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
  - "AD_PROCESS_ID_TYPE"
helpviewer_keywords: 
  - "AD_PROCESS_ID_TYPE 列挙型"
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

[AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) の構造のプロセス ID を解釈する方法を指定します。  
  
## 構文  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```c#  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## メンバー  
 AD\_PROCESS\_ID\_SYSTEM  
 プロセス ID はシステム識別子です。  [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) の構造体の `ProcessId.dwProcessId` のフィールドを使用します。  
  
 AD\_PROCESS\_ID\_GUID  
 プロセス ID は GUID です。  `AD_PROCESS_ID` の構造体の `ProcessId.guidProcessId` のフィールドを使用します。  
  
## 解説  
 構造体に含まれているプロセス ID の種類を識別するために [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md) の構造体のメンバー `ProcessIdType` に使用されます。  構造体の `ProcessId` の共用体を解釈する方法を示します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)