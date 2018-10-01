---
title: TransactedReceiveScope アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a40f29bc9928d354d99be282e5cd4ea32f869270
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533626"
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナー
**TransactedReceiveScope**を作成および構成デザイナーを使用する<xref:System.ServiceModel.Activities.TransactedReceiveScope>アクティビティ。  
  
## <a name="the-transactedreceivescope-activity"></a>TransactedReceiveScope アクティビティ  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを使用すると、ワークフローまたはディスパッチャーによって作成されたサーバー トランザクションにトランザクションをフローできます。  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>TransactedReceiveScope アクティビティ デザイナーの使用  
 **TransactedReceiveScope**アクティビティ デザイナーが記載されて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **TransactedReceiveScope**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス場所でアクティビティを通常配置しています。 これを作成、 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 、既定値は、アクティビティ**DisplayName** TransactedReceiveScope の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TransactedReceiveScope**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
 **TransactedReceiveScope**デザイナーに**要求**と**本文**ボックス。 これらは、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> プロパティを構成するために使用します。このプロパティでは、<xref:System.ServiceModel.Activities.Receive> アクティビティと、他の <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> を指定する <xref:System.Activities.Activity> プロパティを指定します。 <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> によって、トランザクションが作成されます。 その後、トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> のスコープ内のあらゆるアクティビティは、このトランザクション内で実行されます。  
  
### <a name="the-transactedreceivescope-properties"></a>TransactedReceiveScope のプロパティ  
 次の表に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドまたは[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面で編集できますが、他のプロパティはデザイン画面で編集する必要があります。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティの省略可能な表示名。 既定値は、TransactedReceiveScope です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> 名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|削除操作を行う、<xref:System.ServiceModel.Activities.Receive>にアクティビティ、**要求**アクティビティ デザイナー画面にブロックします。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|削除操作を行う、<xref:System.Activities.Activity>に、**本文**アクティビティ デザイナー画面にブロックします。|  
  
## <a name="see-also"></a>関連項目  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [受信](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [送信](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)