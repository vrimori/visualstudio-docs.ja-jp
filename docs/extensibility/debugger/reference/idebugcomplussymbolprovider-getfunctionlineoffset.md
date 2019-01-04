---
title: IDebugComPlusSymbolProvider::GetFunctionLineOffset |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugComPlusSymbolProvider::GetFunctionLineOffset
- GetFunctionLineOffset
ms.assetid: 51460f5a-4e98-427a-8315-27246e24fb61
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3fb64f69c584cc5ae9d96ccc864987b1c1e21b2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854101"
---
# <a name="idebugcomplussymbolprovidergetfunctionlineoffset"></a>IDebugComPlusSymbolProvider::GetFunctionLineOffset
指定した行オフセットを表す関数内でアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionLineOffset(  
   IDebugAddress*  pAddress,   
   DWORD           dwLine,   
   IDebugAddress** ppNewAddress   
);  
```  
  
```csharp  
int GetFunctionLineOffset(  
   IDebugAddress     pAddress,   
   uint              dwLine,   
   out IDebugAddress ppNewAddress  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAddress`  
 [in]関数を表すアドレス。  
  
 `dwLine`  
 [in]行が関数の先頭からのオフセットします。  
  
 `ppNewAddress`  
 [out]関数の先頭からのオフセットの行を表す新しいアドレス。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugSymbolProvider**を公開するオブジェクト、 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)インターフェイス。  
  
```cpp  
HRESULT CDebugSymbolProvider::GetFunctionLineOffset(  
    IDebugAddress *pAddress,  
    DWORD dwLine,  
    IDebugAddress **ppNewAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
    DWORD dwOffset;  
    CDebugAddress* paddr = NULL;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetFunctionLineOffset);  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    // Find the first offset for dwLine in the function  
  
    IfFailGo( pModule->GetFunctionLineOffset( address.addr.addr.addrMethod.tokMethod,  
              address.addr.addr.addrMethod.dwVersion,  
              dwLine,  
              &dwOffset ) );  
  
    // Create the new Address  
  
    address.addr.addr.addrMethod.dwOffset = dwOffset;  
    IfNullGo( paddr = new CDebugAddress(address), E_OUTOFMEMORY );  
    IfFailGo( paddr->QueryInterface( __uuidof(IDebugAddress),  
                                     (void**) ppNewAddress ) );  
  
Error:  
  
    METHOD_EXIT(CDebugSymbolProvider::GetFunctionLineOffset, hr);  
    RELEASE( paddr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)