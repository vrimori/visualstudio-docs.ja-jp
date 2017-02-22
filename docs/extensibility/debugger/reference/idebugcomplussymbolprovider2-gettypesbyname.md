---
title: "IDebugComPlusSymbolProvider2::GetTypesByName | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetTypesByName"
  - "IDebugComPlusSymbolProvider2::GetTypesByName"
ms.assetid: ef76b1a8-6910-48fe-b4af-d9045eefd23f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider2::GetTypesByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

その名前を指定する型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetTypesByName(  
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int GetTypesByName(  
   string               pszClassName,  
   enum_ NAME_MATCH     nameMatch,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszClassName`  
 [in]型の名前。  
  
 `nameMatch`  
 [in]たとえば、一致の大文字小文字の区別の種類を選択します。 値、 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 列挙します。  
  
 `ppEnum`  
 [out]型または指定した名前の型が含まれている列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す `S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="remarks"></a>解説  
 検索する名、ジェネリック型の '一覧 \< int>' または 'List \< int、int >' は 'リスト' です。 複数のモジュールで同じ名前の種類が表示されない場合、 `ppEnum` パラメーターには、すべてのコピーが含まれることができます。 使用する必要がある [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) し、区別に基づいて、 `guidModule` パラメーター。  
  
## <a name="example"></a>例  
 次の例では、このメソッドは実装する方法、 **CDebugSymbolProvider** を公開するオブジェクト、 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md) インターフェイスです。  
  
```cpp#  
HRESULT CDebugSymbolProvider::GetTypesByName(  
    LPCOLESTR pszClassName,  
    NAME_MATCH nameMatch,  
    IEnumDebugFields** ppEnum  
)  
{  
    HRESULT hr = S_OK;  
    CModIter ModIter;  
    CModule* pmodule; // the iterator owns the reference  
    CFieldList listField;  
  
    ASSERT(IsValidWideStringPtr(pszClassName));  
    ASSERT(IsValidWritePtr(ppEnum, IEnumDebugFields*));  
  
    METHOD_ENTRY( CDebugSymbolProvider::GetTypesByName );  
  
    IfFalseGo( pszClassName && ppEnum, E_INVALIDARG );  
    *ppEnum = NULL;  
  
    IfFailGo( GetModuleIter(&ModIter) );  
  
    hr = S_FALSE;  
  
    if ( nameMatch == nmCaseInsensitive)  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByNameCaseInsensitive( pszClassName,  
                    &listField,  
                    this ) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
    else  
    {  
        while (ModIter.GetNext(&pmodule))  
        {  
            if (pmodule->FindTypesByName( pszClassName,  
                                          &listField,  
                                          this) )  
            {  
                hr = S_OK;  
            }  
        }  
    }  
  
    // If the list is empty then no type  
    IfFalseGo( listField.GetCount(), E_FAIL );  
  
    // Create enumerator  
    IfFailGo( CreateEnumerator( ppEnum, &listField ) );  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::GetTypesByName, hr );  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>参照  
 [IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)