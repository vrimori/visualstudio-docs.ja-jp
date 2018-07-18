---
title: 式を評価する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102793"
---
# <a name="evaluating-expressions"></a>式を評価します。
式は、[自動変数]、ウォッチ、[クイック ウォッチ]、またはイミディ エイト ウィンドウから渡される文字列から作成されます。 式を評価するときに、変数または引数とその値の型と名前を含む印刷可能な文字列を生成します。 この文字列は、対応する IDE のウィンドウに表示されます。  
  
## <a name="implementation"></a>実装  
 プログラムがブレークポイントで停止したときに、式が評価されます。 式自体で表される、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスで、バインディング、および指定された式の評価コンテキスト内で評価の準備が整っている解析された式を表します。 スタック フレームを実装することによって、デバッグ エンジン (DE) を提供する式の評価コンテキストを判断、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイスです。  
  
 ユーザー文字列を指定して、 [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイス、デバッグ エンジン (DE) を取得できます、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス ユーザー文字列を渡すことによって、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドです。 返される IDebugExpression2 インターフェイスには、解析された式評価の準備が整ってにはが含まれています。  
  
 `IDebugExpression2`インターフェイス、デが同期または非同期の式の評価を式の値を取得できますを使用して[IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)または[IDebugExpression2:。EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)です。 変数または引数の型と名前と共に、この値は、表示するための IDE に送信されます。 値、名前、型がで表される、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスです。  
  
 式の評価を有効にする、DE を実装する必要があります、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)と[IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)インターフェイスです。 同期および非同期の評価の実装が必要、 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [スタック フレーム](../../extensibility/debugger/stack-frames.md)   
 [式の評価コンテキスト](../../extensibility/debugger/expression-evaluation-context.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)