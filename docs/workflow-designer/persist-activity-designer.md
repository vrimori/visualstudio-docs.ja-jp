---
title: "Persist アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Persist.UI"
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Persist アクティビティ デザイナー
**Persist** アクティビティ デザイナーは、<xref:System.Activities.Statements.Persist> アクティビティを作成および構成するために使用します。  
  
## Persist アクティビティ  
 <xref:System.Activities.Statements.Persist> アクティビティで、ワークフローをディスクに保存します \(可能な場合\)。<xref:System.Activities.Statements.Persist> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティ内などの非永続化ゾーンでは実行できません。非永続化スコープで <xref:System.Activities.Statements.Persist> アクティビティを使用すると、実行時に例外がスローされます。  
  
### Persist アクティビティ デザイナーの使用  
 **Persist** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[ランタイム\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、**\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツールボックス\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Persist** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Persist という既定の **DisplayName** を持つ <xref:System.Activities.Statements.Persist> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**Persist** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### Persist のプロパティ  
 次の表に、<xref:System.Activities.Statements.Persist> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> アクティビティの表示名。既定値は Persist です。表示名は必須ではありませんが、使用することをお勧めします。|  
  
## 参照  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)   
 [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)