---
title: "IDebugStackFrame2::GetThread | Microsoft Docs"
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
  - "IDebugStackFrame2::GetThread"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetThread"
ms.assetid: cbeef85b-3dd7-4f97-adc2-c4d197d979fc
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッドのスタック フレームに関連付けられているを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetThread (   
   IDebugThread2** ppThread  
);  
```  
  
```c#  
int GetThread (   
   out IDebugThread2 ppThread  
);  
```  
  
#### パラメーター  
 `ppThread`  
 \[入力\] スレッドを表す [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) のオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)