---
title: Getmethodproperty の実装 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetMethodProperty method
- IDebugExpressionEvaluator2 property
ms.assetid: 6305874f-a2c4-4432-834c-07530ea84bff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 86dea630dc4f04a96cf017d6ac203441c71dedf5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031943"
---
# <a name="implement-getmethodproperty"></a>GetMethodProperty を実装します。
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 Visual Studio はデバッグ エンジン (DE) を呼び出して[GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)、この[GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)スタック フレーム上の現在のメソッドに関する情報を取得します。  
  
 この実装の`IDebugExpressionEvaluator::GetMethodProperty`は、次のタスクを実行します。  
  
1.  呼び出し[GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)で渡し、 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)オブジェクト。 シンボル プロバイダー (SP) を返します、 [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md)を指定したアドレスを含むメソッドを表します。  
  
2.  取得、 [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md)から、`IDebugContainerField`します。  
  
3.  クラスをインスタンス化します (と呼ばれる`CFieldProperty`この例では) を実装する、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスし、が含まれています、 `IDebugMethodField` SP から返されたオブジェクト  
  
4.  返します、`IDebugProperty2`からインターフェイス、`CFieldProperty`オブジェクト。  
  
## <a name="managed-code"></a>マネージド コード  
 この例の実装を示しています。`IDebugExpressionEvaluator::GetMethodProperty`マネージ コードでします。  
  
```csharp  
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
  
## <a name="unmanaged-code"></a>アンマネージ コード  
 この例の実装を示しています。`IDebugExpressionEvaluator::GetMethodProperty`アンマネージ コードにします。  
  
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
  
## <a name="see-also"></a>関連項目  
 [ローカル変数のサンプルの実装](../../extensibility/debugger/sample-implementation-of-locals.md)