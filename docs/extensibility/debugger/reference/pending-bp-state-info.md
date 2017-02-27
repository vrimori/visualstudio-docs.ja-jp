---
title: "PENDING_BP_STATE_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PENDING_BP_STATE_INFO"
helpviewer_keywords: 
  - "PENDING_BP_STATE_INFO 構造体"
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

コード位置にバインドする準備が整ったブレークポイントの状態に関する情報を格納します。  
  
## 構文  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```c#  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## メンバー  
 state  
 保留中のブレークポイントの [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) の状態を指定する列挙体の値。  
  
 フラグ  
 ブレークポイントが仮想化されているかどうかを指定する [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) の列挙体のフラグの組み合わせ。  
  
## 解説  
 この構造が表示される [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../Topic/IDebugPendingBreakpoint2::GetState.md)   
 [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)