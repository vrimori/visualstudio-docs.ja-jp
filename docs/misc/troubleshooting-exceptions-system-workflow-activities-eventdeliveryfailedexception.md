---
title: "例外のトラブルシューティング : System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException 例外"
  - "EventDeliveryFailedException 例外"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Workflow.Activities.EventDeliveryFailedException
<xref:System.Workflow.Activities.EventDeliveryFailedException> 例外は、ホストから発生したイベントをワークフロー インスタンスに配信できなかった場合にスローされます。 通常、このイベントは、ワークフロー インスタンスの <xref:System.Workflow.Activities.ExternalDataExchangeService> から発生します。 このクラスは継承できません。  
  
## コメント  
 この例外がスローされると、イベント ログに `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered` という文字列が追加されます。  
  
 ステート マシン ワークフローを使用している場合は、`Queue '{0}' is not enabled` というメッセージを含んだ例外を受け取ることがあります。 これは、ステート マシンの現在の状態では特定のイベントを処理できない場合に発生します。 たとえば、現在の状態を除くいずれかの状態に、キュー <xref:System.Workflow.Activities.EventDrivenActivity> で表される <xref:System.Workflow.Activities.HandleExternalEventActivity> を含む `'{0}'` が含まれるような場合に、このメッセージが発生します。  
  
## 参照  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)