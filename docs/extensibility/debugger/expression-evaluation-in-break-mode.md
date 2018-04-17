---
title: 中断モードでの式の評価 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66c69d6dc3dbce328e519f6d078e0aa4a5208ca0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluation-in-break-mode"></a>中断モードでの式の評価
次に、デバッガーが中断モードであり、式の評価を実施する必要があるときに発生するプロセスについて説明します。  
  
## <a name="expression-evaluation-process"></a>式の評価プロセス  
 式の評価に関係する基本的な手順を次に示します。  
  
1.  セッションのデバッグ マネージャー (SDM) を呼び出す[IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)式コンテキスト インターフェイスを取得する[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)です。  
  
2.  SDM を呼び出して[IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)解析する文字列を使用します。  
  
3.  ParseText が S_OK を返さない場合は、エラーの原因が返されます。  
  
     それ以外の場合-  
  
     ParseText は S_OK を返す場合、SDM 呼び出すことができますし、いずれかの[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)解析された式から、最終的な値を取得します。  
  
    -   使用されている場合`IDebugExpression2::EvaluateSync`評価の進行中のプロセスが通信するために、指定されたコールバック インターフェイスを使用します。 最終的な値が返されます、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスです。  
  
    -   使用されている場合`IDebugExpression2::EvaluateAsync`評価の進行中のプロセスが通信するために、指定されたコールバック インターフェイスを使用します。 評価が完了したら、EvaluateAsync 送信、 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)コールバックを介して、インターフェイスです。 このイベント インターフェイスでの最終的な値を取得できます[GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)です。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのイベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)