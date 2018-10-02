---
title: IDebugComPlusSymbolProvider::CreateTypeFromPrimitive |Microsoft Docs
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
- IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
- CreateTypeFromPrimitive
ms.assetid: 37213cc2-a038-42ea-9b28-3ae40d4cfe69
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 554c690f2b20d62cb176fbe303dadfe166feb725
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548067"
---
# <a name="idebugcomplussymbolprovidercreatetypefromprimitive"></a>IDebugComPlusSymbolProvider::CreateTypeFromPrimitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugComPlusSymbolProvider::CreateTypeFromPrimitive](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive)します。  
  
指定したプリミティブ型から型を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
[C++]  
HRESULT CreateTypeFromPrimitive(  
   DWORD          dwPrimType,  
   IDebugAddress* pAddress,  
   IDebugField**  ppType  
);  
```  
  
```  
[C#]  
int CreateTypeFromPrimitive(  
   uint          dwPrimType,  
   IDebugAddress pAddress,  
   IDebugField   ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwPrimType`  
 [in]値を[CorElementType 列挙型](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration)プリミティブ型を表します。  
  
 `pAddress`  
 [in]によって表されるアドレス オブジェクトを[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)インターフェイス。  
  
 `ppType`  
 [in]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)型を記述するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugSymbolProvider**を公開するオブジェクト、 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)インターフェイス。  
  
```cpp#  
HRESULT CDebugSymbolProvider::CreateTypeFromPrimitive(  
    DWORD dwPrimType,  
    IDebugAddress* pAddress,  
    IDebugField** ppType)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS addr;  
    const COR_SIGNATURE* pTypeInfo = (const COR_SIGNATURE*) & dwPrimType;  
    CDebugGenericParamScope* pGenScope = NULL;  
  
    //  
    // This function will only work for primitive types  
    //  
  
    METHOD_ENTRY( CDebugSymbolProvider::CreateTypeFromPrimitive );  
  
    IfFailGo( pAddress->GetAddress( &addr ) );  
  
    IfNullGo( pGenScope = new CDebugGenericParamScope(addr.GetModule(), addr.tokClass, addr.GetMethod()), E_OUTOFMEMORY );  
  
    IfFailGo( CreateType( pTypeInfo,  
                          1,  
                          addr.GetModule(),  
                          addr.GetMethod(),  
                          pGenScope,  
                          ppType ) );  
  
    METHOD_EXIT( CDebugSymbolProvider::CreateTypeFromPrimitive, hr );  
  
Error:  
  
    RELEASE( pGenScope );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)

