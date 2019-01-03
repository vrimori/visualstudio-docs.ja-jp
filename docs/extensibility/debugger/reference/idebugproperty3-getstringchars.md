---
title: IDebugProperty3::GetStringChars |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0597d67e55cb458648b757ca0e222aee7b7a073
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53927234"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
このプロパティに関連付けられている文字列を取得し、ユーザーが指定したバッファーに格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `buflen`  
 [in]ユーザーが指定したバッファーが保持できる最大文字数。  
  
 `rgString`  
 [out]文字列を返します。  
  
 [C++ のみ]、`rgString`を文字列の Unicode 文字を受け取るバッファーへのポインターです。 このバッファーは以上である必要があります`buflen`サイズの文字 (バイトではありません)。  
  
 `pceltFetched`  
 [out]実際には、バッファーに格納されている文字数が返されます。 (できます`NULL`c++)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 C++ では、注意が必要、バッファーが少なくともがあることを保証する`buflen`文字の Unicode 文字。 Unicode 文字は 2 バイト長であることに注意してください。  
  
> [!NOTE]
>  C++ では、返される文字列に終端の null 文字は含まれません。 与えられた場合、`pceltFetched`文字列の文字数を指定します。  
  
## <a name="example"></a>例  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>関連項目  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)