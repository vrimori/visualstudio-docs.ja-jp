---
title: "While アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# While アクティビティ デザイナー
<xref:System.Activities.Statements.While> アクティビティでは、指定した <xref:System.Activities.Statements.Condition%2A> が **true** に評価される場合に、<xref:System.Activities.Statements.While.Body%2A> に含まれるアクティビティを実行します。場合によっては、含まれているアクティビティが実行されない可能性があります。含まれているアクティビティを少なくとも 1 回は実行する必要がある場合は、<xref:System.Activities.Statements.DoWhile> アクティビティを代わりに使用します。  
  
## ワークフロー デザイナーでの While のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.While> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|ヘッダーの <xref:System.Activities.Statements.While> アクティビティ デザイナーの表示名を指定します。既定値は While です。この値は、**\[プロパティ\]** ウィンドウで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.While.Body%2A>|省略可|<xref:System.Activities.Statements.Condition%2A> が **true** に評価される場合に実行されるアクティビティが含まれます。|  
|<xref:System.Activities.Statements.Condition%2A>|必須|<xref:System.Activities.Statements.While.Body%2A> に含まれるアクティビティを実行するかどうかを決定するために評価される [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の式が含まれます。|  
  
## 参照  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)