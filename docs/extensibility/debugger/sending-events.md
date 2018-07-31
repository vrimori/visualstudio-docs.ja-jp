---
title: イベントの送信 |Microsoft Docs
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
ms.openlocfilehash: 87087a2087591b01170b82c0335e4bbffc579cc2
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252454"
---
# <a name="send-events"></a>イベントを送信します。
デバッガーとデバッグ エンジン (DE) 間の通信メカニズムは、DCOM に基づいてイベント モデル。 イベントは、COM オブジェクトとして送信され、各イベントを指定するパラメーターには。  
  
-   この DE イベントと呼ばれます。  
  
-   変更点の説明。  
  
-   プロセス、プログラム、およびイベントの発生場所のコンテキストを識別するスレッドの情報。 プロセスは、ドイツから送信されたイベントは送信されません。  
  
-   イベントが同期または非同期であるかどうかを示すイベントの種類。  
  
 メソッドを使用してすべてのデバッグ イベントが送信される[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [イベント ソース](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 イベントの 2 つのソースについて説明します。 デバッグ エンジン (DE) とセッション デバッグ マネージャー (SDM)。  
  
 [サポートされているイベントの種類](../../extensibility/debugger/supported-event-types.md)  
 現在サポートされているイベントの種類について説明します。 非同期と同期します。  
  
 [イベントの説明](../../extensibility/debugger/event-descriptions.md)  
 イベントとその使用する理由を定義します。  
  
## <a name="related-sections"></a>関連項目  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 インタープリターまたはオペレーティング システムは、デバッグ サービスを提供すると、DE のしくみについて説明します。