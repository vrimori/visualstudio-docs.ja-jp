---
title: "IDebugComPlusSymbolProvider2::IsAddressSequencePoint | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugComPlusSymbolProvider2::IsAddressSequencePoint"
  - "IsAddressSequencePoint"
ms.assetid: 89b27c57-5295-428b-8229-a402500d8cd3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugComPlusSymbolProvider2::IsAddressSequencePoint
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグのアドレス指定がシーケンス ポイントであるかどうかを判定します。  
  
## 構文  
  
```cpp#  
HRESULT IsAddressSequencePoint(  
   IDebugAddress* pAddress  
);  
```  
  
```c#  
int IsAddressSequencePoint(  
   IDebugAddress pAddress  
);  
```  
  
#### パラメーター  
 `pAddress`  
 \[入力\] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) のインターフェイスで表されるアドレスをデバッグします。  
  
## 戻り値  
 デバッグのアドレスがシーケンス ポイントの場合戻り `S_OK`; それ以外の場合戻り `S_FALSE`。  
  
## 使用例  
 次の例に [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) インターフェイスを公開する **CDebugSymbolProvider の**  オブジェクトに対してこのメソッドを実装する方法を示します。  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsAddressSequencePoint(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    METHOD_ENTRY( CDebugSymbolProvider::LoadSymbol );  
  
    IfFalseGo( pAddress, E_INVALIDARG );  
  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsSequencePoint( address.addr.addr.addrMethod.tokMethod,  
                                   address.addr.addr.addrMethod.dwVersion,  
                                   address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this is not a sequence point  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::LoadSymbol, hr );  
  
    return hr;  
}  
```  
  
## 参照  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)