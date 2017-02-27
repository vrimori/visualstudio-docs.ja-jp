---
title: "IDebugPendingBreakpoint2::GetBreakpointRequest | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::GetBreakpointRequest"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::GetBreakpointRequest メソッド"
  - "GetBreakpointRequest メソッド"
ms.assetid: cb1e36aa-4302-455c-98fb-6638a1ef5c46
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::GetBreakpointRequest
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

この保留中のブレークポイントの作成に使用されたブレークポイントの要求を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetBreakpointRequest(   
   IDebugBreakpointRequest2** ppBPRequest  
);  
```  
  
```c#  
int GetBreakpointRequest(   
   out IDebugBreakpointRequest2 ppBPRequest  
);  
```  
  
#### パラメーター  
 `ppBPRequest`  
 \[入力\] [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) を表すオブジェクトをこの保留中のブレークポイントの作成に使用されたブレークポイントの要求返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  ブレークポイントが削除された `E_BP_DELETED` を返します。  
  
## 参照  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)