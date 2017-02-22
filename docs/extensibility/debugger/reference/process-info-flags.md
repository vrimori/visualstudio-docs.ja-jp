---
title: "PROCESS_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PROCESS_INFO_FLAGS"
helpviewer_keywords: 
  - "PROCESS_INFO_FLAGS 列挙型"
ms.assetid: 696951ce-701a-40c2-ac8c-b897f3aae6e2
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# PROCESS_INFO_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスのプロパティを記述したり指定します。  
  
## 構文  
  
```cpp#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
typedef DWORD PROCESS_INFO_FLAGS;  
```  
  
```c#  
enum enum_PROCESS_INFO_FLAGS {   
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,  
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,  
   PIFLAG_PROCESS_STOPPED   = 0x00000004,  
   PIFLAG_PROCESS_RUNNING   = 0x00000008,  
};  
```  
  
## メンバー  
 PIFLAG\_SYSTEM\_PROCESS  
 プロセスがシステム プロセスであることを示します。  
  
 PIFLAG\_DEBUGGER\_ATTACHED  
 プロセスにデバッガーを使用してデバッグことを示します。  これは [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] のデバッガーであるかは他のデバッガーなど読み込まれた WinDbg である場合があります。  
  
 PIFLAG\_PROCESS\_STOPPED  
 プロセスが停止していることを示します。  `PIFLAG_DEBUGGER_ATTACHED` は指定した場合にのみ有効です。  の以降で使用できます [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]。  
  
 PIFLAG\_PROCESS\_RUNNING  
 プロセスが実行されていることを示します。  `PIFLAG_DEBUGGER_ATTACHED` は指定した場合にのみ有効です。  の以降で使用できます [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]。  
  
## 解説  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md) の構造体のメンバー `Flags` に使用されます。  
  
 これらのフラグはビットごと `OR` に組み合わせることがあります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)