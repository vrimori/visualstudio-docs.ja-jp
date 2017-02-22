---
title: "IDebugExpressionEvaluator | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator インターフェイス"
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、式エバリュエーターを表します。  
  
## 構文  
  
```  
IDebugExpressionEvaluator : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、このインターフェイスを実装する必要があります。  
  
## 呼び出し元のノート  
 このインターフェイスを取得するには、を通じて、式エバリュエーターをインスタンス化、 `CoCreateInstance` エバリュエーターのクラス ID \(CLSID\) を使用してメソッドです。 この例を参照してください。  
  
## Vtable 順序のメソッド  
 次の表は、のメソッドを示しています。 `IDebugExpressionEvaluator`します。  
  
|メソッド|説明|  
|----------|--------|  
|[Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|式の文字列を解析された式に変換します。|  
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|ローカル変数、引数、およびメソッドの他のプロパティを取得します。|  
|[GetMethodLocationProperty](../Topic/IDebugExpressionEvaluator::GetMethodLocationProperty.md)|メモリ アドレス、メソッドの場所とのオフセットに変換します。|  
|[Setlocale 関数](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|印刷可能な結果を作成するのに使用する言語を決定します。|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|レジストリのルートを設定します。 サイド バイ サイドのデバッグに使用します。|  
  
## 解説  
 一般的な状況で \(DE\) のデバッグ エンジンのインスタンスを作成、式エバリュエーター \(EE\) への呼び出しの結果として [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)します。 デがレジストリから EE の CLSID を取得、DE には、言語として使用する EE のベンダーが認識している、ため \(、 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) 関数の場合、 `GetEEMetric`, は、この検索に役立ちます\)。  
  
 EE がインスタンス化された後、DE を呼び出す [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) 式を解析し、保存、 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) オブジェクトです。 その後への呼び出し [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) 式を評価します。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 使用例  
 この例では、ソース コードで指定されているシンボル プロバイダーは、アドレス式エバリュエーターをインスタンス化する方法を示します。 この例は、関数を使用して `GetEEMetric`, から、 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) ライブラリ、dbgmetric.lib です。  
  
```cpp#  
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
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [デバッグ用の SDK ヘルパー](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)