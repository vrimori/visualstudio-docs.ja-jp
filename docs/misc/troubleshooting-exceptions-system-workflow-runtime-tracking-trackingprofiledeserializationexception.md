---
title: "例外のトラブルシューティング : System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException | Microsoft Docs"
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
  - "EHWRTTrackingProfileDeserialization"
helpviewer_keywords: 
  - "System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException 例外"
  - "TrackingProfileDeserializationException 例外"
ms.assetid: ce8fe4c1-43e3-4930-947e-74b8d94f32bf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException
<xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException> 例外は、<xref:System.Workflow.Runtime.Tracking.TrackingProfile> によって XML ドキュメントを <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> に逆シリアル化できない場合にスローされます。  
  
## コメント  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> は、この例外をスローするときに、例外の理由を説明するメッセージを表示します。<xref:System.Workflow.Runtime.Tracking.TrackingProfileSerializer> が、<xref:System.Workflow.Runtime.Tracking.TrackingProfile> を逆シリアル化しようとした際に発生した検証エラーと警告の一覧を表示する場合もあります。 このような一覧が表示された場合、この一覧は <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException.ValidationEventArgs%2A> プロパティに格納されます。  
  
## 参照  
 <xref:System.Workflow.Runtime.Tracking.TrackingProfileDeserializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)