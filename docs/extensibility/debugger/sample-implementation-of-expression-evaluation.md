---
title: "式の評価の実装のサンプル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式エバリュエーター"
  - "[デバッグ SDK] の式エバリュエーターのデバッグ"
  - "式の評価の例"
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 式の評価の実装のサンプル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 **ウォッチ** ウィンドウの式、Visual Studio 呼び出し [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) を生成する、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) オブジェクトです。`IDebugExpressionContext2::ParseText` 式エバリュエーター \(EE\) と呼び出しをインスタンス化 [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) させることが、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) オブジェクトです。  
  
 この実装の `IDebugExpressionEvaluator::Parse` 次のタスクを実行します。  
  
1.  \[C\+\+ のみ\]エラーを検索する式を解析します。  
  
2.  クラスをインスタンス化 \(と呼ばれる `CParsedExpression` この例では\) を実装する、 `IDebugParsedExpression` インターフェイスし、クラスに解析する式を格納します。  
  
3.  返します。、 `IDebugParsedExpression` からインターフェイス、 `CParsedExpression` オブジェクトです。  
  
> [!NOTE]
>  次の例および MyCEE サンプルでは、式エバリュエーターで分離されていない、その評価から解析します。  
  
## マネージ コード  
 これは、実装の `IDebugExpressionEvaluator::Parse` マネージ コードにします。 このバージョンのメソッドは、文字列の解析に延期に注意してください [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) を解析するコードは、同時にも評価 \(を参照してください [\[ウォッチ式を評価します。](../../extensibility/debugger/evaluating-a-watch-expression.md)\)。  
  
```c#  
namespace EEMC { public class CParsedExpression : IDebugParsedExpression { public HRESULT Parse( string                 expression, uint                   parseFlags, uint                   radix, out string                 errorMessage, out uint                   errorPosition, out IDebugParsedExpression parsedExpression) { errorMessage = ""; errorPosition = 0; parsedExpression = new CParsedExpression(parseFlags, radix, expression); return COM.S_OK; } } }  
```  
  
## アンマネージ コード  
 これは、実装の `IDebugExpressionEvaluator::Parse` アンマネージ コードにします。 このメソッドは、ヘルパー関数を呼び出したり `Parse`, 、式およびエラーのチェックを解析するが、このメソッドには、結果の値が無視されます。 正式な評価はまで延期 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) が評価されるときに、式が解析される \(を参照してください [\[ウォッチ式を評価します。](../../extensibility/debugger/evaluating-a-watch-expression.md)\)。  
  
```cpp#  
STDMETHODIMP CExpressionEvaluator::Parse( in    LPCOLESTR                 pszExpression, in    PARSEFLAGS                flags, in    UINT                      radix, out   BSTR                     *pbstrErrorMessages, inout UINT                     *perrorCount, out   IDebugParsedExpression  **ppparsedExpression ) { if (pbstrErrorMessages == NULL) return E_INVALIDARG; else *pbstrErrormessages = 0; if (pparsedExpression == NULL) return E_INVALIDARG; else *pparsedExpression = 0; if (perrorCount == NULL) return E_INVALIDARG; HRESULT hr; // Look for errors in the expression but ignore results hr = ::Parse( pszExpression, pbstrErrorMessages ); if (hr != S_OK) return hr; CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression ); if (!pparsedExpr) return E_OUTOFMEMORY; hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression, reinterpret_cast<void**>(ppparsedExpression) ); pparsedExpr->Release(); return hr; }  
```  
  
## 参照  
 [\[ウォッチ\] ウィンドウの式を評価します。](../Topic/Evaluating%20a%20Watch%20Window%20Expression.md)   
 [\[ウォッチ式を評価します。](../../extensibility/debugger/evaluating-a-watch-expression.md)