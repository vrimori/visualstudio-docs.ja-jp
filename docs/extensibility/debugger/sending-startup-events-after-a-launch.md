---
title: "スタートアップ イベントを起動後に送信する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0620821ec908deed2c57ddfefb40763a48fd2074
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sending-startup-events-after-a-launch"></a>スタートアップ イベントを起動後に送信します。
デバッグ エンジン (DE) がプログラムにアタッチされる、デバッグ セッションに戻す、一連のスタートアップ イベントを送信します。  
  
 スタートアップ イベント、デバッグ セッションに送信される、次のとおりです。  
  
-   エンジンの作成イベントです。  
  
-   プログラムの作成イベントです。  
  
-   スレッドの作成やモジュール読み込みイベント。  
  
-   送信されたコードが読み込まれ、実行する準備が任意のコードが実行される前に、読み込み完了イベント  
  
    > [!NOTE]
    >  このイベントを続行すると、グローバル変数は初期化され、スタートアップ ルーチンを実行します。  
  
-   可能なその他のスレッドの作成とモジュール読み込みイベント。  
  
-   プログラムに達したことのメイン エントリ ポイントなどの通知をエントリ ポイント イベント、 **Main**または`WinMain`です。 このイベントは通常、デが既に実行されているプログラムにアタッチする場合は送信されません。  
  
 セッションのデバッグ マネージャー (SDM) が最初に送信、DE、プログラムによって、 [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)エンジン作成イベントを表すインターフェイスが続く、 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)、プログラムの作成イベントを表します。  
  
 これは通常続く 1 つまたは複数[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)スレッド作成イベントと[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)モジュール読み込みイベント。  
  
 コードが読み込まれ、実行、準備ができて場合は、DE 送信、SDM で任意のコードが実行される前に、 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)完了イベントをロードします。 最後に、プログラムが既に実行されていない場合、DE 送信、 [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)エントリ ポイント イベント、プログラムのメイン エントリ ポイントに達して、およびデバッグの準備ができているを通知します。  
  
## <a name="see-also"></a>関連項目  
 [実行の制御](../../extensibility/debugger/control-of-execution.md)   
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)