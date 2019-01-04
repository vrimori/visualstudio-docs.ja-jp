---
title: 実行の制御 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5617849b1dbd8e3857818fb762f562502b89386
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947427"
---
# <a name="control-of-execution"></a>実行の制御
デバッグ エンジン (DE) では、最後のスタートアップ イベントとして、次のイベントのいずれかの通常送信します。  
  
- 新しく起動されたプログラムにアタッチする場合、エントリ ポイント イベント  
  
- 読み込み完了イベントを既に実行されているプログラムにアタッチする場合  
  
  これら両方のイベントは、イベント、つまり、DE が IDE を使用して、ユーザーからの応答を待機する停止しています。 詳細については、次を参照してください。[操作モード](../../extensibility/debugger/operational-modes.md)します。  
  
## <a name="stopping-event"></a>イベントを停止しています  
 ときに、デバッグ セッションを停止イベントが送信されます。  
  
1. プログラムと現在の命令ポインターが含まれているスレッドは、イベント インターフェイスから取得できます。  
  
2. IDE は、現在のソース コード ファイルと、エディターで強調表示されている表示の位置を決定します。  
  
3. デバッグ セッションが通常、プログラムを呼び出して、この最初の停止イベントに応答**続行**メソッド。  
  
4. プログラムは、ブレークポイントのヒットなどの停止条件を検出するまで実行されます。 この場合は、デでは、デバッグ セッションをブレークポイント イベントを送信します。 ブレークポイント イベントは stopping イベントとユーザーの応答待ち、もう一度、DE します。  
  
5. 場合は、ステップ イン、するか、または、関数から IDE を呼び出して、プログラムのデバッグ セッション`Step`メソッド。 IDE は、次の手順 (命令、ステートメント、または行) と (ステップ イン、または、関数からステップするかどうか) のステップの種類の単位を渡します。 ステップが完了したら、デは stopping イベントが、デバッグ セッションに手順の完了イベントを送信します。  
  
    または  
  
    IDE を呼び出して、プログラムのデバッグ セッションを求める場合は、現在の命令ポインターから実行を継続することにした場合、ユーザー、 **Execute**メソッド。 プログラムは、[次へ] の停止条件を検出するまで実行を再開します。  
  
    または  
  
    デバッグ セッションが、プログラムを呼び出して、デバッグ セッションを停止してから特定のイベントを無視する場合、**続行**メソッド。 プログラムが、停止条件が発生したときに、または関数からステップ実行している場合、は、ステップが続行します。  
  
   プログラムでは、停止条件を検出すると、DE、送信などの停止イベント[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)または[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)によってセッション デバッグ マネージャー (SDM)[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)インターフェイス。 DE パス、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)と[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)プログラムと現在の命令ポインターを格納しているスレッドを表すインターフェイス。 SDM コール[IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)最上位のスタック フレームと呼び出しを取得する[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)現在の命令に関連付けられているドキュメント コンテキストを取得するにはポインター。 このドキュメントのコンテキストは、ソース コード ファイル名、線、および列番号では通常です。 IDE は、これらを使用して、現在の命令ポインターを含むソース コードを強調表示します。  
  
   SDM は通常、この最初の停止イベントを呼び出して、応答[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)します。 プログラムを実行し、DE ケースを送信する、ブレークポイントのヒットなどの停止条件を検出するまで、 [IDebugBreakpointEvent2 インターフェイス](../../extensibility/debugger/reference/idebugbreakpointevent2.md)SDM をします。 ブレークポイント イベントは stopping イベントとユーザーの応答待ち、もう一度、DE します。  
  
   ステップ イン、するか、関数から呼び出す SDM IDE するように求められます。 [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)します。 IDE が通過し、 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (命令、ステートメント、または行) と[STEPKIND](../../extensibility/debugger/reference/stepkind.md)、つまり、ステップ イン、または、関数からステップするかどうか。 ステップが完了したら、デを送信、 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) stopping イベントであると、SDM へのインターフェイス。  
  
   現在の命令ポインターから実行を継続することにした場合、ユーザー、IDE 確認を呼び出す SDM [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)します。 プログラムは、[次へ] の停止条件を検出するまで実行を再開します。  
  
   デバッグ パッケージが呼び出すと、SDM を呼び出してデバッグ パッケージが停止してから特定のイベントを無視する場合は、 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)します。 場合は、プログラムが、停止条件が発生したときに、または関数からステップ実行、ステップを続行します。 つまり、継続する方法を認識できるように、プログラムがステップ実行の状態を維持します。  
  
   SDM を呼び出し`Step`、 **Execute**、および**続行**は非同期で、SDM をすばやく返す呼び出しを期待していることを意味します。 かどうか、DE、SDM stopping イベントに送信する前に、同じスレッド`Step`、 **Execute**、または**続行**、SDM のハングを返します。  
  
## <a name="see-also"></a>関連項目  
 [タスクをデバッグします。](../../extensibility/debugger/debugging-tasks.md)