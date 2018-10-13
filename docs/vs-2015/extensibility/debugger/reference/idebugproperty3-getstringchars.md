---
title: IDebugProperty3::GetStringChars |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 953c5d9f2a0dac12825e0e92776f4800d7d719ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245896"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
<!-- TODO: review snippet reference  [!CODE [[cpp]]([cpp])]  -->  
  
```  
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
```  
  
<!-- TODO: review snippet reference  [!CODE [}](})]  -->  
  
## <a name="see-also"></a>関連項目  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)