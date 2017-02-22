---
title: "If アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# If アクティビティ デザイナー
<xref:System.Activities.Statements.If> アクティビティでは、条件を評価し、その評価の結果に応じてアクティビティを実行します。このアクティビティは、手順型モデルのプログラミング スタイルを使用する場合に最も役立ちます。<xref:System.Activities.Statements.If> アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Parallel> アクティビティなどの内部に入れ子にすることができます。<xref:System.Activities.Statements.Flowchart> アクティビティを使用している場合は、代わりに、<xref:System.Activities.Statements.FlowDecision> アクティビティの使用を検討してください。  
  
## ワークフロー デザイナーでの If のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.If> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Statements.If.Condition%2A>|必須|実行する子アクティビティを決定する条件。<xref:System.Activities.Statements.If.Condition%2A> を設定するには、**If** アクティビティ デザイナーまたはプロパティ グリッドの **\[Condition\]** ボックスに [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の式を入力します。|  
|<xref:System.Activities.Statements.If.Else%2A>|省略可|<xref:System.Activities.Statements.If.Condition%2A> が **false** の場合に実行するアクティビティ。<xref:System.Activities.Statements.If.Else%2A> 分岐によって実行されるアクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **If** アクティビティ デザイナーの **\[Else\]** ボックスに、**\[ツールボックス\]** からアクティビティをドロップします。|  
|<xref:System.Activities.Statements.If.Then%2A>|False|<xref:System.Activities.Statements.If.Condition%2A> が **true** の場合に実行するアクティビティ。<xref:System.Activities.Statements.If.Then%2A> 分岐によって実行されるアクティビティを追加するには、"ここにアクティビティをドロップします" というヒント テキストが表示された **If** アクティビティ デザイナーの **\[Then\]** ボックスに、**\[ツールボックス\]** からアクティビティをドロップします。|  
  
## 参照  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)