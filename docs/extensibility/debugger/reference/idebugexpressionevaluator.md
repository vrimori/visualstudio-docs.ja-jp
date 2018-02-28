---
title: "IDebugExpressionEvaluator |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: e0dad3317c3566051144bb7f3c335be9574103c4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 このインターフェイスは、式エバリュエーターを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、このインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを取得するには、を通じて、式エバリュエーターをインスタンス化、`CoCreateInstance`エバリュエーターのクラス ID (CLSID) を使用してメソッドです。 この例を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugExpressionEvaluator`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|式の文字列を解析された式に変換します。|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|ローカル変数、引数、およびメソッドの他のプロパティを取得します。|  
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|メモリ アドレスには、メソッドの場所とオフセットを変換します。|  
|[Setlocale、_wsetlocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|印刷可能な結果の作成に使用する言語を決定します。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|レジストリ ルートを設定します。 サイド バイ サイドのデバッグに使用します。|  
  
## <a name="remarks"></a>コメント  
 一般的な状況で、デバッグ エンジン (DE) インスタンスを作成、式エバリュエーター (EE) への呼び出しの結果として[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)です。 デがレジストリから EE の CLSID を取得、DE には、言語および使用したい EE の仕入先が認識している、ため (、[をデバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)関数、`GetEEMetric`取得に役立ちます)。  
  
 EE はインスタンス化した後、DE を呼び出す[解析](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)に式を解析し、保存、 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)オブジェクト。 その後への呼び出し[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)式を評価します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、ソース コードでシンボル プロバイダーとアドレスを指定された式エバリュエーターをインスタンス化する方法を示します。 この例では、`GetEEMetric`から、[をデバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)ライブラリ、dbgmetric.lib です。  
  
```cpp  
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,  
                                                 IDebugAddress *pSourceAddress)  
{  
    // This is typically defined globally but is specified here just  
    // for this example.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
  
    IDebugExpressionEvaluator *pEE = NULL;  
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {  
        HRESULT hr         = S_OK;  
        GUID  languageGuid = { 0 };  
        GUID  vendorGuid   = { 0 };  
  
        hr = pSymbolProvider->GetLanguage(pSourceAddress,  
                                          &languageGuid,  
                                          &vendorGuid);  
        if (SUCCEEDED(hr)) {  
            CLSID clsidEE      = { 0 };  
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;  
            // Get the expression evaluator's CLSID from the registry.  
            ::GetEEMetric(languageGuid,  
                          vendorGuid,  
                          metricCLSID,  
                          &clsidEE,  
                          strRegistrationRoot);  
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {  
                // Instantiate the expression evaluator.  
                spExpressionEvaluator.CoCreateInstance(clsidEE);  
            }  
            if (spExpressionEvaluator != NULL) {  
                pEE = spExpressionEvaluator.Detach();  
            }  
        }  
    }  
    return pEE;  
}  
```  
  
## <a name="see-also"></a>参照  
 [式の評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)