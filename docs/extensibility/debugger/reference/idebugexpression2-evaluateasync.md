---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドは式を非同期的に評価されます。  
  
## 構文  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### パラメーター  
 `dwFlags`  
 \[入力\] 式の評価を制御する [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) の列挙体のフラグの組み合わせ。  
  
 `pExprCallback`  
 \[入力\] このパラメーターは null 値は常にです。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  一般的なエラー コードは次のとおりです :  
  
|エラー|Description|  
|---------|-----------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|別の式は現在同時に評価される式の評価はサポートされません。|  
  
## 解説  
 このメソッドは式の評価を呼び出した直後にを返す必要があります。  式が正常に評価されると[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) は [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) または [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) によって提供されるように [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のイベント コールバックに渡さない場合があります。  
  
## 使用例  
 次の例に `CExpression` の単純なオブジェクトに対してこのメソッドを実装する方法を実装するインターフェイスの [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) 示します。  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## 参照  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)