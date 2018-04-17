---
title: 必要なイベントを送信する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sending-the-required-events"></a>必要なイベントを送信します。
必要なイベントを送信するためには、この手順を使用します。  
  
## <a name="process-for-sending-required-events"></a>必要なイベントを送信するためのプロセス  
 次のイベントは、この順番に、エンジン (DE) のデバッグを作成するときに、プログラムに接続し、必要があります。  
  
1.  送信、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)セッション デバッグ マネージャー (SDM) のプロセスで 1 つまたは複数のプログラムをデバッグするため、DE が初期化されるときにイベント オブジェクトです。  
  
2.  デバッグするプログラムに関連付けられている場合は、送信、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM にイベント オブジェクトです。 このイベントには、エンジン設計に応じて、停止イベント可能性があります。  
  
3.  接続する場合、プログラムをプロセスが起動されたときに、送信、 [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)新しいスレッドの IDE に通知する SDM にイベント オブジェクトです。 このイベントには、エンジン設計に応じて、停止イベント可能性があります。  
  
4.  送信、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) SDM デバッグ中のプログラムが終了の読み込みまたはプログラムへのアタッチが完了したときにイベント オブジェクトです。 このイベントは、停止イベントである必要があります。  
  
5.  デバッグするアプリケーションを起動する場合は、送信、 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) SDM ランタイム アーキテクチャでは、コードの最初の命令が実行されるときにイベント オブジェクトです。 このイベントは、常に、停止イベントです。 デバッグ セッションにステップ イン、ときに、IDE は、このイベントを停止します。  
  
> [!NOTE]
>  多くの言語は、そのコードの先頭にグローバル初期化子、または (CRT ライブラリまたは _Main) から、外部のプリコンパイル済みの関数を使用します。 デバッグ中のプログラムの言語には、これらの型の最初のエントリ ポイントの前に要素のいずれかが含まれています、し、このコードが実行され、エントリ ポイント イベントが送信される場合、ユーザーのエントリ ポイントなど**メイン**または`WinMain`、達しています。  
  
## <a name="see-also"></a>関連項目  
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)