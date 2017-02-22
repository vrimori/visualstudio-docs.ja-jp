---
title: "Assign アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Assign.UI"
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Assign アクティビティ デザイナー
**Assign** アクティビティ デザイナーは、<xref:System.Activities.Statements.Assign> アクティビティを作成および構成するために使用します。  
  
## Assign アクティビティ  
 <xref:System.Activities.Statements.Assign> アクティビティで、変数または引数に値を割り当てます。  
  
### Assign アクティビティ デザイナーの使用  
 **Assign** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[プリミティブ\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、**\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツールボックス\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Assign** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、Assign という既定の **DisplayName** を持つ <xref:System.Activities.Statements.Assign> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**Assign** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### Assign のプロパティ  
 次の表に、<xref:System.Activities.Statements.Assign> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.Assign> アクティビティの表示名。既定値は Assign です。<xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Assign.To%2A>|必須|<xref:System.Activities.Statements.Assign.Value%2A> を割り当てる変数または引数。有効な Visual Basic 識別子を指定する必要があります。このプロパティを設定するには、**Assign** アクティビティ デザイナーまたはプロパティ グリッドの **\[割り当て先\]** ボックスに Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.Assign.Value%2A>|必須|変数に割り当てられる値。<xref:System.Activities.Statements.Assign.Value%2A> を設定するには、**Assign** アクティビティ デザイナーまたはプロパティ グリッドの **\[値\]** ボックスに Visual Basic の式を入力します。|  
  
## 参照  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)