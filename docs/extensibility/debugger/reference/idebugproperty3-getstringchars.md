---
title: "IDebugProperty3::GetStringChars |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: f84c744eef8dab863ec9a91aec621764dfa3c266
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

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
 [in]ユーザーが指定したバッファーに保持できる最大文字数。  
  
 `rgString`  
 [out]文字列を返します。  
  
 [C++ のみ]、`rgString`文字列の Unicode 文字を受け取るバッファーへのポインターです。 このバッファーは以上である必要があります`buflen`サイズ (バイトではなく) 文字です。  
  
 `pceltFetched`  
 [out]ここで、バッファーに実際に格納されている文字の数が返されます。 (できます`NULL`c++)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 C++ では、ある注意する必要があることを確認、バッファーには、少なくとも`buflen`文字の Unicode 文字。 Unicode 文字は 2 バイト長であることに注意してください。  
  
> [!NOTE]
>  C++ では、返される文字列に終端の null 文字は含まれません。 指定された場合`pceltFetched`文字列内の文字数を指定します。  
  
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
