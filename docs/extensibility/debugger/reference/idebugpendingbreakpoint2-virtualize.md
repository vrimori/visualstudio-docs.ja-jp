---
title: IDebugPendingBreakpoint2::Virtualize |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7b9145cff487ebb97894d9b93ad5e1ec54d5b4b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122432"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
ブレークポイントの保留中の仮想化された状態を切り替えます。 保留中のブレークポイントを仮想化すると、デバッグ エンジンは、プログラムに新しいコードを読み込むたびにバインドしようとします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fVirtualize`  
 [in]0 以外に設定 (`TRUE`) 保留中のブレークポイントを仮想化する、または 0 (`FALSE`) 仮想化をオフにします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`場合は、ブレークポイントが削除されました。  
  
## <a name="remarks"></a>コメント  
 コードが読み込まれるたびに、仮想化されたブレークポイントがバインドされています。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示します`CPendingBreakpoint`を公開するオブジェクト、 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)インターフェイスです。  
  
```cpp  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
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