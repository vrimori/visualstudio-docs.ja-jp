---
title: IDebugExpression2::Abort |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 668b4fe87bb0c37796d63cb313c15d146c70a58e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910595"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
呼び出しによって起動すると、このメソッドが非同期式の評価をキャンセル、 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 非同期の式の評価が取り消されたときに送信されません、 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)にイベントをイベント コールバックが渡される、[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)または[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)