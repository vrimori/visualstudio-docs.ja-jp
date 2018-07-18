---
title: PENDING_BP_STATE_INFO |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4bf5f77ae24d83a0c0874d2cd03d1f5abbc0e2f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135742"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
コードの場所にバインドする準備が整っているブレークポイントの状態に関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>メンバー  
 状態  
 値、 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)保留中のブレークポイントの状態を指定する列挙体です。  
  
 フラグ  
 フラグの組み合わせ、 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)ブレークポイントが仮想化されているかどうかを指定する列挙です。  
  
## <a name="remarks"></a>コメント  
 この構造体に渡される、 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)で塗り分けはメソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)