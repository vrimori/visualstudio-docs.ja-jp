---
title: "IDebugSymbolProvider |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider
helpviewer_keywords: IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2fbafdf4e2227d7c4d4a69b8b310cf082ac72ee0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
このインターフェイスは、シンボルとそれらをフィールドとして返す型を提供するシンボル プロバイダーを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、シンボルを指定し、式エバリュエーターに情報を入力するには、このインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは COM を使用して取得されます`CoCreateInstance`関数 (アンマネージ シンボル プロバイダー) を読み込んで、適切なマネージ コード アセンブリおよびそのアセンブリ内の情報に基づくシンボル プロバイダーをインスタンス化します。 デバッグ エンジンは、式エバリュエーターと連携するシンボル プロバイダーをインスタンス化します。 このインターフェイスをインスタンス化する方法の 1 つの例を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugSymbolProvider`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|`Initialize`|使用しないでください。 使用しないでください。|  
|`Uninitialize`|使用しないでください。 使用しないでください。|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|デバッグのアドレスを指定するフィールドを取得します。|  
|`GetField`|使用しないでください。 使用しないでください。|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|デバッグのアドレスの配列を作成するドキュメントの位置をマップします。|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|デバッグのアドレスの配列には、ドキュメントのコンテキストをマップします。|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|ドキュメントのコンテキストにデバッグ アドレスにマップします。|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|デバッグのアドレスでコードをコンパイルするために使用する言語を取得します。|  
|`GetGlobalContainer`|使用しないでください。 使用しないでください。|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|完全修飾メソッド名を表すフィールドを取得します。|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|完全修飾クラス名を表すクラスのフィールドの型を取得します。|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|デバッグのアドレスに関連付けられている名前空間の列挙子を作成します。|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|シンボル名を記号の型にマップされます。|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|メソッドで指定されたデバッグ アドレスに依存しているデバッグ アドレスを取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、ドキュメントの位置をデバッグ アドレスに、その逆をマップします。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、シンボル プロバイダーをインスタンス化 (デバッグ エンジンは、この値を認識する必要があります)、GUID を指定する方法を示します。  
  
```cpp  
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
  
## <a name="see-also"></a>参照  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)