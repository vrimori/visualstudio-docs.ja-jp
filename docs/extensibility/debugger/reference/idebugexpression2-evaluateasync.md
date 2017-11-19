---
title: "IDebugExpression2::EvaluateAsync |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugExpression2::EvaluateAsync
helpviewer_keywords: IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 371dbeff80ce424cbb37aad6be4265aeec437cd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
このメソッドは、非同期的に式を評価します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFlags`  
 [in]フラグの組み合わせ、 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)式の評価を制御する列挙です。  
  
 `pExprCallback`  
 [in]このパラメーターは、常に null 値です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 それ以外の場合はエラー コードを返します。 一般的なエラー コードは次のとおりです。  
  
|エラー|説明|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|もう一方の式が評価されている現在、および同時式の評価はサポートされていません。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、式の評価が開始された後にすぐに返す必要があります。 式が評価されたときに、 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)に送信する必要があります、 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)イベント コールバックを介して提供された[アタッチ](../../../extensibility/debugger/reference/idebugprogram2-attach.md)または[アタッチ](../../../extensibility/debugger/reference/idebugengine2-attach.md)です。  
  
## <a name="example"></a>例  
 次の例は、単純なは、このメソッドを実装する方法を示します`CExpression`を実装するオブジェクト、 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)インターフェイスです。  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)