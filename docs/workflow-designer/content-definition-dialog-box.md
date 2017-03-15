---
title: "[コンテンツ定義] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "MessageContent.UI"
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# [コンテンツ定義] ダイアログ ボックス
**\[コンテンツ定義\]** ダイアログ ボックスは [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] で <xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply>、および <xref:System.ServiceModel.Activities.ReceiveReply> の各アクティビティの **Content** プロパティを構成するために使用されます。このダイアログ ボックスを使用するアクティビティ デザイナー[!INCLUDE[crabout](../test/includes/crabout_md.md)]、「[Send](../workflow-designer/send-activity-designer.md)」、「[Receive](../workflow-designer/receive-activity-designer.md)」、「[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)」および「[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)」を参照してください。  
  
 次の表に、**\[関連付けの初期化\]** ダイアログ ボックスのユーザー インターフェイス \(UI\) 要素を示します。  
  
|UI 要素|説明|  
|-----------|--------|  
|**メッセージ**|**\[メッセージ データ\]** 式テキスト ボックスでメッセージの内容を指定し、**\[メッセージ型\]** ボックスを使用して種類を指定します。**\[コンテンツ定義\]** では、既定で、ワークフロー サービス定義内の <xref:System.ServiceModel.Channels.Message> またはメッセージ コントラクト型を受け取る <xref:System.ServiceModel.Activities.ReceiveMessageContent> が使用されます。|  
|**パラメーター**|**\[パラメーター\]** オプション ボタンをクリックすると、データ コントラクトを受け取る <xref:System.ServiceModel.Activities.ReceiveParametersContent> が使用されます。<xref:System.Activities.OutArgument> キーおよび値のペアのジェネリック コレクションを設定するには、データ グリッドを使用します。これらの値は、現在のワークフローの変数パラメーターに割り当てられます。|  
  
 **\[コンテンツ定義\]** ダイアログ ボックスは、**Send**、**Receive**、**ReceiveAndSendReply**、および **SendAndReceiveReply** の各デザイナーで使用されます。デザイナーへのアクセス方法は、どの場合も同様です。ここでは、Receive デザイナーを使用する例で手順を説明します。  
  
 **Receive** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所にドロップできます。この操作により、Receive という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.ServiceModel.Activities.Receive> アクティビティが作成されます。**Receive** アクティビティ デザイナーを選択し、プロパティ グリッドで **Content** プロパティの "\(コンテンツ\)" というテキストの横にある省略記号ボタンをクリックして、**\[コンテンツ定義\]** ダイアログ ボックスを表示します。  
  
 コンテンツは、<xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティの **\[メッセージ\]** セクション内、または <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティの **\[パラメーター\]** セクション内で指定できます。  
  
## 参照  
 [ワークフロー デザイナーの UI ヘルプ](../workflow-designer/workflow-designer-ui-help.md)