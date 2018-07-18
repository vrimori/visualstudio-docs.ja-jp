---
title: BP_CONDITION |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee951c5bc18fbf92f94f557c5ade4cd7f39159f2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102601"
---
# <a name="bpcondition"></a>BP_CONDITION
ブレークポイントが発生する条件をについて説明します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```csharp  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## <a name="members"></a>メンバー  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)ブレークポイントが含まれているアプリケーションのアクティブなスレッドを表すオブジェクト。  
  
 `styleCondition`  
 値、 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)このブレークポイントの条件のスタイルを説明する列挙です。  
  
 `bstrContext`  
 ブレークポイントの場所です。  
  
 `bstrCondition`  
 ブレークポイントの発生条件です。  
  
 `nRadix`  
 任意の数値情報を評価する際に使用する基数。  
  
## <a name="remarks"></a>コメント  
 この構造体のメンバーである、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)と[BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)構造体。  
  
 この構造体がパラメーターとして渡されるも、 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)と[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)メソッドです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [構造体と共用体](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)