---
title: "InitializeCorrelation アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.InitializeCorrelation.UI"
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# InitializeCorrelation アクティビティ デザイナー
**InitializeCorrelation** アクティビティ デザイナーを使用して <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティが作成および構成され、このアクティビティを使用して、送信または受信の前にメッセージ間の関連付けが確立されます。  
  
## InitializeCorrelation アクティビティ  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用すると、メッセージが送受信されずに関連付けが初期化されます。通常、関連付けはメッセージを送受信するときに初期化されます。メッセージを送受信する前に関連付けを確立する必要がある場合は、<xref:System.ServiceModel.Activities.InitializeCorrelation> を使用して関連付けを初期化できます。  
  
### InitializeCorrelation アクティビティ デザイナーの使用  
 **InitializeCorrelation** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **InitializeCorrelation** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面にドロップできます。この操作により、InitializeCorrelation という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**InitializeCorrelation** アクティビティ デザイナーのヘッダー、または **\[プロパティ\]** ウィンドウの **\[DisplayName\]** ボックスで編集できます。  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle> は、**InitializeCorrelation** アクティビティ デザイナー画面の **\[プロパティ\]** ウィンドウの **\[関連付け\]** フィールドで指定できます。  
  
 **\[プロパティ\]** ウィンドウ内の **CorrelationData** フィールドの横にある省略記号ボタン、または **InitializeCorrelation** アクティビティ デザイナー画面の "表示…" ヒント テキストをクリックすると、**\[関連付けの初期化\]** ダイアログ ボックスが表示され、ここで、関連付けハンドルとそれを初期化するために使用するキー\/値ペアを指定できます。このダイアログ ボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[型コレクション エディター\] ダイアログ ボックス](../Topic/Type%20Collection%20Editor%20Dialog%20Box.md)」を参照してください。  
  
### InitializeCorrelation プロパティ  
 次の表に、<xref:System.ServiceModel.Activities.InitializeCorrelation> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、**\[プロパティ\]** ウィンドウまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの表示名。既定値は InitializeCorrelation です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用をお勧めします。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|省略可|関連付け内のワークフロー アクティビティを関連付けるために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|省略可|メッセージをワークフロー インスタンスに関連付ける、関連付けデータのディクショナリ。<br /><br /> <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> を構成するには **\[関連付け初期化\]** ダイアログ ボックスを使用します。このダイアログ ボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[型コレクション エディター\] ダイアログ ボックス](../Topic/Type%20Collection%20Editor%20Dialog%20Box.md)」を参照してください。|  
  
## 参照  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)