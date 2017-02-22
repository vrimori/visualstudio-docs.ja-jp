---
title: "ReceiveAndSendReply テンプレート デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.ServiceModel.Activities.ReceiveAndSendReply.UI"
  - "System.ServiceModel.Activities.SendReply.UI"
ms.assetid: d1d9a058-df7e-48f5-a2e7-3caeeba7eaa6
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ReceiveAndSendReply テンプレート デザイナー
**ReceiveAndSendReply** テンプレートは、<xref:System.Activities.Statements.Sequence> アクティビティ内に、サーバーでの要求\/応答メッセージ交換パターンの一部として関連付けられる、定義済みの <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティのペアを作成するために使用します。  
  
## ReceiveAndSendReply テンプレート  
 **ReceiveAndSendReply** テンプレートを追加すると、<xref:System.Activities.Statements.Sequence> アクティビティ内に <xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティが作成されるほかに、次の 3 つの処理が実行されます。  
  
1.  <xref:System.ServiceModel.Activities.Receive> アクティビティの <xref:System.ServiceModel.Activities.Receive.OperationName%2A> プロパティと <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> プロパティを構成する。  
  
2.  <xref:System.ServiceModel.Activities.Receive> アクティビティの <xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。  
  
3.  親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。  
  
### ReceiveAndSendReply テンプレート デザイナーの使用  
 **ReceiveAndSendReply** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[メッセージング\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **ReceiveAndSendReply** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所にドロップできます。この操作により、**Send** アクティビティ デザイナーで構成できる <xref:System.ServiceModel.Activities.Receive> アクティビティと、SendReplyToReceive デザイナーで構成できる関連付けられた <xref:System.ServiceModel.Activities.SendReply> が作成されます。  
  
 **Receive** デザイナーを使用して <xref:System.ServiceModel.Activities.Receive> アクティビティを構成する方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[Receive](../workflow-designer/receive-activity-designer.md)」を参照してください。  
  
 **SendReplyToReceive** デザイナーを使用して <xref:System.ServiceModel.Activities.SendReply> アクティビティを構成する方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、次のセクションを参照してください。  
  
### SendReply のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.SendReply> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.ServiceModel.Activities.SendReply> アクティビティの省略可能な表示名。既定値は SendReplyToReceive です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.SendReply.Request%2A>|必須|この <xref:System.ServiceModel.Activities.SendReply> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.Receive> アクティビティへの参照。このプロパティには、**null** を指定できません。<xref:System.ServiceModel.Activities.Receive> アクティビティと <xref:System.ServiceModel.Activities.SendReply> アクティビティは、要求\/応答メッセージ パターンをモデル化するためにサーバーで一緒に使用されます。このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。このプロパティは、<xref:System.ServiceModel.Activities.SendReply> アクティビティの作成元である <xref:System.ServiceModel.Activities.Send> アクティビティに自動的にバインドされるため、デザイナーでは編集できません。|  
|<xref:System.ServiceModel.Activities.SendReply.Content%2A>|省略可|受信するメッセージまたはパラメーターの内容を指定します。<xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。このプロパティを編集するには、プロパティ グリッドで **\[Content\]** フィールドの横にある省略記号ボタンをクリックするか、**Receive** アクティビティ デザイナー画面で "**コンテンツ**" というラベルの横にある **\[定義\]** ボタンをクリックします。両方で **\[コンテンツ定義\]** ダイアログが表示されます。このダイアログ ボックスの使用方法[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[コンテンツ定義\] ダイアログ ボックス](../Topic/Content%20Definition%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A>|省略可|ワークフロー内のこの <xref:System.ServiceModel.Activities.Receive> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.CorrelationInitializer> オブジェクトのコレクションを指定します。プロパティ グリッドで <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> プロパティの横にある省略記号ボタンをクリックして、**\[関連付け初期化子の追加\]** ダイアログ ボックスを開きます。このボックスの使用[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[\[関連付け初期化子の追加\] ダイアログ ボックス](../Topic/Add%20CorrelationInitializers%20Dialog%20Box.md)」を参照してください。|  
|<xref:System.ServiceModel.Activities.SendReply.Action%2A>|省略可|メッセージのアクション ヘッダーを指定します。これを明示的に設定しない場合は、次の既定値が設定されます。<br /><br /> **https:\/\/tempuri.org\/\<サービス コントラクトの名前空間\>\/\<サービス コントラクト名\>\/\<操作名\>。**|  
|<xref:System.ServiceModel.Activities.SendReply.PersistBeforeSend%2A>|False|応答メッセージを送信する前にワークフロー サービス インスタンスを永続化するかどうかを指定します。既定値は **false** です。|  
  
## 参照  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Receive](../workflow-designer/receive-activity-designer.md)   
 [Send](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)