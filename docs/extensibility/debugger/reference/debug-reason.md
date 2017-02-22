---
title: "DEBUG_REASON | Microsoft Docs"
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
  - "DEBUG_REASON"
helpviewer_keywords: 
  - "DEBUG_REASON 列挙型"
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_REASON
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスはデバッグに開始理由を指定します。  
  
## 構文  
  
```cpp#  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```c#  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### パラメーター  
 DEBUG\_REASON\_ERROR  
 意図的にエラーが他の理由が収まらない場合\) 発生しました。これは既定の条件として使用されます。  
  
 DEBUG\_REASON\_USER\_LAUNCHED  
 プロセスがユーザー要求で起動されます。  
  
 DEBUG\_REASON\_USER\_ATTACHED  
 既に実行中のプロセスがユーザーによって追加されました。  
  
 DEBUG\_REASON\_AUTO\_ATTACHED  
 プロセスが自動的に起動時にアタッチされています。  
  
 DEBUG\_REASON\_CAUSALITY  
 プロセスは Just\-In\-Time デバッグ イベントが原因 \(JIT\) です。  
  
## 解説  
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) のメソッドから返される値。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)