---
title: "THREADSTATE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "THREADSTATE"
helpviewer_keywords: 
  - "THREADSTATE 列挙体"
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# THREADSTATE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッドの状態を指定します。  
  
## 構文  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```c#  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## メンバー  
 THREADSTATE\_RUNNING  
 スレッドが実行されていることを示します。  
  
 THREADSTATE\_STOPPED  
 スレッドがブレークポイントで停止することを示します。  
  
 THREADSTATE\_FRESH  
 スレッドが作成されたかがまだ実行中のコードではないことを示します。  
  
 THREADSTATE\_DEAD  
 スレッドがデッド キーであることを示します。  
  
 THREADSTATE\_FROZEN  
 スレッドが固定されることを示します \(実行は実行できません\)。  
  
## 解説  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) の構造体の `dwThreadState` の各フィールドに使用されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [列挙](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)