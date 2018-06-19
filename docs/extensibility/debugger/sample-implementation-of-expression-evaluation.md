---
title: 式の評価の実装のサンプル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edc31a8bc403f4f6dfcb16847d3cfce5d99b526
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127838"
---
# <a name="sample-implementation-of-expression-evaluation"></a>式の評価の実装のサンプル
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 **ウォッチ**ウィンドウ表現、Visual Studio 呼び出し[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)生成するために、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。 `IDebugExpressionContext2::ParseText` 式エバリュエーター (EE) および呼び出しをインスタンス化[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)を取得する、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。  
  
 この実装`IDebugExpressionEvaluator::Parse`は、次のタスクを実行します。  
  
1.  [C++ のみ]エラーを検索する式を解析します。  
  
2.  クラスをインスタンス化 (と呼ばれる`CParsedExpression`この例では) を実装する、`IDebugParsedExpression`インターフェイスし、クラスに解析される式を格納します。  
  
3.  返します、`IDebugParsedExpression`からインターフェイス、`CParsedExpression`オブジェクト。  
  
> [!NOTE]
>  次の例と MyCEE サンプルでは、式エバリュエーターで分離されていない、その評価から解析します。  
  
## <a name="managed-code"></a>マネージ コード  
 これは、実装の`IDebugExpressionEvaluator::Parse`マネージ コードでします。 このバージョンのメソッドが、解析を行ってを延期ことに注意してください[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を解析するためのコードは、同時にもと評価されると (を参照してください[ウォッチ式を評価する](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT Parse(  
                string                 expression,   
                uint                   parseFlags,  
                uint                   radix,  
            out string                 errorMessage,   
            out uint                   errorPosition,   
            out IDebugParsedExpression parsedExpression)  
        {   
            errorMessage = "";  
            errorPosition = 0;  
  
            parsedExpression =  
                new CParsedExpression(parseFlags, radix, expression);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>アンマネージ コード  
 これは、実装の`IDebugExpressionEvaluator::Parse`アンマネージ コードにします。 このメソッドは、ヘルパー関数を呼び出したり`Parse`、式およびエラーの確認を解析するが、このメソッドには、結果の値が無視されます。 正式な評価の遅延を[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)が評価されるときに、式が解析される (を参照してください[ウォッチ式を評価する](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```cpp  
STDMETHODIMP CExpressionEvaluator::Parse(  
        in    LPCOLESTR                 pszExpression,  
        in    PARSEFLAGS                flags,  
        in    UINT                      radix,  
        out   BSTR                     *pbstrErrorMessages,  
        inout UINT                     *perrorCount,  
        out   IDebugParsedExpression  **ppparsedExpression  
    )  
{  
    if (pbstrErrorMessages == NULL)  
        return E_INVALIDARG;  
    else  
        *pbstrErrormessages = 0;  
  
    if (pparsedExpression == NULL)  
        return E_INVALIDARG;  
    else  
        *pparsedExpression = 0;  
  
    if (perrorCount == NULL)  
        return E_INVALIDARG;  
  
    HRESULT hr;  
    // Look for errors in the expression but ignore results  
    hr = ::Parse( pszExpression, pbstrErrorMessages );  
    if (hr != S_OK)  
        return hr;  
  
    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );  
    if (!pparsedExpr)  
        return E_OUTOFMEMORY;  
  
    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,  
                                      reinterpret_cast<void**>(ppparsedExpression) );  
    pparsedExpr->Release();  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [[ウォッチ] ウィンドウの式を評価します。](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [ウォッチ式の評価](../../extensibility/debugger/evaluating-a-watch-expression.md)