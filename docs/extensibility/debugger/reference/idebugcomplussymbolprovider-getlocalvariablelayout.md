---
title: IDebugComPlusSymbolProvider::GetLocalVariablelayout |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetLocalVariablelayout
- IDebugComPlusSymbolProvider::GetLocalVariablelayout
ms.assetid: b7328d85-e5e9-4d9f-bcd1-e7711fd33878
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fda531db157d75edff107df6de43e48f3dcdfaf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913095"
---
# <a name="idebugcomplussymbolprovidergetlocalvariablelayout"></a>IDebugComPlusSymbolProvider::GetLocalVariablelayout
一連のメソッドのローカル変数のレイアウトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetLocalVariablelayout(  
   ULONG32   ulAppDomainID,  
   GUID      guidModule,  
   ULONG32   cMethods,  
   _mdToken  rgMethodTokens[],  
   IStream** pStreamLayout  
);  
```  
  
```csharp  
int GetLocalVariablelayout(  
   uint        ulAppDomainID,  
   Guid        guidModule,  
   uint        cMethods,  
   int[]       rgMethodTokens,  
   out IStream pStreamLayout  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ulAppDomainID`  
 [in]アプリケーション ドメインの識別子。  
  
 `guidModule`  
 [in]モジュールの一意の識別子。  
  
 `cMethods`  
 [in]メソッドの数のトークン、`rgMethodTokens`配列。  
  
 `rgMethodTokens`  
 [in]メソッドのトークンの配列。  
  
 `pStreamLayout`  
 [out]変数のレイアウトを含むテキスト ストリーム。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugSymbolProvider**を公開するオブジェクト、 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)インターフェイス。  
  
```cpp  
HRESULT CDebugSymbolProvider::GetLocalVariablelayout(  
    ULONG32 ulAppDomainID,   
    GUID guidModule,   
    ULONG32 cMethods,   
    _mdToken rgMethodTokens[],   
    IStream** ppStreamLayout)  
{  
    HRESULT hr = S_OK;  
  
    METHOD_ENTRY(CDebugSymbolProvider::GetLocalVariablelayout);  
  
    CComPtr<ISymUnmanagedReader> symReader;  
    IfFailRet(GetSymUnmanagedReader(ulAppDomainID, guidModule, (IUnknown **) &symReader));  
    CComPtr<IStream> stream;  
    IfFailRet(CreateStreamOnHGlobal(NULL, true, &stream));  
  
    for (ULONG32 iMethod = 0; iMethod < cMethods; iMethod += 1)  
    {  
        CComPtr<ISymUnmanagedMethod> method;  
        IfFailRet(symReader->GetMethod(rgMethodTokens[iMethod], &method));  
        CComPtr<ISymUnmanagedScope> rootScope;  
        IfFailRet(method->GetRootScope(&rootScope));  
  
        //  
        // Add the method's variables to the stream  
        //  
        IfFailRet(AddScopeToStream(rootScope, 0, stream));  
  
        // do end of method marker  
        ULONG32 depth = 0xFFFFFFFF;  
        ULONG cb = 0;  
        IfFailRet(stream->Write(&depth, sizeof(depth), &cb));  
    }  
  
    LARGE_INTEGER pos;  
    pos.QuadPart = 0;  
    IfFailRet(stream->Seek(pos, STREAM_SEEK_SET, 0));  
    *ppStreamLayout = stream.Detach();  
  
    METHOD_EXIT(CDebugSymbolProvider::GetLocalVariablelayout, hr);  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)