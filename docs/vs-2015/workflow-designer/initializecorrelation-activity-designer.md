---
title: InitializeCorrelation アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 314b5de716017d4c5c40653eed678626f00c20ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548831"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation アクティビティ デザイナー
**InitializeCorrelation**作成および構成するアクティビティ デザイナーが使用される、<xref:System.ServiceModel.Activities.InitializeCorrelation>送信および受信する前にメッセージ間の相関関係を確立するために使用されるアクティビティ。  
  
## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation アクティビティ  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用すると、メッセージが送受信されずに関連付けが初期化されます。 通常、関連付けはメッセージを送受信するときに初期化されます。 メッセージを送受信する前に関連付けを確立する必要がある場合は、<xref:System.ServiceModel.Activities.InitializeCorrelation> を使用して関連付けを初期化できます。  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation アクティビティ デザイナーの使用  
 **InitializeCorrelation**アクティビティ デザイナーが記載されて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブで、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **InitializeCorrelation**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面。 これを作成、 <xref:System.ServiceModel.Activities.InitializeCorrelation> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>InitializeCorrelation.The の<xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InitializeCorrelation**アクティビティ デザイナーまたは、 **DisplayName**のボックス、**プロパティ**ウィンドウ。  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle>できますでを指定します、**相関**フィールドに**プロパティ**上のウィンドウ、 **InitializeCorrelation**アクティビティ デザイナー画面。  
  
 だけでなく、省略記号ボタンをクリックすると、 **CorrelationData**フィールドに**プロパティ**ウィンドウまたは「表示…」 ヒント テキスト**InitializeCorrelation**アクティビティ デザイナー画面が表示されます、**関連付けの初期化**関連付けハンドルとするために使用するキーと値のペアを指定できるダイアログ ボックスこれを初期化します。 [!INCLUDE[crabout](../includes/crabout-md.md)] このダイアログ ボックスを使用して参照してください、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピック。  
  
### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation プロパティ  
 次の表に、<xref:System.ServiceModel.Activities.InitializeCorrelation> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティを編集できます**プロパティ**ウィンドウか、または[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの表示名。 既定値は InitializeCorrelation です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|関連付け内のワークフロー アクティビティを関連付けるために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|メッセージをワークフロー インスタンスに関連付ける、関連付けデータのディクショナリ。<br /><br /> 使用して、**関連付けの初期化**を構成するダイアログ ボックス、<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>します。 [!INCLUDE[crabout](../includes/crabout-md.md)] 使用してこのダイアログ ボックスを参照してください、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピック。|  
  
## <a name="see-also"></a>関連項目  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [受信](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [送信](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)