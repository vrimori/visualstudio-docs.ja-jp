---
title: "Parallel アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Parallel アクティビティ デザイナー
<xref:System.Activities.Statements.Parallel> アクティビティは、一連の子アクティビティを同時に実行するアクティビティです。  
  
## Parallel アクティビティ  
 <xref:System.Activities.Statements.Parallel> アクティビティは、子アクティビティを <xref:System.Activities.Statements.Parallel.Branches%2A> コレクションに格納します。一部の子アクティビティがアイドル状態になる可能性がある場合は、<xref:System.Activities.Statements.Sequence> アクティビティの代わりに <xref:System.Activities.Statements.Parallel> アクティビティを使用してください。  
  
 <xref:System.Activities.Statements.Parallel> アクティビティには、ユーザーによって指定された [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 式を保持する <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> プロパティがあります。このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.Parallel> アクティビティによって評価されます。評価結果が **True** の場合、<xref:System.Activities.Statements.Parallel> アクティビティは他の分岐を実行せずに完了します。<xref:System.Activities.Statements.Parallel.CompletionCondition%2A> が **True** に評価されない場合は、すべての子アクティビティが完了するまで <xref:System.Activities.Statements.Parallel> アクティビティが継続されます。  
  
### Parallel アクティビティ デザイナーの使用  
 **Parallel** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[制御フロー\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Parallel** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティ デザイナーを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(**Sequence** アクティビティ デザイナー内など\) にドロップできます。このアクティビティ デザイナーを[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]にドロップすると、<xref:System.Activities.Statements.Parallel> アクティビティが作成されます。既定では、このアクティビティに **Parallel** の <xref:System.Activities.Activity.DisplayName%2A> が含まれます。  
  
 並列アクティビティの <xref:System.Activities.Statements.Parallel.Branches%2A> コレクションにアクティビティを追加するには、**\[ツールボックス\]** から他のアクティビティ デザイナーをドラッグし、**Parallel** アクティビティ デザイナー内の三角形にドロップします。分岐に含まれるアクティビティのそばに三角形が配置されます。この手順を繰り返すことによって、さらにアクティビティを追加できます。アクティビティを並べ替えるには、**Parallel** アクティビティ デザイナー内でアクティビティをドラッグ アンド ドロップします。  
  
### ワークフロー デザイナーでの Parallel アクティビティのプロパティ  
 次の表に、Parallel アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|------------|--------|----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|ヘッダーのアクティビティ デザイナーの表示名を指定します。既定値は **Parallel** です。この値は、**\[プロパティ\]** グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|必須|実行される子アクティビティのコレクションが格納されます。|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|省略可|分岐の完了後に評価されます。**True** であると評価する場合、スケジュールされた保留分岐はキャンセルされます。このプロパティが設定されていないか、**False** であると評価する場合は、すべての子アクティビティが完了するまでアクティビティが継続されます。既定値は、**null** です。|  
  
## 参照  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)