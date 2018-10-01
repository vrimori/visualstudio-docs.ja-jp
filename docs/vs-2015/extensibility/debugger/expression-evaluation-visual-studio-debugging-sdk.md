---
title: 式の評価 (Visual Studio Debugging SDK) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd5fb9ac88b2535c897978cdd63f9cf0716d53a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538593"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>式の評価 (Visual Studio Debugging SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[式の評価 (Visual Studio Debugging SDK)](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk)します。  
  
IDE は、中断モード中に、プログラムのいくつかの変数を含む単純な式を評価できる必要があります。 これを実現するには、デバッグ エンジン (DE) が解析および IDE のウィンドウの 1 つに入力された式を評価することがあります。  
  
 使用して式を作成、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドとは、その結果では表さ[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイス。  
  
 **IDebugExpression2** DE および呼び出しによってインターフェイスが実装されているその**EvalAsync**を返すメソッドを[IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスを表示するために、IDE、IDE で式の評価の結果。 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)をウォッチ ウィンドウまたは [ローカル] ウィンドウに式の値を使用できる構造体を返します。  
  
 デバッグ パッケージまたはセッション デバッグ マネージャー (SDM) を呼び出す[IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)または[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)を取得する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)を表すインターフェイス評価の結果。 `IDebugProperty2` 名前、種類、および式の値を返すメソッドがあります。 この情報は、さまざまなデバッガー ウィンドウに表示されます。  
  
## <a name="using-expression-evaluation"></a>式の評価を使用します。  
 式の評価を使用することを実装する必要があります、 [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)メソッドとそのすべてのメソッドの[IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスを次の表に示すようにします。  
  
|メソッド|説明|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|非同期的に式を評価します。|  
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|非同期の式の評価を終了します。|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|同期的に式を評価します。|  
  
 同期および非同期の評価の実装が必要に、 [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)メソッド。 非同期の式の評価の実装が必要[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)

