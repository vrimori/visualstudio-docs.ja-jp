---
title: "実行を制御 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a76b14f28bdb74345813931fc334f98090abd93c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="control-of-execution"></a>実行の制御
デバッグ エンジン (DE) では、最後のスタートアップ イベントとして、次のイベントのいずれかの通常送信します。  
  
-   エントリ ポイント イベントが表示され、新しく起動されたプログラムにアタッチする場合  
  
-   読み込み完了イベントを既に実行されているプログラムにアタッチする場合  
  
 これら両方のイベントは、イベント、つまり、DE、IDE を使用して、ユーザーからの応答に待機を停止しています。 詳細については、次を参照してください。[の操作モード](../../extensibility/debugger/operational-modes.md)です。  
  
## <a name="stopping-event"></a>イベントを停止しています  
 Stopping イベントが、デバッグ セッションに送信されたとき。  
  
1.  プログラムと現在の命令ポインターが含まれているスレッドは、イベント インターフェイスから取得できます。  
  
2.  IDE では、現在のソース コード ファイルとの位置が表示されます、エディターで強調表示を決定します。  
  
3.  デバッグ セッションは通常この最初の停止イベントに、プログラムを呼び出すことによって応答**続行**メソッドです。  
  
4.  プログラムは、ケース、DE が、デバッグ セッションをブレークポイント イベントを送信する、ブレークポイントにヒットなどの停止条件を検出するまで実行されます。 ブレークポイント イベントは、停止イベント、および、DE 再度応答を待ってユーザー。  
  
5.  場合は、ステップ イン、するか、または、関数から IDE を呼び出して、プログラムのデバッグ セッション`Step`ステップ (命令、ステートメント、または行) とステップの種類の単位を引数としてメソッド: は、ステップ イン、超えるするかどうか、または関数外です。 ステップが完了したら、デは stopping イベントが、デバッグ セッションに手順の完了イベントを送信します。  
  
     - または -  
  
     呼び出して、プログラムのデバッグ セッションのように求められますが、ユーザーの現在の命令ポインターから実行を続行する場合、 **Execute**メソッドです。 プログラムは、[次へ] の停止条件を検出するまで実行を再開します。  
  
     - または -  
  
     デバッグ セッションが、プログラムを呼び出す場合は、デバッグ セッションは、特定の停止イベントを無視するのには、**続行**メソッドです。 プログラムが停止する条件が発生したときに、または関数からステップ実行している場合、は、ステップが続行します。  
  
 プログラムでは、DE には、停止する条件が検出されると、送信などの停止イベント[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)または[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)によりセッション デバッグ マネージャー (SDM) する[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)インターフェイスです。 DE パス、 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)と[IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)プログラムと現在の命令ポインターを格納しているスレッドを表すインターフェイス。 SDM 呼び出し[IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 、最上位のスタック フレームと呼び出しを取得する[IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)を現在の命令に関連付けられているドキュメントのコンテキストを取得するにはポインター。 このドキュメントのコンテキストは、通常、ソース コード ファイル名、行、および列番号です。 IDE は、これらを使用して、現在の命令ポインターを含むソース コードを強調表示します。  
  
 SDM は通常この最初の停止イベントを呼び出すことによって応答[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)です。 プログラムを実行し、ケース、DE を送信する、ブレークポイントにヒットなどの停止条件を検出するまで、 [IDebugBreakpointEvent2 インターフェイス](../../extensibility/debugger/reference/idebugbreakpointevent2.md)SDM にします。 ブレークポイント イベントは、停止イベント、および、DE 再度応答を待ってユーザー。  
  
 場合は、ステップ イン、するか、または、関数から IDE を呼び出す SDM [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)、渡す、 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (命令、ステートメント、または行) と[STEPKIND](../../extensibility/debugger/reference/stepkind.md),、つまりに、オーバー、ステップまたはステップ アウト関数するかどうか。 ステップが完了したら、デを送信、 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)停止イベントであると、SDM へのインターフェイスです。  
  
 IDE が呼び出す SDM を要求する場合は、ユーザーは、現在の命令ポインターから実行を続行するが、 [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)です。 プログラムは、[次へ] の停止条件を検出するまで実行を再開します。  
  
 デバッグ パッケージが呼び出すと、SDM を呼び出してデバッグ パッケージが特定の停止イベントを無視する場合は、 [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)です。 プログラムが停止する条件が発生したときに、または関数からステップ実行している場合、は、ステップが続行します。 つまり、継続する方法を認識できるように、プログラムがステップ実行の状態を保持することです。  
  
 SDM がに対して行う呼び出し`Step`、 **Execute**、および**続行**は非同期で、SDM にすばやく戻るへの呼び出しが期待していることを意味します。 かどうか、DE、SDM 停止イベントに送信する前に、同じスレッド`Step`、 **Execute**、または**続行**、SDM のハングアップを返します。  
  
## <a name="see-also"></a>参照  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)