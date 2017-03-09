---
title: "例外のトラブルシューティング : System.ServiceModel.ServerTooBusyException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.ServiceModel.ServerTooBusyException 例外"
  - "ServerTooBusyException 例外"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 例外のトラブルシューティング : System.ServiceModel.ServerTooBusyException
<xref:System.ServiceModel.ServerTooBusyException> 例外は、サーバーがビジー状態であるため、メッセージを受け取ることができない場合にスローされます。  
  
## コメント  
 この例外は、エンドポイント間の通信時にスローされることがある回復可能なエラーのクラスを表す <xref:System.ServiceModel.CommunicationException> から派生します。 これらの例外は、堅牢なクライアントとサービス [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] アプリケーションによって処理されます。<xref:System.ServiceModel.CommunicationException> のハンドラーが詳細な <xref:System.ServiceModel.ServerTooBusyException> をキャッチしないようにするには、<xref:System.ServiceModel.CommunicationException> を処理する前にこの例外をキャッチします。  
  
## 参照  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)