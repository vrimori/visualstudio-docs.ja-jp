---
title: "実行の制御 | Microsoft Docs"
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
  - "実行の [デバッグ SDK] コントロールのデバッグ"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 実行の制御
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは \(DE\)最後のスタートアップ イベントとしては次の 1 種類のイベントを送信します :  
  
-   最近起動プログラムにアタッチする場合エントリ ポイント イベント  
  
-   既に実行中のプログラムにアタッチする場合読み込みの完了イベント  
  
 これらのイベントはとの両方にユーザーから IDE でことを確認します waits の場合イベントを停止します。  詳細については[オペレーショナル モード](../../extensibility/debugger/operational-modes.md) を参照してください。  
  
## イベントの停止  
 停止イベントがデバッグ セッションに送信される場合 :  
  
1.  現在の命令ポインターを含むスレッド イベント インターフェイスでプログラムを取得できます。  
  
2.  IDE がエディターで強調表示されます。現在のソース・コード ファイルと場所を指定します。  
  
3.  デバッグ セッションを停止この最初のイベントでプログラムの  **続行**  のメソッドを呼び出して応答します。  
  
4.  プログラムではデバッグ セッションにブレークポイントのヒットのような停止条件にde\-DE sends ブレークポイント イベントが発生するまで実行されます。  ブレークポイント イベントは停止イベントが発生しますが再度ユーザーの応答を待機します。  
  
5.  ユーザーが関数にまたはからテスト ステップを選択するとIDE によってデバッグ セッションがステップに関数またはからステップ アウトするかどうか手順についてステートメント \(または\) を行単位と型に渡すプログラムの `Step` のメソッドを呼び出すように要求します。  ステップが完了したらde\-DE sends 停止のイベントのデバッグ セッションの手順への完全なイベント。  
  
     または  
  
     ユーザーが現在の命令ポインターから実行を続けるに選択した場合デバッグ セッションをプログラムの  **実行**  のメソッドを呼び出すように求められます。  プログラムは次の終了条件を検出するまで実行を再開します。  
  
     または  
  
     デバッグ セッションを停止の特定のイベントを無視する場合はプログラムのデバッグ セッション  **続行**  のメソッドを呼び出します。  停止条件が発生したときにプログラムはまたは関数にステップ インし手順を続行します。  
  
 DE が停止条件が発生したときにプログラムによって[IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) のインターフェイスによってデバッグ セッション [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) マネージャー \(SDM\) に [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) や停止などのイベントを送信します。  DE が現在の命令ポインターを含むプログラムおよびスレッドを表す [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) と [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) のインターフェイスを渡します。  SDM は上のスタック フレームを取得する [IDebugThread2:: EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) を呼び出しドキュメントのコンテキストを現在の命令ポインターと関連付けられた取得するに [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) を呼び出します。  このドキュメントのコンテキストはソース・コードのファイル名行番号と列番号です。  IDE が現在の命令ポインターを含むソース・コードを強調表示に使用します。  
  
 SDM は最初に停止のイベント [IDebugProgram2:: 続行](../../extensibility/debugger/reference/idebugprogram2-continue.md) を呼び出して通常応答します。  プログラムはブレークポイントのヒット SDM になどの条件に停止de\-DE sends [IDebugBreakpointEvent2 インターフェイス](../../extensibility/debugger/reference/idebugbreakpointevent2.md) 発生するまで実行されます。  ブレークポイント イベントは停止イベントが発生しますが再度ユーザーの応答を待機します。  
  
 ユーザーが関数にまたはからテスト ステップを選択するとIDE の関数にまたはでステップ実行するに SDM を [IDebugProgram2:: 手順](../../extensibility/debugger/reference/idebugprogram2-step.md) にプロンプトを表示し[STEPUNIT](../../extensibility/debugger/reference/stepunit.md) \(命令ステートメントまたは行\)および [STEPKIND](../../extensibility/debugger/reference/stepkind.md) をつまりかどうかを渡します。  ステップが完了したらde\-DE sends 停止のイベントが SDM への [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) のインターフェイス。  
  
 ユーザーが現在の命令ポインターから実行を続けるに選択した場合SDM に [IDebugProgram2:: 実行](../../extensibility/debugger/reference/idebugprogram2-execute.md) を呼び出すように要求します。  プログラムは次の終了条件を検出するまで実行を再開します。  
  
 デバッグのパッケージが特定の停止のイベントを無視する場合は [IDebugProgram2:: 続行](../../extensibility/debugger/reference/idebugprogram2-continue.md) デバッグのパッケージを呼び出す SDM を呼び出します。  停止条件が発生したときにプログラムはまたは関数にステップ インし手順を続行します。  これは次の方法がわかるようなプログラムについての状態を維持することを意味します。  
  
 SDM が `Step` するには **実行  続行**  は非同期であるためSDM が直ちに制御の呼び出しが実行されることを意味します。  DE sends が SDM `Step` **実行** または  **続行**  が返される前に同じスレッドが停止するイベントSDM ハングします。  
  
## 参照  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)