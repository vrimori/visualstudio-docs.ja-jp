---
title: 式の評価 (Visual Studio Debugging SDK) |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bdd8937963175ffe0e8cadbfe2f6653b16a1f5a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888726"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>式の評価 (Visual Studio Debugging SDK)
中断モード中に IDE がいくつかのプログラム変数に関連する単純な式を評価する必要があります。 評価を行うためには、デバッグ エンジン (DE) は解析し、IDE のウィンドウの 1 つに入力された式を評価する必要があります。 
  
 式を作成、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドと、その結果によって表される[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス。  
  
 **IDebugExpression2** DE および呼び出しによってインターフェイスが実装されているその**EvalAsync**を返すメソッドを[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスを表示するために、IDE、IDE で式の評価の結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)に式の値を格納するために使用する構造体を返します、**ウォッチ**ウィンドウに、**ローカル**ウィンドウ。  
  
 デバッグ パッケージまたはセッション デバッグ マネージャー (SDM) を呼び出す[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)または[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)を表すインターフェイス評価の結果。 `IDebugProperty2` 名前、種類、および式の値を返すメソッドがあります。 この情報は、さまざまなデバッガー ウィンドウに表示されます。  
  
## <a name="using-expression-evaluation"></a>式の評価を使用します。  
 式の評価を使用することを実装する必要があります、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドとそのすべてのメソッドの[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスを次の表に示すようにします。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|非同期的に式を評価します。|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|非同期の式の評価を終了します。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同期的に式を評価します。|  
  
 同期および非同期の評価では、実装する必要があります、 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。 非同期の式の評価の実装が必要[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)