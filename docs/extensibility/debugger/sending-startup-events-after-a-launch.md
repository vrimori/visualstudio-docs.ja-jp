---
title: "起動した後、スタートアップ イベントを送信します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] スタートアップ イベントのデバッグ"
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# 起動した後、スタートアップ イベントを送信します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

いったんデバッグ エンジンはデバッグ \(DE\) セッションにプログラムに送り返します一連のスタートアップ イベントにアタッチされます。  
  
 デバッグ セッションに送信されるスタートアップ イベントが含まれています :  
  
-   エンジンの作成イベント。  
  
-   プログラムの作成イベント。  
  
-   スレッドの作成とモジュールの読み込みイベント。  
  
-   コードが実行される前にコードが読み込まれてされ実行可能な読み込みの完了イベントまたは  
  
    > [!NOTE]
    >  このイベントが従うとグローバル変数が初期化および起動ルーチンが実行されます。  
  
-   可能な他のスレッドの作成およびモジュールの読み込みイベント。  
  
-   プログラムはメイン エントリ ポイントに達したことを通知  **主要**  または `WinMain` のようなエントリ ポイント イベント。  このイベントは通常de\-DE が既に実行中のプログラムにアタッチして送信されません。  
  
 プログラムによってde\-DE 1 番目のデバッグ セッション マネージャーに \(SDM\) エンジンの作成イベントを表す [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) に続く [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) インターフェイスプログラムの作成イベントを表す。  
  
 これは一つ以上の [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) のスレッドの作成イベントと [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) のモジュールの読み込みイベントに一般的に適用されます。  
  
 コードが読み込まれ操作できますがとコードが実行される前にde\-DE sends SDM [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) の読み込みの完了イベント。  最後にプログラムがまだ実行されていない場合de\-DE sends は [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) のエントリ ポイント イベントプログラムのメイン エントリ ポイントに達したデバッグの準備ができていることを通知します。  
  
## 参照  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)