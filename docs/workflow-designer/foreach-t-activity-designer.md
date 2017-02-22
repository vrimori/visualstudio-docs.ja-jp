---
title: "ForEach&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ForEach&lt;T&gt; アクティビティ デザイナー
<xref:System.Activities.Statements.ForEach%601> アクティビティは、指定した <xref:System.Activities.Statements.ForEach%601.Values%2A> コレクション内の各項目に対して、<xref:System.Activities.Statements.ForEach%601.Body%2A> に含まれるアクティビティを実行します。  
  
## ワークフロー デザイナーでの ForEach\<T\> のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.ForEach%601> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> アクティビティの表示名。既定値は ForEach\<Int32\> です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|反復処理を行う項目のコレクション。<xref:System.Activities.Statements.ForEach%601.Values%2A> を設定するには、**ForEach\<T\>** アクティビティ デザイナーまたはプロパティ グリッドの **\[値\]** ボックスに [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の式を入力します。|  
|*TypeArgument*|必須|ジェネリック パラメーター *T* で指定された <xref:System.Activities.Statements.ForEach%601.Values%2A> コレクション内の項目の型。既定では、*TypeArgument* は **Int32** に設定されています。型を変更するには、プロパティ グリッドで、*TypeArgument* のコンボ ボックスの値を変更します。|  
  
 既定では、**item** という名前がループ反復子に付けられます。反復子変数の名前は、<xref:System.Activities.Statements.ForEach%601> アクティビティ デザイナーで変更できます。ループ反復子は、<xref:System.Activities.Statements.ForEach%601> アクティビティの子の式で使用できます。  
  
## 参照  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)