---
title: "イベントの送信 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2bfdefc3202a026516edb3f9221e0626e1a83b4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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