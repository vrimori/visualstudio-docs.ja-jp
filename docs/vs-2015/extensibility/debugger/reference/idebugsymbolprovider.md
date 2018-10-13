---
title: IDebugSymbolProvider |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugSymbolProvider
helpviewer_keywords:
- IDebugSymbolProvider interface
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a87795244e23ac4319fc7ba5eb69d18b163bce0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306723"
---
# <a name="idebugsymbolprovider"></a>IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、記号とフィールドとして返送型を提供するシンボル プロバイダーを表します。  
  
## <a name="syntax"></a>構文  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 シンボル プロバイダーは、シンボルを指定し、式エバリュエーターに情報を入力するには、このインターフェイスを実装する必要があります。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスが COM を使用して取得した`CoCreateInstance`(アンマネージ シンボル プロバイダー) の関数を読み込んで、適切なマネージ コード アセンブリおよびそのアセンブリ内の情報に基づくシンボル プロバイダーをインスタンス化します。 デバッグ エンジンには、式エバリュエーターと連携して動作するシンボル プロバイダーがインスタンス化します。 このインターフェイスをインスタンス化する方法の 1 つの例を参照してください。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDebugSymbolProvider`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|`Initialize`|非推奨。 使用しないでください。|  
|`Uninitialize`|非推奨。 使用しないでください。|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|デバッグ アドレスが含まれるフィールドを取得します。|  
|`GetField`|非推奨。 使用しないでください。|  
|[GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)|デバッグ アドレスの配列にドキュメントの位置をマップします。|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|デバッグ アドレスの配列には、ドキュメントのコンテキストをマップします。|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|ドキュメント コンテキスト デバッグ アドレスにマップします。|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|デバッグ アドレスにコードをコンパイルするために使用する言語を取得します。|  
|`GetGlobalContainer`|非推奨。 使用しないでください。|  
|[GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)|完全修飾メソッド名を表すフィールドを取得します。|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|完全修飾クラス名を表すクラスのフィールドの型を取得します。|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|デバッグ アドレスに関連付けられた名前空間の列挙子を作成します。|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|シンボル名を記号の型にマップします。|  
|[GetNextAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnextaddress.md)|メソッドで指定されたデバッグ アドレスに続くデバッグ アドレスを取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスでは、ドキュメントの位置、またはその逆をデバッグ アドレスにマップされます。  
  
## <a name="requirements"></a>要件  
 ヘッダー: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>例  
 この例では、その GUID (デバッグ エンジンは、この値を知る必要があります) を指定されたシンボル プロバイダーをインスタンス化する方法を示します。  
  
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
  
## <a name="see-also"></a>関連項目  
 [シンボルプロバイダーのインターフェイス](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)

