---
title: "イベントの送信 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: edd4abfa31b309290bdb07fd98c104a279d98fc7
ms.lasthandoff: 02/22/2017

---
# <a name="sending-events"></a>イベントを送信します。
デバッガーとデバッグ エンジン (DE) 間の通信メカニズムは、DCOM に基づいてイベント モデルです。 イベントは、COM オブジェクトとして送信され、各イベントには、次を指定するパラメーター。  
  
-   イベントと呼ばれる DE します。  
  
-   変更内容の説明です。  
  
-   プロセス、プログラム、およびイベントの発生場所のコンテキストを識別するスレッドの情報です。 プロセスは、DE から送信されるイベントには送信されません。  
  
-   イベントが同期または非同期であるかどうかを示すイベントの種類。  
  
 メソッドを使用してすべてのデバッグ イベントが送信される[IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [イベント ソース](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 イベントの&2; つのソースについて説明します。 デバッグ エンジン (DE) とセッション マネージャー (SDM) をデバッグします。  
  
 [サポートされているイベントの種類](../../extensibility/debugger/supported-event-types.md)  
 現在サポートされているイベントの種類について説明します。 非同期と同期します。  
  
 [イベントの説明](../../extensibility/debugger/event-descriptions.md)  
 イベントとその使用理由を定義します。  
  
## <a name="related-sections"></a>関連項目  
 [カスタム デバッグ エンジンを作成します。](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 デバッグ サービスを提供するには、インタープリターまたはオペレーティング システムが、DE のしくみについて説明します。
