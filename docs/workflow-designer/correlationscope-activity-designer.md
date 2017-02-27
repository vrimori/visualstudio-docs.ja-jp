---
title: "CorrelationScope アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.CorrelationScope.UI"
ms.assetid: 75f20664-9042-464d-8e2b-148d365a2286
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# CorrelationScope アクティビティ デザイナー
**CorrelationScope** アクティビティ デザイナーは、<xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを使用して、子メッセージング アクティビティを暗黙で管理する <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティを作成および構成するために使用します。  
  
## CorrelationScope アクティビティ  
 <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> プロパティでは、子メッセージング アクティビティの管理に使用する <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A> に含まれる <xref:System.ServiceModel.Activities.Send> アクティビティおよび <xref:System.ServiceModel.Activities.Receive> アクティビティは、親 <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティの <xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A> プロパティを使用して関連付けを行うように構成されます。  
  
### CorrelationScope アクティビティ デザイナーの使用  
 **CorrelationScope** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **CorrelationScope** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面にドロップできます。この操作により、CorrelationScope という既定の **DisplayName** を持つ <xref:System.ServiceModel.Activities.CorrelationScope> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**CorrelationScope** アクティビティ デザイナーのヘッダー、または **\[プロパティ\]** ウィンドウの **\[DisplayName\]** ボックスで編集できます。  
  
 子メッセージング アクティビティで使用される <xref:System.ServiceModel.Activities.CorrelationHandle> を指定するには、**\[プロパティ\]** ウィンドウの **\[CorrelatesWith\]** フィールドの横にある省略記号ボタンをクリックして、**\[式エディター\]** ダイアログ ボックスを開きます。このプロパティは、アクティビティ デザイナー画面で設定することもできます。  
  
 相関関係内にスコープ設定されるアクティビティを指定するには、そのアクティビティのデザイナーを、**CorrelationScope** デザイナーの **\[Body\]** ボックス内にドラッグします。  
  
### CorrelationScope プロパティ  
 次の表に、<xref:System.ServiceModel.Activities.CorrelationScope> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、**\[プロパティ\]** ウィンドウ、または[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。多くの場合は、どちらでも編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの省略可能な表示名。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.CorrelatesWith%2A>|省略可|子メッセージング アクティビティの管理に使用する <xref:System.ServiceModel.Activities.CorrelationHandle> を指定します。このプロパティを設定しない場合は、<xref:System.ServiceModel.Activities.CorrelationScope> に、暗黙の <xref:System.ServiceModel.Activities.CorrelationHandle> が自動的に作成されます。|  
|<xref:System.ServiceModel.Activities.CorrelationScope.Body%2A>|省略可|相関関係のスコープ内のアクティビティを指定します。|  
  
## 参照  
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)