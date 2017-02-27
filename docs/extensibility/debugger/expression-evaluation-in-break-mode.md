---
title: "中断モードでの式の評価 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断モードでは、式の評価"
  - "[デバッグ SDK] の式の評価のデバッグ"
  - "式の評価、中断モード"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 中断モードでの式の評価
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次にデバッガーが中断モードで式の評価を行う必要があるときに発生するプロセスについて説明します。  
  
## 式の評価の手順  
 これらは式の評価に関連する基本的な手順を示します :  
  
1.  デバッグ セッションのマネージャーは \(SDM\)式のコンテキスト インターフェイス[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) を取得するに [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) を呼び出します。  
  
2.  SDM は解析対象の文字列に [IDebugExpressionContext2:: ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) を呼び出します。  
  
3.  ParseText が S\_OK を返すエラーの原因が返されます。  
  
     \- は  
  
     ParseText が S\_OK を返す場合SDM は解析された式から最終値を取得するに [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) または [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) を呼び出すことができます。  
  
    -   `IDebugExpression2::EvaluateSync` の評価で進行中のプロセスを知らせるのに使用する場合は特定のコールバック インターフェイスが使用されます。  最終値は [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスに返されます。  
  
    -   `IDebugExpression2::EvaluateAsync` の評価で進行中のプロセスを知らせるのに使用する場合は特定のコールバック インターフェイスが使用されます。  評価が終わったらEvaluateAsync はコールバックによって [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) のインターフェイスを送信します。  このイベントのインターフェイスを使用すると最終値は [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) を使用して取得できます。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)