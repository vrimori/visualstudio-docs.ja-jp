---
title: "コントロールのイベント | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] イベントのデバッグ"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# コントロールのイベント
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プログラムの制御された実行中にイベントを送信する必要があります。  イベントはすべて[IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスを使用して送信され[IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) のメソッドを実行するように要求する属性があります。  
  
## メソッド  
 一部のイベントは次のようにメソッドの実装が必要です :  
  
-   デバッグ エンジンが初期化された時点 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) の \(DE\) インターフェイスを使用すると[IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) のメソッドを実装する必要があります。  
  
-   コントロールは実行 [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) と [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) のインターフェイスなどのコントロール イベントの実装が必要です。  **IDebugBreakEvent2** は非同期中断にのみ必要です。  
  
-   関数については [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) のインターフェイスおよびメソッドの実装が必要です。  
  
 ブレークポイントから派生したイベント [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) は[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) と [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) インターフェイスおよび [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) のメソッドの実装が必要です。  
  
 非同期式の評価は [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)インターフェイスおよび [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[と GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) のメソッドを実装する必要があります。  
  
 同期イベントは [IDebugEngine2:: ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md) のメソッドを実装する必要があります。  
  
 文字列スタイルの出力を書き込むエンジンに [IDebugOutputStringEvent2:: GetString](../Topic/IDebugOutputStringEvent2::GetString.md) のメソッドを実装する必要があります。  
  
## 参照  
 [実行の制御と状態の評価](../../extensibility/debugger/execution-control-and-state-evaluation.md)