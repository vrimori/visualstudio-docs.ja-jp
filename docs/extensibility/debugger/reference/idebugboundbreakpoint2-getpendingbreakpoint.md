---
title: IDebugBoundBreakpoint2::GetPendingBreakpoint |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBoundBreakpoint2::GetPendingBreakpoint method
- GetPendingBreakpoint method
ms.assetid: 22f94f81-f8d9-46de-96e9-fae6f3c24903
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed136217f9f5c7cffc72ba03562d308723ef5029
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49867781"
---
# <a name="idebugboundbreakpoint2getpendingbreakpoint"></a>IDebugBoundBreakpoint2::GetPendingBreakpoint
指定されたバインドされたブレークポイントの作成元となる保留中のブレークポイントを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPendingBreakpoint(   
   IDebugPendingBreakpoint2** ppPendingBreakpoint  
);  
```  
  
```csharp  
int GetPendingBreakpoint(   
   out IDebugPendingBreakpoint2 ppPendingBreakpoint  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppPendingBreakpoint`  
 [out]返します、 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)ブレークポイントがバインドされるこの作成に使用された保留中のブレークポイントを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 保留中のブレークポイントは、1 つまたは複数のプログラムに適用できるコードにブレークポイントをバインドするために必要なすべての必要な情報のコレクションと考えることができます。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示しています。`CBoundBreakpoint`を公開するオブジェクト、 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)インターフェイス。  
  
```  
HRESULT CBoundBreakpoint::GetPendingBreakpoint(  
    IDebugPendingBreakpoint2** ppPendingBreakpoint)  
{    
   HRESULT hr;    
  
   // Check for valid IDebugPendingBreakpoint2 interface pointer.    
   if (ppPendingBreakpoint)    
   {    
      // Be sure that the bound breakpoint has not been deleted. If  
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugPendingBreakpoint2 interface.    
         hr = m_pPendingBP->QueryInterface(IID_IDebugPendingBreakpoint2,  
                                           (void**)ppPendingBreakpoint);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
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
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)