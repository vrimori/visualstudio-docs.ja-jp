---
title: "Sequence アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Sequence アクティビティ デザイナー
<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。  
  
 他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。プログラムの単純な分岐またはループのフローをダイアグラムでモデル化する場合は、[フローチャート](../workflow-designer/flowchart-activity-designer.md) の使用を検討してください。  
  
## Sequence アクティビティ デザイナーの使用  
 <xref:System.Activities.Statements.Sequence> アクティビティを追加するには、**\[ツールボックス\]** から **Sequence** アクティビティ デザイナーをドラッグして、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]画面にドロップします。この <xref:System.Activities.Statements.Sequence> アクティビティに子アクティビティを追加するには、**\[ツールボックス\]** から他のアクティビティをドラッグして、"ここにアクティビティをドロップ" というヒント テキストが表示される、ボックス内の三角形にドロップします。  
  
### ワークフロー デザイナーでの Sequence アクティビティのプロパティ  
 次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。既定値はシーケンスです。この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
  
## 参照  
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)