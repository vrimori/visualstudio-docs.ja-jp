---
title: "必要なイベントを送信します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] をデバッグするには、イベントが必要"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# 必要なイベントを送信します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

必要なイベントを送信するにはこの手順を使用します。  
  
## 必要なイベントを送信するための手順  
 次のイベントはデバッグ エンジンを作成しプログラムにアタッチする \(DE\) とこの順序で必要です :  
  
1.  DE が一つ以上のプロセスのプログラムをデバッグするために初期化された時点のデバッグ セッション マネージャー \(SDM\) への [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) のイベント オブジェクトを送信します。  
  
2.  デバッグするプログラムを適用するとSDM への [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベント オブジェクトを送信します。  このイベントはデザイン エンジンによって停止のイベントとなる場合があります。  
  
3.  プロセスの起動時にプログラムがアタッチされている場合新しいスレッド IDE に通知するために SDM への [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) のイベント オブジェクトを送信します。  このイベントはデザイン エンジンによって停止のイベントとなる場合があります。  
  
4.  プログラムへのアタッチが完了するとデバッグされるプログラムの読み込みが終了するとまたは SDM への [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) のイベント オブジェクトを送信します。  このイベントは停止のイベントである必要があります。  
  
5.  デバッグするアプリケーションが起動して実行時アーキテクチャのコードの最初の命令が実行時に SDM への [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) のイベント オブジェクトを送信します。  このイベントは常に停止のイベントがあります。  デバッグ セッションにステップ インするとこのイベントで停止します。  
  
> [!NOTE]
>  多くの言語はグローバルな初期化子または外部のコードの先頭にプリコンパイル関数 \(CRT ライブラリまたは \_Main\) を使用します。  ユーザー エントリ ポイントは **主要**  または `WinMain` など到達するとこのコードが実行されエントリ ポイント イベントが送信されますがデバッグ対象の言語が最初のエントリ ポイントの前にそのこれらの型のいずれかが含まれている場合は。  
  
## 参照  
 [デバッグするプログラムを有効にします。](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)