---
title: "IDebugProperty3::SetValueAsStringWithError | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::SetValueAsStringWithError"
helpviewer_keywords: 
  - "IDebugProperty3::SetValueAsStringWithError"
ms.assetid: b378368f-4a45-4b2f-8e3d-3bff7a18ab17
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty3::SetValueAsStringWithError
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロパティの値を設定しエラー メッセージを必要に応じて返します。  
  
## 構文  
  
```cpp  
HRESULT SetValueAsStringWithError(  
   LPCOLESTR pszValue,  
   DWORD     dwRadix,  
   DWORD     dwTimeout,  
   BSTR*     errorString  
);  
```  
  
```c#  
int SetValueAsStringWithError(  
   string     pszValue,  
   uint       dwRadix,  
   uint       dwTimeout,  
   out string errorString  
);  
```  
  
#### パラメーター  
 `pszValue`  
 \[入力\] 設定する値。  
  
 `dwRadix`  
 \[入力\] 設定される値の基数。  
  
 `dwTimeout`  
 \[入力\] 値を設定するために待機する時間 \(`INFINITE` の方法では待機\)。  
  
 `errorString`  
 値を設定する \[入力\] このエラーが発生した場合は失敗の理由を保持します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 受信した値が評価される式を指定できます。  
  
## 使用例  
 次の例に [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) インターフェイスを公開する **CProperty の**  オブジェクトに対してこのメソッドを実装する方法を示します。  
  
```cpp#  
HRESULT CProperty::SetValueAsStringWithError(   
    LPCOLESTR in_szValue,  
    DWORD in_RADIX,  
    DWORD in_TIMEOUT,   
    BSTR * out_ERRORTEXT  
)  
{  
    // precondition  
    REQUIRE( NULL != in_szValue );  
  
    if (NULL == in_szValue)  
        return E_INVALIDARG;  
  
    INVARIANT( this );  
    if (!this->ClassInvariant())  
        return E_UNEXPECTED;  
  
    if (NULL == m_pPropertyContext->m_pCEE->m_LanguageSpecificUseCases.pfSetValue)  
        return S_OK;  
  
    // function body  
    DEBUG_PROPERTY_INFO dpInfo,dpInfo2;  
    HRESULT HR = this->GetPropertyInfo(DEBUGPROP_INFO_FULLNAME | DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_TYPE | DEBUGPROP_INFO_VALUE_AUTOEXPAND,  
                                       in_RADIX,  
                                       in_TIMEOUT,  
                                       NULL,  
                                       0,  
                                       &dpInfo);  
  
    if (ENSURE( S_OK == HR ))  
    {  
        REQUIRE( NULL != dpInfo.bstrFullName );  
        REQUIRE( NULL != dpInfo.bstrType );  
  
        REQUIRE( NULL == dpInfo.bstrName );  
        REQUIRE( NULL == dpInfo.bstrValue );  
        REQUIRE( NULL == dpInfo.pProperty );  
  
        BSTR bstrError = NULL;  
  
        UINT ichError = 0;  
        IDebugProperty2* pProperty = NULL;  
        IDebugParsedExpression* pParsedExpression = NULL;  
  
        CComBSTR bstrValue = dpInfo.bstrFullName;  
        bstrValue += L" = ";  
        bstrValue += in_szValue;  
        HR = this->m_pPropertyContext->m_pCEE->  
                Parse(bstrValue, 0, in_RADIX, &bstrError, &ichError, &pParsedExpression);  
        if (S_OK == HR)  
        {  
            REQUIRE( NULL == bstrError );  
            HR = pParsedExpression->EvaluateSync(EVAL_NOEVENTS | EVAL_RETURNVALUE,  
                                                 in_TIMEOUT,  
                                                 m_pPropertyContext->m_pSymbolProvider,  
                                                 m_pPropertyContext->m_pAddress,  
                                                 m_pPropertyContext->m_pBinder,  
                                                 NULL,  
                                                 &pProperty);  
  
            dpInfo2.dwAttrib = DBG_ATTRIB_VALUE_ERROR;  
            if (pProperty)  
            {  
                pProperty->GetPropertyInfo(DEBUGPROP_INFO_ATTRIB | DEBUGPROP_INFO_VALUE,10,in_TIMEOUT,NULL,0,&dpInfo2);  
            }  
            if (DBG_ATTRIB_VALUE_ERROR & dpInfo2.dwAttrib)  
            {  
                HR = E_FAIL;  
                bstrError = dpInfo2.bstrValue;  
            }  
            else  
            {  
                ::SysFreeString(dpInfo.bstrValue);  
            }  
            EXTERNAL_RELEASE(pProperty);  
            EXTERNAL_RELEASE(pParsedExpression);          
        }  
  
        if (bstrError)  
        {  
            if(out_ERRORTEXT)  
            {  
                *out_ERRORTEXT = bstrError;  
                bstrError = NULL;  
            }  
            else  
            {  
                ::SysFreeString(bstrError);  
            }  
        }  
        ::SysFreeString(dpInfo.bstrFullName);  
        ::SysFreeString(dpInfo.bstrType);  
    }  
  
    // postcondition  
    INVARIANT( this );  
  
    return HR;  
}  
```  
  
## 参照  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)