---
title: IDebugBreakpointResolution2::GetBreakpointType |Microsoft Docs
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
- IDebugBreakpointResolution2::GetBreakpointType
helpviewer_keywords:
- IDebugBreakpointResolution2::GetBreakpointType
ms.assetid: 2b707fb9-f703-4c78-91bf-7434f57790a0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3afe1d78e247fc55e5b6f80c9d5f38be37bc29dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306749"
---
# <a name="idebugbreakpointresolution2getbreakpointtype"></a>IDebugBreakpointResolution2::GetBreakpointType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

この解像度によって表されるブレークポイントの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT GetBreakpointType(   
   BP_TYPE* pBPType  
);  
```  
  
```csharp  
int GetBreakpointType(   
   out enum_ BP_TYPE pBPType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBPType`  
 [out]値を返します、 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)このブレークポイントの種類を指定する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外の場合はエラー コードを返します。 E_FAIL が返された場合、`bpResLocation`フィールドに関連付けられている[BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)構造が無効です。  
  
## <a name="remarks"></a>Remarks  
 ブレークポイントは、たとえば、コードまたはデータ ブレークポイントを指定できます。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示しています。`CDebugBreakpointResolution`を公開するオブジェクト、 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)インターフェイス。  
  
```  
HRESULT CDebugBreakpointResolution::GetBreakpointType(BP_TYPE* pBPType)    
{    
   HRESULT hr;    
  
   if (pBPType)    
   {    
      // Set default BP_TYPE.    
      *pBPType = BPT_NONE;    
  
      // Check if the BPRESI_BPRESLOCATION flag is set in BPRESI_FIELDS.    
      if (IsFlagSet(m_bpResolutionInfo.dwFields, BPRESI_BPRESLOCATION))    
      {    
         // Set the new BP_TYPE.    
         *pBPType = m_bpResolutionInfo.bpResLocation.bpType;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_FAIL;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)

