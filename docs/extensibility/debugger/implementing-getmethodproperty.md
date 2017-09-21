---
title: "GetMethodProperty を実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetMethodProperty メソッド"
  - "IDebugExpressionEvaluator2 プロパティ"
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# GetMethodProperty を実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 Visual Studio はデバッグ エンジン \(DE\) を呼び出して [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md), 、呼び出している [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) スタック フレームの現在のメソッドに関する情報を取得します。  
  
 この実装の `IDebugExpressionEvaluator::GetMethodProperty` 次のタスクを実行します。  
  
1.  呼び出し [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md), を渡すことで、 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) オブジェクトです。 シンボル プロバイダー \(SP\) が返す、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) を指定したアドレスを含むメソッドを表します。  
  
2.  取得、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) から、 `IDebugContainerField`です。  
  
3.  クラスをインスタンス化 \(と呼ばれる `CFieldProperty` この例では\) を実装する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) インターフェイスを含む、 `IDebugMethodField` SP から返されたオブジェクト  
  
4.  返します。、 `IDebugProperty2` からインターフェイス、 `CFieldProperty` オブジェクトです。  
  
## マネージ コード  
 この例の実装を示しています。 `IDebugExpressionEvaluator::GetMethodProperty` マネージ コードにします。  
  
```c#  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        public HRESULT GetMethodProperty(  
                IDebugSymbolProvider symbolProvider,  
                IDebugAddress        address,  
                IDebugBinder         binder,  
                int                  includeHiddenLocals,  
            out IDebugProperty2      property)   
        {  
            IDebugContainerField containerField = null;  
            IDebugMethodField methodField       = null;  
            property = null;  
  
            // Get the containing method field.  
            symbolProvider.GetContainerField(address, out containerField);  
            methodField = (IDebugMethodField) containerField;  
  
            // Return the property of method field.  
            property = new CFieldProperty(symbolProvider, address, binder, methodField);  
            return COM.S_OK;  
        }  
    }  
}  
```  
  
## アンマネージ コード  
 この例の実装を示しています。 `IDebugExpressionEvaluator::GetMethodProperty` アンマネージ コードにします。  
  
```  
[CPP]  
STDMETHODIMP CExpressionEvaluator::GetMethodProperty(  
        in IDebugSymbolProvider *pprovider,  
        in IDebugAddress        *paddress,  
        in IDebugBinder         *pbinder,  
        in BOOL                  includeHiddenLocals,  
        out IDebugProperty2    **ppproperty  
    )  
{  
    if (pprovider == NULL)  
        return E_INVALIDARG;  
  
    if (ppproperty == NULL)  
        return E_INVALIDARG;  
    else  
        *ppproperty = 0;  
  
    HRESULT hr;  
    IDebugContainerField* pcontainer = NULL;  
  
    hr = pprovider->GetContainerField(paddress, &pcontainer);  
    if (FAILED(hr))  
        return hr;  
  
    IDebugMethodField*    pmethod    = NULL;  
    hr = pcontainer->QueryInterface( IID_IDebugMethodField,  
            reinterpret_cast<void**>(&pmethod));  
    pcontainer->Release();  
    if (FAILED(hr))  
        return hr;  
  
    CFieldProperty* pfieldProperty = new CFieldProperty( pprovider,  
                                                         paddress,  
                                                         pbinder,  
                                                         pmethod );  
    pmethod->Release();  
    if (!pfieldProperty)  
        return E_OUTOFMEMORY;  
  
    hr = pfieldProperty->Init();  
    if (FAILED(hr))  
    {  
        pfieldProperty->Release();  
        return hr;  
    }  
  
    hr = pfieldProperty->QueryInterface( IID_IDebugProperty2,  
            reinterpret_cast<void**>(ppproperty));  
    pfieldProperty->Release();  
  
    return hr;  
}  
```  
  
## 参照  
 [ローカル変数の実装のサンプル](../../extensibility/debugger/sample-implementation-of-locals.md)