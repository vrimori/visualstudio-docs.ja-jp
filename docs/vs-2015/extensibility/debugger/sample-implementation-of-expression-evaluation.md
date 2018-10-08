---
title: 式の評価の実装のサンプル |Microsoft Docs
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
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f500245a00a3c176d19f85f15655c64a512b6ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539003"
---
# <a name="sample-implementation-of-expression-evaluation"></a>式の評価の実装のサンプル
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[式評価のサンプル実装](https://docs.microsoft.com/visualstudio/extensibility/debugger/sample-implementation-of-expression-evaluation)します。  
  
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 **ウォッチ**ウィンドウ式、Visual Studio 呼び出し[ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)生成するために、 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)オブジェクト。 `IDebugExpressionContext2::ParseText` 式エバリュエーター (EE) および呼び出しをインスタンス化[解析](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)を取得する、 [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。  
  
 この実装の`IDebugExpressionEvaluator::Parse`は、次のタスクを実行します。  
  
1.  [C++ のみ]エラーを検索する式を解析します。  
  
2.  クラスをインスタンス化します (と呼ばれる`CParsedExpression`この例では) を実装する、`IDebugParsedExpression`インターフェイスし、クラスで解析する式を格納します。  
  
3.  返します、`IDebugParsedExpression`からインターフェイス、`CParsedExpression`オブジェクト。  
  
> [!NOTE]
>  以下の例と MyCEE サンプルでは、式エバリュエーターで分離されていない、評価を解析します。  
  
## <a name="managed-code"></a>マネージド コード  
 これは、実装の`IDebugExpressionEvaluator::Parse`マネージ コードでします。 このバージョンのメソッドは、解析を遅延に注意してください。 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)を解析するためのコードは、同時にも評価 (を参照してください[ウォッチ式の評価](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
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
 これは、実装の`IDebugExpressionEvaluator::Parse`アンマネージ コードにします。 このメソッドは、ヘルパー関数を呼び出したり`Parse`、解析した式とエラーをチェックするにはこのメソッドは、結果の値を無視します。 正式な評価の遅延を[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)が評価されるときに、式が解析される (を参照してください[ウォッチ式の評価](../../extensibility/debugger/evaluating-a-watch-expression.md))。  
  
```cpp#  
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
 [ウォッチ ウィンドウ式の評価](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [ウォッチ式の評価](../../extensibility/debugger/evaluating-a-watch-expression.md)

