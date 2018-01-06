---
title: "InitializeCorrelation アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 83abd9f76f68ec4131840fb0ea58e9aeb93f30d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation アクティビティ デザイナー
**InitializeCorrelation**アクティビティ デザイナーを使用して作成し、構成、<xref:System.ServiceModel.Activities.InitializeCorrelation>送信または受信する前にメッセージ間の相関関係を確立するために使用されるアクティビティ。  
  
## <a name="the-initializecorrelation-activity"></a>InitializeCorrelation アクティビティ  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティを使用すると、メッセージが送受信されずに関連付けが初期化されます。 通常、関連付けはメッセージを送受信するときに初期化されます。 メッセージを送受信する前に関連付けを確立する必要がある場合は、<xref:System.ServiceModel.Activities.InitializeCorrelation> を使用して関連付けを初期化できます。  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>InitializeCorrelation アクティビティ デザイナーの使用  
 **InitializeCorrelation**アクティビティ デザイナーは含まれて、**メッセージング**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブで、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。  
  
 **InitializeCorrelation**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面。 これを作成、 <xref:System.ServiceModel.Activities.InitializeCorrelation> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>InitializeCorrelation.The の<xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **InitializeCorrelation**アクティビティ デザイナーまたは、 **DisplayName**のボックス、**プロパティ**ウィンドウです。  
  
 <xref:System.ServiceModel.Activities.CorrelationHandle>できますでを指定します、**相関**フィールドに**プロパティ**上のウィンドウ、 **InitializeCorrelation**アクティビティ デザイナー画面。  
  
 他の省略記号ボタンをクリックすると、 **CorrelationData**フィールドに**プロパティ**ウィンドウまたは上の「表示…」ヒント テキスト**InitializeCorrelation**アクティビティ デザイナー画面が表示されます、**関連付けの初期化** ダイアログ ボックスの関連付けハンドルとそれを初期化するために使用されるキー/値ペアを指定できます。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]このダイアログ ボックスを使用して参照してください、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピックです。  
  
### <a name="the-initializecorrelation-properties"></a>InitializeCorrelation プロパティ  
 次の表に、<xref:System.ServiceModel.Activities.InitializeCorrelation> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティを編集できます**プロパティ**ウィンドウまたは [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.ServiceModel.Activities.InitializeCorrelation> アクティビティの表示名。 既定値は InitializeCorrelation です。<br /><br /> 既定値以外の <xref:System.Activities.Activity.DisplayName%2A> の使用は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|関連付け内のワークフロー アクティビティを関連付けるために使用される <xref:System.ServiceModel.Activities.CorrelationHandle>。|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|メッセージをワークフロー インスタンスに関連付ける、関連付けデータのディクショナリ。<br /><br /> 使用して、**関連付けの初期化**を構成するダイアログ ボックス、<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>です。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]使用するこのダイアログ ボックスを参照してください、[型コレクション エディター ダイアログ ボックス](../workflow-designer/type-collection-editor-dialog-box.md)トピックです。|  
  
## <a name="see-also"></a>参照  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [受信](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [送信](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)