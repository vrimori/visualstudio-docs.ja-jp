---
title: "STEPKIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STEPKIND"
helpviewer_keywords: 
  - "STEPKIND 列挙型"
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# STEPKIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ステップについての種類を指定します。  
  
## 構文  
  
```cpp#  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```c#  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## メンバー  
 STEP\_INTO  
 関数にステップ インします。  
  
 STEP\_OVER  
 関数をステップ オーバーします。  
  
 STEP\_OUT  
 関数にステップ インします。  
  
 STEP\_BACKWARDS  
 逆方向の関数について。  
  
## 解説  
 [ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md) のメソッドに引数として渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md)