---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "IDebugSymbolProvider インターフェイス"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはシンボルを提供するフィールドとして返すプロバイダーのシンボルを表します。  
  
## 構文  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## 実装についてのメモ  
 シンボルのプロバイダーは式エバリュエーターにシンボルと型情報を指定するにはこのインターフェイスを実装する必要があります。  
  
## 呼び出し元のメモ  
 このインターフェイスはアンマネージのシンボル \(プロバイダー\) に COM `CoCreateInstance` の関数を使用することで取得または適切なマネージ コード アセンブリを読み込んで情報に基づいてシンボルのプロバイダーをインスタンス化してそのアセンブリで使用します。  デバッグ エンジンは式エバリュエーターとの関連に動作するようにシンボルのプロバイダーをインスタンス化します。  このインターフェイスのインスタンス化に1 種類の方法の例を参照してください。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugSymbolProvider` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|`Initialize`|使用は推奨されていません。  使用しないでください。|  
|`Uninitialize`|使用は推奨されていません。  使用しないでください。|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|デバッグを含むのアドレス フィールドを取得します。|  
|`GetField`|使用は推奨されていません。  使用しないでください。|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|デバッグのアドレスの配列にドキュメント内の位置をマップします。|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|デバッグのアドレスの配列にドキュメントのコンテキストをマップします。|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|ドキュメントのコンテキストにデバッグのアドレスをマップします。|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|言語のデバッグのアドレスのコードをコンパイルするために使用するを取得します。|  
|`GetGlobalContainer`|使用は推奨されていません。  使用しないでください。|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|完全修飾名を表すフィールドを取得します。|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|完全修飾クラス名を表すクラスのフィールドの種類を取得します。|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|デバッグのアドレスに関連付けられている名前空間の列挙子を作成します。|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|シンボルの型のシンボル名をマップします。|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|メソッドの特定のデバッグのアドレスに従ってデバッグのアドレスを取得します。|  
  
## 解説  
 このインターフェイスはデバッグのアドレスにドキュメントの場所をその逆もマップします。  
  
## 必要条件  
 ヘッダー : sh.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 使用例  
 この例ではGUID を持つシンボルのプロバイダーのインスタンスを作成する方法を示しています \(デバッグ エンジンはこの値を知っている必要があります。  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## 参照  
 [シンボルのプロバイダー インターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)