---
title: "BP_CONDITION | Microsoft Docs"
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
  - "BP_CONDITION"
helpviewer_keywords: 
  - "BP_CONDITION 構造体"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

ブレークポイントが発生する条件を説明します。  
  
## 構文  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## メンバー  
 `pThread`  
 ブレークポイントを含むアプリケーションのアクティブなスレッドを表すオブジェクトの [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)。  
  
 `styleCondition`  
 ブレークポイント条件のスタイルを記述する [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) の列挙体の値。  
  
 `bstrContext`  
 ブレークポイントの位置。  
  
 `bstrCondition`  
 ブレークポイントが条件。  
  
 `nRadix`  
 数値情報の評価で使用する基数。  
  
## 解説  
 この構造は [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) と [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) の構造体のメンバーです。  
  
 この構造体には[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) と [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) のメソッドにパラメーターとして渡します。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)