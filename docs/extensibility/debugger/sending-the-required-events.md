---
title: "必要なイベントを送信する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f2fa28a3429c52e3d4eb8b5fc9faefbd86ee04d9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [デバッグするプログラムの有効化](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)