---
title: イベントの送信 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9bbe7946b866cd751be1f0dac2dba5b8dea57e04
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sending-events"></a>イベントの送信
デバッガーとデバッグ エンジン (DE) 間の通信メカニズムは DCOM に基づいてイベント モデルです。 イベントは、COM オブジェクトとして送信され、各イベントには、次を指定するパラメーター。  
  
-   イベントと呼ばれる DE です。  
  
-   何が起こったの説明です。  
  
-   プロセス、プログラム、およびイベントの発生場所のコンテキストを識別するスレッドの情報です。 プロセスは、DE から送信されるイベントの送信されません。  
  
-   イベントが同期または非同期であるかどうかを示すイベントの種類。  
  
 メソッドを使用してすべてのデバッグ イベントが送信される[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [イベント ソース](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 イベントの 2 つのソースについて説明します。 デバッグ エンジン (DE) と、セッションは、マネージャー (SDM) をデバッグします。  
  
 [サポートされているイベントの種類](../../extensibility/debugger/supported-event-types.md)  
 現在サポートされているイベントの種類について説明します。 非同期および同期します。  
  
 [イベントの説明](../../extensibility/debugger/event-descriptions.md)  
 イベントと、使用する理由を定義します。  
  
## <a name="related-sections"></a>関連項目  
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 デバッグ サービスを提供する、インタープリターまたはオペレーティング システムで、DE のしくみについて説明します。