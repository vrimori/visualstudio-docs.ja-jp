---
title: IDebugCustomAttributeQuery::IsCustomAttributeDefined |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugCustomAttributeQuery::IsCustomAttributeDefined
- IsCustomAttributeDefined
ms.assetid: c7425db6-4347-4f69-8f88-337ddaa34fa6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d4ee98e4a843227f1855a456fae0f698286b3dc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893750"
---
# <a name="idebugcustomattributequeryiscustomattributedefined"></a>IDebugCustomAttributeQuery::IsCustomAttributeDefined
指定されたカスタム属性が定義されているかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsCustomAttributeDefined(  
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszCustomAttributeName`  
 [in]カスタム属性の名前。  
  
## <a name="return-value"></a>戻り値  
 カスタム属性が定義されている場合を返します`S_OK`。 それ以外を返します`S_FALSE`します。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CDebugClassFieldSymbol**を公開するオブジェクト、 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)インターフェイス。  
  
```cpp  
HRESULT CDebugClassFieldSymbol::IsCustomAttributeDefined(  
    LPCOLESTR pszCustomAttribute  
)  
{  
    HRESULT hr = S_FALSE;  
    CComPtr<IMetaDataImport> pMetadata;  
    mdToken token = mdTokenNil;  
    CComPtr<IDebugField> pField;  
    CComPtr<IDebugCustomAttributeQuery> pCA;  
  
    ASSERT(IsValidWideStringPtr(pszCustomAttribute));  
  
    METHOD_ENTRY( CDebugClassFieldSymbol::IsCustomAttributeDefined );  
  
    IfFalseGo( pszCustomAttribute, E_INVALIDARG );  
  
    IfFailGo( m_spSH->GetMetadata( m_spAddress->GetModule(), &pMetadata ) );  
  
    IfFailGo( CDebugCustomAttribute::GetTokenFromAddress( m_spAddress, &token) );  
    IfFailGo( pMetadata->GetCustomAttributeByName( token,  
              pszCustomAttribute,  
              NULL,  
              NULL ) );  
Error:  
  
    METHOD_EXIT( CDebugClassFieldSymbol::IsCustomAttributeDefined, hr );  
  
    if (hr != S_OK)  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)