---
title: "CancellationScope アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.CancellationScope.UI"
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# CancellationScope アクティビティ デザイナー
**CancellationScope** アクティビティ デザイナーは、<xref:System.Activities.Statements.CancellationScope> アクティビティを作成および構成するために使用します。  
  
## CancellationScope アクティビティ  
 <xref:System.Activities.Statements.CancellationScope> アクティビティを使用すると、実行のアクティビティと、そのアクティビティの取り消しロジックを指定できます。  
  
### CancellationScope アクティビティ デザイナーの使用  
 **CancellationScope** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[トランザクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **CancellationScope** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、CancellationScope という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.CancellationScope> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**CancellationScope** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### CancellationScope プロパティ  
 次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。<xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドで編集できますが、それ以外のプロパティは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集する必要があります。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.CancellationScope> アクティビティの省略可能な表示名。既定では、CancellationScope です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|必須|取り消しロジックの対象となるアクティビティを指定します。<xref:System.Activities.Statements.CancellationScope.Body%2A> アクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **CancellationScope** アクティビティ デザイナーの **\[Body\]** ボックスに、**\[ツールボックス\]** からアクティビティをドロップします。|  
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|取り消しの際に実行されるアクティビティを指定します。<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> アクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **CancellationScope** アクティビティ デザイナーの **\[CancellationHandler\]** ボックスに、**\[ツールボックス\]** からアクティビティをドロップします。|  
  
## 参照  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)