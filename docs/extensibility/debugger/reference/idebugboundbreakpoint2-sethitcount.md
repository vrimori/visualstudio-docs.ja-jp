---
title: "IDebugBoundBreakpoint2::SetHitCount |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 44393469852cc17c982e644433ba8f38af5f7aa1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
バインドされたブレークポイントのヒット カウントを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```csharp  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwHitCount`  
 [in]ヒット カウントを設定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`バインドされたブレークポイント オブジェクトの状態は に設定されているかどうかは`BPS_DELETED`(の一部、 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)列挙型)。  
  
## <a name="remarks"></a>コメント  
 ヒット カウントは、セッションの現在の実行中にこのブレークポイントが発生した回数です。  
  
 このメソッドは通常、このブレークポイントで現在のヒット カウントを更新するデバッグ エンジンによって呼び出されます。  
  
## <a name="see-also"></a>参照  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)