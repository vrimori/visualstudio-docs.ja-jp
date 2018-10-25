---
title: IDebugPendingBreakpoint2::SetPassCount |Microsoft Docs
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
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f753c95124ec3813a92f1439518ef6c0b1996b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915969"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

設定または保留中のブレークポイントに関連付けられているパスの数を変更します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]A [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)パスの数を含む構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。 返します`E_BP_DELETED`ブレークポイントが削除されている場合。  
  
## <a name="remarks"></a>Remarks  
 以前、保留中のブレークポイントに関連付けられていたパスの数が失われます。 保留中のブレークポイントからこれにバインドされているすべてのブレークポイントがそのパスの数に設定すると呼ばれる、`bpPassCount`パラメーター。  
  
## <a name="see-also"></a>関連項目  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)

