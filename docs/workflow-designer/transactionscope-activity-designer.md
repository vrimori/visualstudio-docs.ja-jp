---
title: "TransactionScope アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TransactionScope.UI"
ms.assetid: 8d7ebfc6-7478-4888-b3b0-b14f296096af
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionScope アクティビティ デザイナー
**TransactionScope** アクティビティ デザイナーは、<xref:System.Activities.Statements.TransactionScope> アクティビティを作成および構成するために使用します。  
  
## TransactionScope アクティビティ  
 <xref:System.Activities.Statements.TransactionScope> アクティビティでは、含まれているアクティビティを単一のトランザクションで実行します。<xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティおよびトランザクションの他のすべての参加要素が正常に完了すると、トランザクションはコミットされます。  
  
### TransactionScope アクティビティ デザイナーの使用  
 **TransactionScope** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[トランザクション\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **TransactionScope** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、TransactionScope という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.TransactionScope> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> 値は、**TransactionScope** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### TransactionScope のプロパティ  
 次の表に、<xref:System.Activities.Statements.TransactionScope> のプロパティと、デザイナーでのその使用方法を示します。<xref:System.Activities.Activity.DisplayName%2A> プロパティと <xref:System.Activities.Statements.TransactionScope.Body%2A> プロパティは、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。ただし、他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.TransactionScope> アクティビティの省略可能な表示名。既定値は、TransactionScope です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.TransactionScope.Body%2A>|必須|単一のトランザクションで実行するアクティビティを指定します。<xref:System.Activities.Statements.TransactionScope.Body%2A> アクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **TransactionScope** アクティビティ デザイナーの **\[Body\]** ボックスに、**\[ツールボックス\]** からアクティビティをドロップします。|  
|<xref:System.Activities.Statements.TransactionScope.IsolationLevel%2A>|True|この <xref:System.Activities.Statements.TransactionScope> の <xref:System.Transactions.IsolationLevel> を指定します。|  
|<xref:System.Activities.Statements.TransactionScope.Timeout%2A>|False|トランザクションが完了するまでの時間間隔を "00:00:00" \(時:分:秒\) という形式で指定します。既定値は 1 分 \(00:01:00\) です。|  
|<xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A>|True|トランザクションが中止した場合にワークフローを中止する必要があるかどうかを示す値を指定します。|  
  
## 参照  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)   
 [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)   
 [Compensate](../workflow-designer/compensate-activity-designer.md)   
 [Confirm](../workflow-designer/confirm-activity-designer.md)