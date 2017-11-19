---
title: "IDebugEngineProgram2::WatchForExpressionEvaluationOnThread |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbb3437edc8d357e6a4e96eed9bf9881970a01c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
プログラムが停止された場合でも、特定のスレッドで発生する式の評価を許可 (または許可されていません) します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WatchForExpressionEvaluationOnThread(   
   IDebugProgram2*       pOriginatingProgram,  
   DWORD                 dwTid,  
   DWORD                 dwEvalFlags,  
   IDebugEventCallback2* pExprCallback,  
   BOOL                  fWatch  
);  
```  
  
```csharp  
int WatchForExpressionEvaluationOnThread(   
   IDebugProgram2       pOriginatingProgram,  
   uint                  dwTid,  
   uint                  dwEvalFlags,  
   IDebugEventCallback2 pExprCallback,  
   int                   fWatch  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pOriginatingProgram`  
 [in][IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)式の評価は、プログラムを表すオブジェクト。  
  
 `dwTid`  
 [in]スレッドの識別子を指定します。  
  
 `dwEvalFlags`  
 [in]フラグの組み合わせ、 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)評価を実行する方法を指定する列挙体です。  
  
 `pExprCallback`  
 [in][IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)式の評価中に発生するデバッグ イベントを送信するために使用するオブジェクト。  
  
 `fWatch`  
 [in]0 以外の場合 (`TRUE`)、によって識別される、スレッドで式の評価は、`dwTid`以外の場合、0 (`FALSE`) そのスレッドで式の評価は許可されていません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 セッション デバッグ マネージャー (SDM) によって識別される、プログラムを要求するときに、`pOriginatingProgram`パラメーターを式の評価にこのメソッドを呼び出すことによって接続されている他のすべてのプログラムに通知します。  
  
 1 つのプログラムに式の評価が原因で、コードの関数の評価またはいずれかの評価のため、別の実行が`IDispatch`プロパティです。 このためは、このメソッドを実行し、場合でも、このプログラムにスレッドを停止する可能性があります完了の式の評価を使用します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)