---
title: IDebugProperty3::GetStringChars |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: d2f7d5430326f57acf686b90f911445cc36dbf02
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118246"
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