---
title: IDebugPendingBreakpoint2::SetPassCount |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21e39c54249add3b5d57cd6db907256122aab56b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
設定または保留中のブレークポイントに関連付けられたパスの数を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bpPassCount`  
 [in]A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)パスの数を格納する構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`場合は、ブレークポイントが削除されました。  
  
## <a name="remarks"></a>コメント  
 保留中のブレークポイントに以前関連付けられていたパスの数が失われます。 保留中のブレークポイントからこのバインドのすべてのブレークポイントがそのパスの数に設定すると呼ばれる、`bpPassCount`パラメーター。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)