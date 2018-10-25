---
title: IDebugPendingBreakpoint2::Enable |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::Enable
helpviewer_keywords:
- IDebugPendingBreakpoint2::Enable method
- Enable method
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51309f1af6a96663e9d2ad71348a5b56a0fab6f8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855483"
---
# <a name="idebugpendingbreakpoint2enable"></a>IDebugPendingBreakpoint2::Enable
保留中のブレークポイントの有効な状態を切り替えます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Enable(   
   BOOL fEnable  
);  
```  
  
```csharp  
int Enable(   
   int fEnable  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fEnable`  
 [in]0 以外に設定 (`TRUE`) またはゼロに保留中のブレークポイントを有効にする (`FALSE`) を無効にします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`ブレークポイントが削除されている場合。  
  
## <a name="remarks"></a>Remarks  
 保留中のブレークポイントを有効または無効になっている、ときに、そこからバインドされているすべてのブレークポイントは、同じ状態に設定されます。  
  
 このメソッドは、ブレークポイントが既に有効または無効になっている場合でも、必要な回数だけ呼び出すことがあります。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示しています。`CPendingBreakpoint`を公開するオブジェクト、 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイス。  
  
```cpp  
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the bound breakpoint member variable is valid, then enable or   
      // disable the bound breakpoint.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Enable(fEnable);    
      }    
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to enabled or disabled depending on the passed BOOL condition.    
      m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;    
      hr = S_OK;    
  
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)