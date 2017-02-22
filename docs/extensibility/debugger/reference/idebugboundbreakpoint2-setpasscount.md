---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount メソッド"
  - "IDebugBoundBreakpoint2::SetPassCount メソッド"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

パスの数がこのバインド ブレークポイントに関連付けられている変更または設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### パラメーター  
 `bpPassCount`  
 \[入力\] パスの数を指定する [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) の構造体。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  バインドされたブレークポイントのオブジェクトの状態が `BPS_DELETED` \([BP\_STATE](../../../extensibility/debugger/reference/bp-state.md) の列挙型の一部\) に設定されて `E_BP_DELETED` を返します。  
  
## 解説  
 パスの数はブレークポイントに発生するかを指定します。  現在のパスまたはヒット カウントが [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) のメソッドを呼び出して取得できます。  
  
 このブレークポイントが関連付けられているパスの数は失われます。  
  
## 参照  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)