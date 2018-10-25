---
title: IDebugProperty3::GetStringCharLength |Microsoft Docs
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
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a20dc964868386bc345b38fa6ca164cec3a2cada
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876296"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

関連付けられているプロパティの文字列の文字数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStringCharLength(  
   ULONG *pLen  
);  
```  
  
```csharp  
int GetStringCharLength(  
   out uint pLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`pLen`|[out]プロパティの文字列の文字数を返します。|  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`; エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 呼び出しにバッファーを割り当てるための準備としてこのメソッドを使用する、通常、 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)メソッド。  
  
## <a name="example"></a>例  
 次の例では、このメソッドを実装する方法を示しています、 **CProperty**を公開するオブジェクト、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)インターフェイス。  
  
```cpp#  
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)  
{  
    HRESULT hr = E_INVALIDARG;  
  
    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;  
  
    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;  
  
    if (pLen)  
    {  
        DEBUG_PROPERTY_INFO dpInfo;  
        dpInfo.bstrValue = NULL;  
        ULONG ulen = 0;  
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);  
        if (hr == S_OK && dpInfo.bstrValue)  
        {  
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)  
            {  
                ulen = 0;   //VSWhidbey#64815  
            }  
            else  
            {  
                ulen = ::SysStringLen(dpInfo.bstrValue);  
                if( ulen > 2 &&  
                    dpInfo.bstrValue[0] == L'"' &&  
                    dpInfo.bstrValue[ulen-1] == L'"')  
                {                      
                    ulen = ulen > 2 ? ulen - 2 : ulen;  //remove two double quotes  
                }  
            }  
        }  
        ::SysFreeString(dpInfo.bstrValue);  
        *pLen = ulen;  
    }  
    m_EVALFLAGS = oldEVALFLAGS;  
    return hr;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)

