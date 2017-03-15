---
title: "Compensate アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Compensate.UI"
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Compensate アクティビティ デザイナー
**Compensate** アクティビティ デザイナーは、<xref:System.Activities.Statements.Compensate> アクティビティを作成および構成するために使用します。  
  
## Compensate アクティビティ  
 <xref:System.Activities.Statements.Compensate> アクティビティは、<xref:System.Activities.Statements.CompensableActivity> に含まれているアクティビティの <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> を明示的に呼び出します。<xref:System.Activities.Statements.Compensate> アクティビティが <xref:System.Activities.Statements.CompensableActivity> の <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 内、<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 内、および <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 内のいずれでも使用されていない場合は、<xref:System.Activities.Statements.Compensate.Target%2A> プロパティを指定する必要があります。  
  
 <xref:System.Activities.Statements.Compensate.Target%2A> で指定された <xref:System.Activities.Statements.CompensationToken> は、<xref:System.Activities.Statements.CompensableActivity> の <xref:System.Activities.Statements.CompensableActivity.Body%2A> が正常に完了した後に <xref:System.Activities.Statements.CompensableActivity> を明示的に確認または補正する手段を提供します。  
  
### Compensate アクティビティ デザイナーの使用  
 **Compensate** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[トランザクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Compensate** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Compensate という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.Compensate> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**Compensate** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### Compensate のプロパティ  
 次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。<xref:System.Activities.Activity.DisplayName%2A> プロパティはプロパティ グリッドまたは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できますが、<xref:System.Activities.Statements.Compensate.Target%2A> プロパティはプロパティ グリッドで編集する必要があります。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.Compensate> アクティビティの表示名を指定します \(省略可能\)。既定値は Compensate です。|  
|<xref:System.Activities.Statements.Compensate.Target%2A>|必須|この <xref:System.Activities.Statements.Compensate> アクティビティの <xref:System.Activities.Statements.CompensationToken> を含む <xref:System.Activities.InArgument%601> を指定します。|  
  
## 参照  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate Activity Designer](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)   
 [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)