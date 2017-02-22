---
title: "SendAndReceiveReply テンプレート デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.SendAndReceiveReply.UI"
  - "System.ServiceModel.Activities.ReceiveReply.UI"
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# SendAndReceiveReply テンプレート デザイナー
**SendAndReceiveReply** テンプレートは、<xref:System.Activities.Statements.Sequence> アクティビティ内に、クライアントでの要求\/応答メッセージ交換パターンの一部として関連付けられる、定義済みの <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティのペアを作成するために使用します。  
  
## SendAndReceiveReply テンプレート  
 **SendAndReceiveReply** テンプレートを追加すると、<xref:System.Activities.Statements.Sequence> アクティビティ内に <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティが作成されるほかに、次の 3 つの処理が実行されます。  
  
1.  <xref:System.ServiceModel.Activities.Send> アクティビティの <xref:System.ServiceModel.Activities.Send.OperationName%2A> プロパティと <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> プロパティを構成する。  
  
2.  <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。  
  
3.  親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。  
  
### SendAndReceiveReply テンプレート デザイナーの使用  
 **SendAndReceiveReply** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **SendAndReceiveReply** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所にドロップできます。この操作により、**Send** アクティビティ デザイナーで構成できる <xref:System.ServiceModel.Activities.Send> アクティビティと、**ReceiveReplyForSend** デザイナーで構成可能な関連する <xref:System.ServiceModel.Activities.ReceiveReply> が作成されます。  
  
 **Send** デザイナーを使用して <xref:System.ServiceModel.Activities.Send> アクティビティを構成する方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[Send](../workflow-designer/send-activity-designer.md)」を参照してください。  
  
 **ReceiveReplyForSend** デザイナーを使用して <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティを構成する方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、次のセクションを参照してください。  
  
### ReceiveReply のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.ReceiveReply> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの省略可能な表示名。既定値は、ReceiveReplyForSend です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|必須|この <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.Send> アクティビティへの参照。このプロパティには、**null** を指定できません。<xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、要求\/応答メッセージ パターンをモデル化するためにクライアントで一緒に使用されます。このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。このプロパティは、<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの作成元である <xref:System.ServiceModel.Activities.Send> アクティビティに自動的にバインドされるため、デザイナーでは編集できません。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|省略可|受信するメッセージまたはパラメーターの内容を指定します。<xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。このプロパティを編集するには、プロパティ グリッドで **\[Content\]** フィールドの横にある省略記号ボタンをクリックするか、**Receive** アクティビティ デザイナー画面で "**コンテンツ**" というラベルの横にある **\[定義\]** ボタンをクリックします。両方で **\[コンテンツ定義\]** ダイアログが表示されます。このダイアログ ボックスの使用方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[コンテンツ定義\] ダイアログ ボックス](../Topic/Content%20Definition%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|省略可|ワークフロー内のこの <xref:System.ServiceModel.Activities.Receive> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.CorrelationInitializer> オブジェクトのコレクションを指定します。プロパティ グリッドで <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> プロパティの横にある省略記号ボタンをクリックして、**\[関連付け初期化子の追加\]** ダイアログ ボックスを開きます。このボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[関連付け初期化子の追加\] ダイアログ ボックス](../Topic/Add%20CorrelationInitializers%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|省略可|メッセージのアクション ヘッダーを指定します。これを明示的に設定しない場合は、次の既定値が設定されます。<br /><br /> **https:\/\/tempuri.org\/\<サービス コントラクトの名前空間\>\/\<サービス コントラクト名\>\/\<操作名\>。**|  
  
## 参照  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)