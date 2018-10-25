---
title: コントロールのイベント |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb3332ead5928be9127d64c3870b3212cd6754fe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837907"
---
# <a name="control-events"></a>管理イベント
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

