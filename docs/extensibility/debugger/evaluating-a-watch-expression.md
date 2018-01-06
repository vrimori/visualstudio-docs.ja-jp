---
title: "ウォッチ式の評価 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6b28c07ba77bcee7fb0368985cbdcec015177e30
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="evaluating-a-watch-expression"></a>ウォッチ式の評価
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 Visual Studio の準備ができたら、ウォッチ式の値を表示するときに呼び出す[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)をさらにこの[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)です。 これにより作成される、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)値と式の型を含むオブジェクト。  
  
 この実装で`IDebugParsedExpression::EvaluateSync`式が解析され、同時に評価されます。 この実装では、次のタスクを実行します。  
  
1.  解析し、値とその型を格納する汎用オブジェクトを生成するために式を評価します。 C# の場合、これとして表されます、`object`として C++ で表されます中に、`VARIANT`です。  
  
2.  クラスをインスタンス化 (と呼ばれる`CValueProperty`この例では) を実装する、`IDebugProperty2`インターフェイスし、クラスに返される値を格納します。  
  
3.  返します、`IDebugProperty2`からインターフェイス、`CValueProperty`オブジェクト。  
  
## <a name="managed-code"></a>マネージ コード  
 これは、実装、`IDebugParsedExpression::EvaluateSync`マネージ コードでします。 ヘルパー メソッド`Tokenize`解析ツリーに式を解析します。 ヘルパー関数`EvalToken`トークンを値に変換します。 ヘルパー関数`FindTerm`解析ツリーを走査する再帰的に呼び出す`EvalToken`の値を表すと、式で任意の操作 (加算または減算) を適用することは、各ノードのです。  
  
```csharp  
namespace EEMC  
{  
    public class CParsedExpression : IDebugParsedExpression  
    {  
        public HRESULT EvaluateSync(  
            uint evalFlags,  
            uint timeout,  
            IDebugSymbolProvider provider,  
            IDebugAddress address,  
            IDebugBinder binder,  
            string resultType,  
            out IDebugProperty2 result)  
        {  
            HRESULT retval = COM.S_OK;  
            this.evalFlags = evalFlags;  
            this.timeout = timeout;  
            this.provider = provider;  
            this.address = address;  
            this.binder = binder;  
            this.resultType = resultType;  
  
            try  
            {  
                IDebugField field = null;  
                // Tokenize, then parse.  
                tokens = Tokenize(expression);  
                result = new CValueProperty(  
                             expression,  
                             (int) FindTerm(EvalToken(tokens[0], out field),1),  
                             field,  
                             binder);  
            }  
            catch (ParseException)  
            {  
                result = new CValueProperty(expression, "Huh?");  
                retval = COM.E_INVALIDARG;  
            }  
            return retval;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>アンマネージ コード  
 これは、実装、`IDebugParsedExpression::EvaluateSync`アンマネージ コードにします。 ヘルパー関数`Evaluate`を解析し、式を返す、評価、`VARIANT`結果の値を保持します。 ヘルパー関数`VariantValueToProperty`バンドル、`VARIANT`に、`CValueProperty`オブジェクト。  
  
```  
[C++]  
STDMETHODIMP CParsedExpression::EvaluateSync(   
    in  DWORD                 evalFlags,  
    in  DWORD                 dwTimeout,  
    in  IDebugSymbolProvider* pprovider,  
    in  IDebugAddress*        paddress,  
    in  IDebugBinder*         pbinder,  
    in  BSTR                  bstrResultType,  
    out IDebugProperty2**     ppproperty )  
{  
    // dwTimeout parameter is ignored in this implementation.  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (paddress == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    VARIANT value;  
    BSTR    bstrErrorMessage = NULL;  
    hr = ::Evaluate( pprovider,  
                     paddress,  
                     pbinder,  
                     m_expr,  
                     &bstrErrorMessage,  
                     &value );  
    if (hr != S_OK)  
    {  
        if (bstrErrorMessage == NULL)  
            return hr;  
  
        //we can display better messages ourselves.  
        HRESULT hrLocal = S_OK;  
        VARIANT varType;  
        VARIANT varErrorMessage;  
  
        VariantInit( &varType );  
        VariantInit( &varErrorMessage );  
        varErrorMessage.vt      = VT_BSTR;  
        varErrorMessage.bstrVal = bstrErrorMessage;  
  
        CValueProperty* valueProperty = new CValueProperty();  
        if (valueProperty != NULL)  
        {  
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);  
            if (SUCCEEDED(hrLocal))   
            {  
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,  
                        reinterpret_cast<void**>(ppproperty) );  
            }  
        }  
  
        VariantClear(&varType);  
        VariantClear(&varErrorMessage); //frees BSTR  
        if (!valueProperty)  
            return hr;  
        valueProperty->Release();  
        if (FAILED(hrLocal))  
            return hr;  
    }  
    else  
    {  
        if (bstrErrorMessage != NULL)  
            SysFreeString(bstrErrorMessage);  
  
        hr = VariantValueToProperty( pprovider,  
                                     paddress,  
                                     pbinder,  
                                     m_radix,  
                                     m_expr,  
                                     value,  
                                     ppproperty );  
        VariantClear(&value);  
        if (FAILED(hr))  
            return hr;  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>参照  
 [[ウォッチ] ウィンドウの式を評価します。](../../extensibility/debugger/evaluating-a-watch-window-expression.md)   
 [式の評価の実装のサンプル](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)