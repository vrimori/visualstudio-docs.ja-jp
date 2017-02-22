---
title: "WriteLine アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.WriteLine.UI"
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# WriteLine アクティビティ デザイナー
**WriteLine** アクティビティ デザイナーは、<xref:System.Activities.Statements.WriteLine> アクティビティを作成および構成するために使用します。  
  
## WriteLine アクティビティ  
 <xref:System.Activities.Statements.Writeline> アクティビティは、指定された <xref:System.IO.TextWriter> オブジェクトにテキストを書き込みます。<xref:System.IO.TextWriter> を指定しない場合、<xref:System.Activities.Statements.Writeline> はテキストをコンソールに書き込みます。  
  
### WriteLine アクティビティ デザイナーの使用  
 **WriteLine** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[プリミティブ\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の**\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **WriteLine** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の任意の画面 \(<xref:System.Activities.Statements.Sequence> 内など\) にドロップできます。この操作により、WriteLine という既定の <xref:System.Activities.Activity.DisplayName%2A> を持つ <xref:System.Activities.Statements.WriteLine> アクティビティが作成されます。<xref:System.Activities.Activity.DisplayName%2A> は、**WriteLine** アクティビティ デザイナーのヘッダー、またはプロパティ グリッドの **\[DisplayName\]** ボックスで編集できます。  
  
### WriteLine プロパティ  
 次の表に、<xref:System.Activities.Statements.WriteLine> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドで編集できます。また、一部のプロパティは、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|<xref:System.Activities.Statements.WriteLine> アクティビティの表示名。既定値は WriteLine です。<xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|書き込むテキスト。このプロパティを設定するには、**WriteLine** アクティビティ デザイナーの **\[テキスト\]** ボックスまたはプロパティ グリッドに、Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|省略可|<xref:System.Activities.Statements.WriteLine> による <xref:System.Activities.Statements.WriteLine.Text%2A> の書き込み先の <xref:System.IO.TextWriter>。既定はコンソールです。|  
  
## 参照  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)