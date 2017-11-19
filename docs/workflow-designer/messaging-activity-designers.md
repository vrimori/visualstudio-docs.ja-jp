---
title: "メッセージング アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2aa2383326682dcedbb0888f5b55d34e3894327c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="messaging-activity-designers"></a>メッセージング アクティビティ デザイナー
Messaging アクティビティ デザイナーは、[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] アプリケーション内から [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] メッセージを送受信するメッセージング アクティビティを作成および構成するために使用します。 [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] には、5 つのメッセージング アクティビティが導入され、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]には、ワークフロー内でメッセージングを管理できるようにする 2 つの新しいテンプレート デザイナーが用意されています。 次の表に示す、このセクションに含まれるトピックでは、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のアクティビティ デザイナーおよびテンプレート デザイナーの使用方法についてのガイドラインを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|メッセージ アクティビティ|説明|  
|----------------------|-----------------|  
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|<xref:System.ServiceModel.Activities.CorrelationScope> オブジェクトを使用して、子メッセージング アクティビティを暗黙で管理する <xref:System.ServiceModel.Activities.CorrelationHandle> アクティビティを作成および構成します。|  
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|メッセージを送受信せずに関連付けを初期化するために使用する <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを作成および構成します。|  
|[受信](../workflow-designer/receive-activity-designer.md)|サービスからメッセージを受信する <xref:System.ServiceModel.Activities.Receive> アクティビティを作成および構成します。|  
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|<xref:System.ServiceModel.Activities.Send> アクティビティ内に、定義済みの <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティと <xref:System.Activities.Statements.Sequence> アクティビティのペアを作成します。|  
|[送信](../workflow-designer/send-activity-designer.md)|サービスにメッセージを送信する <xref:System.ServiceModel.Activities.Send> アクティビティを作成および構成します。|  
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|<xref:System.ServiceModel.Activities.Receive> アクティビティ内に、定義済みの <xref:System.ServiceModel.Activities.SendReply> アクティビティと <xref:System.Activities.Statements.Sequence> アクティビティのペアを作成します。|  
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|ワークフローへのトランザクションのフローを可能にする <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを作成および構成します。|  
  
## <a name="reference"></a>参照  
 <xref:System.Activities.Activity>  
  
 <xref:System.ServiceModel.Activities.CorrelationScope>  
  
 <xref:System.ServiceModel.Activities.Receive>  
  
 <xref:System.ServiceModel.Activities.Send>  
  
 <xref:System.ServiceModel.Activities.ReceiveReply>  
  
 <xref:System.ServiceModel.Activities.SendReply>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>  
  
## <a name="related-sections"></a>関連項目  
 他の種類のアクティビティ デザイナーについては、次のトピックを参照してください。  
  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)  
  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)  
  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)  
  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)  
  
 [コレクション](../workflow-designer/collection-activity-designers.md)  
  
 [エラー処理](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>外部リソース  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)