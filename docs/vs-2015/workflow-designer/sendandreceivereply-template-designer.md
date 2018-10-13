---
title: SendAndReceiveReply テンプレート デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.SendAndReceiveReply.UI
- System.ServiceModel.Activities.ReceiveReply.UI
ms.assetid: 818a8c84-6593-416d-b016-1d91b85ffb68
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b68eea331c58c0fa2b8249293bda0cfb974b1b42
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234599"
---
# <a name="sendandreceivereply-template-designer"></a>SendAndReceiveReply テンプレート デザイナー
**SendAndReceiveReply**のペアを作成するテンプレートが使用される事前構成済み<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>内のアクティビティを<xref:System.Activities.Statements.Sequence>要求/応答メッセージ交換の一部として関連付けられるアクティビティクライアントのパターン。  
  
## <a name="the-sendandreceivereply-template"></a>SendAndReceiveReply テンプレート  
 追加**SendAndReceiveReply**テンプレートは次の 3 つ作成されるほか、<xref:System.ServiceModel.Activities.Send>と<xref:System.ServiceModel.Activities.ReceiveReply>内のアクティビティを<xref:System.Activities.Statements.Sequence>アクティビティ。  
  
1.  <xref:System.ServiceModel.Activities.Send.OperationName%2A> アクティビティの <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> プロパティと <xref:System.ServiceModel.Activities.Send> プロパティを構成する。  
  
2.  <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> アクティビティの <xref:System.ServiceModel.Activities.ReceiveReply> プロパティを <xref:System.ServiceModel.Activities.Send> アクティビティにバインドする。  
  
3.  親アクティビティに、変数として <xref:System.ServiceModel.Activities.CorrelationHandle> を作成する。  
  
### <a name="using-the-sendandreceivereply-template-designer"></a>SendAndReceiveReply テンプレート デザイナーの使用  
 **SendAndReceiveReply**アクティビティ デザイナーが記載されて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **SendAndReceiveReply**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 これを作成、<xref:System.ServiceModel.Activities.Send>アクティビティで構成できる、**送信**アクティビティ デザイナーと、相関<xref:System.ServiceModel.Activities.ReceiveReply>で構成できる、 **ReceiveReplyForSend**デザイナー。  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用して、**送信**を構成するデザイナー、<xref:System.ServiceModel.Activities.Send>アクティビティを参照してください、[送信](../workflow-designer/send-activity-designer.md)トピック。  
  
 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用して、 **ReceiveReplyForSend**を構成するデザイナー、<xref:System.ServiceModel.Activities.ReceiveReply>アクティビティでは、次のセクションを参照してください。  
  
### <a name="properties-of-receivereply"></a>ReceiveReply のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.ReceiveReply> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.ReceiveReply> アクティビティの省略可能な表示名。 既定値は、ReceiveReplyForSend です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>|True|この <xref:System.ServiceModel.Activities.Send> アクティビティと関連付けられる <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティへの参照。 このプロパティがある必要がありますいない**null**します。 <xref:System.ServiceModel.Activities.Send> アクティビティと <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティは、要求/応答メッセージ パターンをモデル化するためにクライアントで一緒に使用されます。 このプロパティでは、関連付ける <xref:System.ServiceModel.Activities.Send> アクティビティを指定します。 このプロパティは、<xref:System.ServiceModel.Activities.Send> アクティビティの作成元である <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティに自動的にバインドされるため、デザイナーでは編集できません。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Content%2A>|False|受信するメッセージまたはパラメーターの内容を指定します。 <xref:System.ServiceModel.Activities.ReceiveMessageContent> アクティビティまたは <xref:System.ServiceModel.Activities.ReceiveParametersContent> アクティビティを指定できます。 このプロパティの横にある省略記号ボタンをクリックして編集、**コンテンツ**フィールドにプロパティ グリッドまたはをクリックすると、**を定義する.** ボタンの横にある、**コンテンツ**のラベルを**受信**アクティビティ デザイナー画面。 両方を表示、**コンテンツ定義**ダイアログ。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用して、表示する方法、[コンテンツ定義 ダイアログ ボックス](../workflow-designer/content-definition-dialog-box.md)トピック。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.CorrelationInitializers%2A>|False|ワークフロー内のこの <xref:System.ServiceModel.Activities.CorrelationInitializer> アクティビティを構成する複数の <xref:System.ServiceModel.Activities.CorrelationHandle> オブジェクトを初期化する <xref:System.ServiceModel.Activities.Receive> オブジェクトのコレクションを指定します。 横にある省略記号ボタンをクリックして、<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>プロパティを開く [プロパティ] グリッドで、 **[関連付け初期化子**] ダイアログ ボックス。 [!INCLUDE[crabout](../includes/crabout-md.md)] このボックスを使用して参照してください、[関連付け初期化子の追加 ダイアログ ボックス](../workflow-designer/add-correlationinitializers-dialog-box.md)トピック。|  
|<xref:System.ServiceModel.Activities.ReceiveReply.Action%2A>|False|メッセージのアクション ヘッダーを指定します。 これを明示的に設定しない場合は、次の既定値が設定されます。<br /><br /> **https://tempuri.org/{service コントラクトの名前空間}/{サービス コントラクト名}/操作 {name} です。**|  
  
## <a name="see-also"></a>関連項目  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [受信](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [送信](../workflow-designer/send-activity-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)