---
title: コントロールのイベント |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1a9fda07e49df71790419e487b3906799433a2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820479"
---
# <a name="control-events"></a>コントロールのイベント
プログラムの制御された実行中にイベントを送信する必要があります。 使用してすべてのイベントが送信される、 [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md)インターフェイスを実装することを必要とする属性、 [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md)メソッド。  
  
## <a name="additional-methods"></a>追加のメソッド  
 一部のイベントには、次のように追加のメソッドの実装が必要です。  
  
- 送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) (DE) デバッグ エンジンの初期化時にインターフェイスでは、実装する必要があります、 [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)メソッド。  
  
- 実行の制御などのコントロール イベントの実装が必要です、 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)と[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)インターフェイス。 **IDebugBreakEvent2**は非同期の中断でのみ必要です。  
  
- 実装の関数にステップ インする必要があります、 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)インターフェイスとそのメソッド。  
  
  ブレークポイントから派生するイベントの実装が必要に、 [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)、 [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)、および[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)インターフェイス、だけでなく[IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)と[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)メソッド。  
  
  非同期の式の評価では、実装する必要があります、 [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)インターフェイスとその[IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[および GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)メソッド。  
  
  同期イベントは、実装する必要があります、 [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)メソッド。  
  
  文字列形式の出力を書き込む、エンジンでは、実装する必要があります、 [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)