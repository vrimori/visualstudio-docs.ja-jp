---
title: "FlowDecision アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.FlowDecision.UI"
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowDecision アクティビティ デザイナー
<xref:System.Activities.Statements.FlowDecision> ノードは条件ノードであり、指定した条件を満たすかどうかに基づいて、2 つの選択肢のどちらかに進む制御フローの分岐を提供します。フローに 3 つ以上の分岐が必要な場合は、代わりに <xref:System.Activities.Statements.FlowSwitch%601> を使用します。  
  
## FlowDecision ノード  
 <xref:System.Activities.Statements.FlowDecision> は、フローを 2 つに分岐できる場合に使用します。<xref:System.Activities.Statements.FlowDecision> ノードには、<xref:System.Activities.Statements.FlowDecision.Condition%2A> および <xref:System.Activities.Statements.FlowNode> があり、<xref:System.Activities.Statements.FlowDecision.True%2A> または <xref:System.Activities.Statements.FlowDecision.False%2A> という、想定される 2 つの結果のそれぞれに関連付けられています。<xref:System.Activities.Statements.FlowDecision.Condition%2A> が評価され、この評価の値により、次に <xref:System.Activities.Statements.Flowchart> 内で処理される <xref:System.Activities.Statements.FlowNode> が決定されます。  
  
### FlowDecision デザイナーの使用  
 **FlowDecision** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[フローチャート\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **FlowDecision** デザイナーは、**\[ツールボックス\]** からドラッグして、**Flowchart** アクティビティ デザイナー内の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面にドロップできます。これにより、<xref:System.Activities.Statements.Flowchart> アクティビティ内に、**Decision** というラベルの付いた <xref:System.Activities.Statements.FlowDecision> が作成されます。デザイナーでマウスを動かすと、2 つの分岐用の正方形のハンドル \(**\[True\]** および **\[False\]**\) が表示されます。  
  
 **FlowDecision** などのデザイナーを **Flowchart** にドラッグすると、ノードを互いにリンクさせて実行の順序を指定できます。接続元ノード \(**FlowDecision** の **\[True\]** および **\[False\]** 分岐を含む\) と接続先ノードの間にリンクを作成するには、接続元ノードのデザイナー上にマウス ポインターを置きます。これで、その両側に正方形のハンドルが表示されます。そのハンドルのどちらかをクリックし、マウス ボタンを押したまま、接続先ノードにマウス ポインターを置いたときと同じように表示されるハンドルのどちらかにドラッグします。マウス ボタンを放すと、これら 2 つのノードの間にリンクが作成されます。このリンクは、接続元デザイナーから接続先デザイナーへの矢印で表されます。  
  
 "VB の式を入力してください" というヒント テキストが表示される場所をクリックすと、<xref:System.Activities.Statements.FlowDecision.Condition%2A> を示す式を **\[プロパティ\]** ウィンドウの **\[条件\]** ボックスに入力できます。  
  
### FlowDecision プロパティ  
 次の表に、<xref:System.Activities.Statements.FlowDecision> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|必須|フロー制御が使用するパスを決定する条件。|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|省略可|<xref:System.Activities.Statements.FlowDecision.Condition%2A> が満たされた場合にフロー制御で使用されるパス。|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|省略可|<xref:System.Activities.Statements.FlowDecision.Condition%2A> が満たされない場合にフロー制御で使用されるパス。|  
  
## 参照  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)   
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)