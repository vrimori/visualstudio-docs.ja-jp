---
title: "式の評価 (Visual Studio SDK のデバッグ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ed0e494cc0efd48ea3c22d9fd881aafec42a984b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>式の評価 (Visual Studio SDK のデバッグ)
IDE は、中断モード中に、プログラムのいくつかの変数を含む単純な式を評価できる必要があります。 これを実現するには、デバッグ エンジン (DE) できる必要がありますを解析し、IDE のウィンドウの 1 つに入力した式を評価します。  
  
 使用して式を作成、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドとは、結果として得られるで表された[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスです。  
  
 **IDebugExpression2** DE および呼び出しによってインターフェイスが実装されているその**EvalAsync**を返すメソッドを[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスを表示するために、IDE に、IDE で式の評価の結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [ウォッチ] ウィンドウ、または [ローカル] ウィンドウに式の値の配置に使用できる構造体を返します。  
  
 デバッグ パッケージまたはセッション デバッグ マネージャー (SDM) を呼び出す[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)または[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)を表すインターフェイス評価の結果。 `IDebugProperty2`名前、型、および式の値を返すメソッドがあります。 この情報は、さまざまなデバッガー ウィンドウに表示されます。  
  
## <a name="using-expression-evaluation"></a>式の評価を使用します。  
 式の評価を使用する必要がありますを実装する、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドおよびすべてのメソッド、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス、次の表に示すようにします。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|非同期的に式を評価します。|  
|[中止](../../extensibility/debugger/reference/idebugexpression2-abort.md)|非同期の式の評価を終了します。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同期的に式を評価します。|  
  
 同期および非同期の評価の実装が必要、 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッドです。 非同期の式の評価の実装が必要[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)です。  
  
## <a name="see-also"></a>参照  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)