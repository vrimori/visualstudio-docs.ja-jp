---
title: "TerminateWorkflow アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TerminateWorkflow.UI"
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# TerminateWorkflow アクティビティ デザイナー
**TerminateWorkflow** アクティビティ デザイナーは、<xref:System.Activities.Statements.TerminateWorkflow> アクティビティを作成および構成するために使用します。  
  
## TerminateWorkflow アクティビティ  
 <xref:System.Activities.Statements.TerminateWorkflow> アクティビティは、ワークフローの実行を停止します。  
  
### TerminateWorkflow アクティビティ デザイナーの使用  
 **TerminateWorkflow** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[ランタイム\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、**\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツールボックス\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **TerminateWorkflow** アクティビティ デザイナーを **\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、既定の **DisplayName** が TerminateWorkflow である <xref:System.Activities.Statements.TerminateWorkflow> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**TerminateWorkflow** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### TerminateWorkflow のプロパティ  
 次の表に、<xref:System.Activities.Statements.TerminateWorkflow> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.TerminateWorkflow> アクティビティの表示名。既定値は TerminateWorkflow です。表示名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|省略可|ワークフローが停止されたときにスローする例外。このプロパティは、プロパティ グリッドで設定します。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|省略可|ワークフローが停止された理由。このプロパティは、プロパティ グリッドで設定します。|  
  
## 参照  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)