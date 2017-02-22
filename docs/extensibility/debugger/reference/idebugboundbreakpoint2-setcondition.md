---
title: "IDebugBoundBreakpoint2::SetCondition | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition メソッド"
  - "IDebugBoundBreakpoint2::SetCondition メソッド"
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この条件がバインド ブレークポイントに関連付けられている変更または設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### パラメーター  
 `bpCondition`  
 \[入力\] [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) の条件を示す列挙体の値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  バインドされたブレークポイントのオブジェクトの状態が `BPS_DELETED` \([BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) の列挙型の一部\) に設定されて `E_BP_DELETED` を返します。  
  
## 解説  
 このブレークポイントが関連付けられている条件が失われます。  
  
## 参照  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)