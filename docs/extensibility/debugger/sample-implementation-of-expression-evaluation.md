---
title: 式の評価の実装のサンプル |Microsoft Docs
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
ms.openlocfilehash: 10efa25ba2f692e9cf4a9c3588d210d31f9e8065
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901295"
---
# <a name="sample-implementation-of-expression-evaluation"></a>式の評価の実装のサンプル
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーター サンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 **ウォッチ**ウィンドウ式、Visual Studio 呼び出し[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)生成するために、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。 `IDebugExpressionContext2::ParseText` 式エバリュエーター (EE) および呼び出しをインスタンス化[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)を取得する、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。  
  
 `IDebugExpressionEvaluator::Parse`は、次のタスクを実行します。  
  
1.  [C++ のみ]エラーを検索する式を解析します。  
  
2.  クラスをインスタンス化します (と呼ばれる`CParsedExpression`この例では) を実行する、`IDebugParsedExpression`インターフェイスし、クラスで解析する式を格納します。  
  
3.  返します、`IDebugParsedExpression`からインターフェイス、`CParsedExpression`オブジェクト。  
  
> [!NOTE]
>  以下の例と MyCEE サンプルでは、式エバリュエーターで分離されていない、評価を解析します。  
  
## <a name="managed-code"></a>マネージド コード  
 次のコードの実装を示します`IDebugExpressionEvaluator::Parse`マネージ コードでします。 このバージョンのメソッドを延期する解析[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を解析するためのコードは、同時にも評価 (を参照してください[ウォッチ式を評価](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
次のコードは、実装の`IDebugExpressionEvaluator::Parse`アンマネージ コードにします。 このメソッドは、ヘルパー関数を呼び出したり`Parse`、解析した式と、エラーをチェックするにはこのメソッドは、結果の値を無視します。 正式な評価の遅延を[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)が評価されるときに、式が解析される (を参照してください[ウォッチ式を評価](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
 [ウォッチ式を評価します。](../../extensibility/debugger/evaluating-a-watch-expression.md)