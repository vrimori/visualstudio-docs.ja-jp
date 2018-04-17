---
title: IDebugExpression2::Abort |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5f4809fcf8e6947309182ff595ad2784b873f529
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
呼び出しによって開始されると、このメソッドが非同期の式の評価をキャンセル、 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)メソッドです。  
  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 非同期の式の評価が取り消された場合は送信されません、 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)に渡されるイベント コールバックへのイベント、[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)または[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)