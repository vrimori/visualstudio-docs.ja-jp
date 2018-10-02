---
title: IDebugComPlusSymbolProvider::UpdateSymbols |Microsoft Docs
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
- UpdateSymbols
- IDebugComPlusSymbolProvider::UpdateSymbols
ms.assetid: d530f6f1-4af2-454b-bab0-02478a8fe81e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f4263d4f8e98cd03f21a9b007104f5bea3404695
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547617"
---
# <a name="idebugcomplussymbolproviderupdatesymbols"></a>IDebugComPlusSymbolProvider::UpdateSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugComPlusSymbolProvider::UpdateSymbols](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols)します。  
  
指定したデータ ストリームからメモリにデバッグ シンボルを更新します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT UpdateSymbols (  
   ULONG32  ulAppDomainID,  
   GUID     guidModule,  
   IStream* pUpdateStream  
);  
```  
  
```csharp  
int UpdateSymbols (  
   uint    ulAppDomainID,  
   Guid    guidModule,  
   IStream pUpdateStream  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ulAppDomainID`  
 [in]アプリケーション ドメインの識別子。  
  
 `guidModule`  
 [in]モジュールの一意の識別子。  
  
 `pUpdateStream`  
 [in]更新されたデバッグ シンボルが含まれるデータ ストリーム。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugSymbolProvider**を公開するオブジェクト、 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)インターフェイス。  
  
```cpp#  
HRESULT CDebugSymbolProvider::UpdateSymbols(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream  
)  
{  
    ASSERT(!"Use UpdateSymbols2 on IDebugENCSymbolProvider2");  
    return E_NOTIMPL;  
}  
  
HRESULT CDebugSymbolProvider::UpdateSymbols2(  
    ULONG32 ulAppDomainID,  
    GUID guidModule,  
    IStream* pUpdateStream,  
    LINEDELTA* pDeltaLines,  
    ULONG cDeltaLines  
)  
{  
    HRESULT hr = S_OK;  
    CComPtr<CModule> pModule;  
    Module_ID idModule(ulAppDomainID, guidModule);  
  
    METHOD_ENTRY( CDebugSymbolProvider::UpdateSymbols );  
  
    IfFailGo( GetModule( idModule, &pModule ) );  
    IfFailGo( pModule->UpdateSymbols( pUpdateStream, pDeltaLines, cDeltaLines ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::UpdateSymbols, hr );  
  
    return hr;  
}  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

