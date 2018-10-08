---
title: イベントの送信 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65c86cb8028d5c310de6f48c753d862865ea7a46
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546534"
---
# <a name="sending-events"></a>イベントの送信
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[イベントの送信](https://docs.microsoft.com/visualstudio/extensibility/debugger/sending-events)します。  
  
デバッガーとデバッグ エンジン (DE) 間の通信メカニズムは、DCOM に基づいてイベント モデル。 イベントは、COM オブジェクトとして送信され、各イベントには、次を指定するパラメーター。  
  
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
 [カスタム デバッグ エンジンの作成](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 インタープリターまたはオペレーティング システムは、デバッグ サービスを提供すると、DE のしくみについて説明します。

