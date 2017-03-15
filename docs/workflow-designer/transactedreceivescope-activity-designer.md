---
title: "TransactedReceiveScope アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.TransactedReceiveScope.UI"
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TransactedReceiveScope アクティビティ デザイナー
**TransactedReceiveScope** アクティビティ デザイナーは、<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを作成および構成するために使用します。  
  
## TransactedReceiveScope アクティビティ  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用すると、ワークフローまたはディスパッチャーによって作成されたサーバー トランザクションにトランザクションをフローできます。  
  
### TransactedReceiveScope アクティビティ デザイナーの使用  
 **TransactedReceiveScope** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **TransactedReceiveScope** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所にドロップできます。この操作により、TransactedReceiveScope という既定の **DisplayName** を持つ <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**TransactedReceiveScope** アクティビティ デザイナーのヘッダーか、プロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
 **TransactedReceiveScope** デザイナーには、**\[Request\]** ボックスと **\[Body\]** ボックスがあります。これらは、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> プロパティを構成するために使用します。このプロパティでは、<xref:System.ServiceModel.Activities.Receive> アクティビティと、他の <xref:System.Activities.Activity> を指定する <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> プロパティを指定します。<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> によって、トランザクションが作成されます。その後、トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> のスコープ内のあらゆるアクティビティは、このトランザクション内で実行されます。  
  
### TransactedReceiveScope のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> のプロパティと、デザイナーでのその使用方法を示します。<xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できますが、他のプロパティはデザイン画面で編集する必要があります。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの省略可能な表示名。既定値は、TransactedReceiveScope です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|必須|アクティビティ デザイナー画面の **\[Request\]** ブロックに <xref:System.ServiceModel.Activities.Receive> アクティビティをドロップします。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|省略可|<xref:System.Activities.Activity> アクティビティをアクティビティ デザイナー画面の **\[Body\]** ブロックにドロップします。|  
  
## 参照  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)