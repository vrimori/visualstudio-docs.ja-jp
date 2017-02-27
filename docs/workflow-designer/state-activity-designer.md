---
title: "State アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# State アクティビティ デザイナー
<xref:System.Activities.Statements.State> はステート マシンの状態を表します。  
  
## State アクティビティ デザイナーの使用  
 <xref:System.Activities.Statements.State> をワークフローに追加するには、**\[ツールボックス\]** の **\[ステート マシン\]** セクションから **State** アクティビティ デザイナーをドラッグして、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] 画面の <xref:System.Activities.Statements.StateMachine> アクティビティにドロップします。<xref:System.Activities.Statements.State> アクティビティは、 <xref:System.Activities.Statements.StateMachine> にドロップして遷移を後で追加できます。または遷移は、<xref:System.Activities.Statements.State> アクティビティをドロップしたときに作成できます。<xref:System.Activities.Statements.State> アクティビティを追加し、1 ステップの遷移を作成するには、**\[ツールボックス\]** の **\[ステート マシン\]** セクションから **State** アクティビティをドラッグし、ワークフロー デザイナーの別の状態に置きます。ドラッグされている <xref:System.Activities.Statements.State> が別の <xref:System.Activities.Statements.State> の上にある場合、もう一方の <xref:System.Activities.Statements.State> の周囲に 4 つの三角形が表示されます。<xref:System.Activities.Statements.State> を 4 つの三角形のいずれかにドロップすると、ステート マシンに追加され、遷移元の <xref:System.Activities.Statements.State> からドロップされた遷移先の <xref:System.Activities.Statements.State> に遷移が作成されます。詳細については、「[Transition](../workflow-designer/transition-activity-designer.md)」を参照してください。  
  
### ワークフロー デザイナーでの State アクティビティのプロパティ  
 次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.State> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティの中には、プロパティ グリッドで編集できるものがあります。また、その一部はデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.State> アクティビティ デザイナーの表示名を指定します。既定値は **State** です。この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<xref:System.Activities.Statements.State.DisplayName%2A> はワーク フロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|この状態の遷移時に発生するアクションを指定します。<xref:System.Activities.Statements.State> アクティビティが展開されているとき、この値は **\[ツールボックス\]** からアクティビティをドラッグし、状態の **\[開始\]** セクションにドロップして設定できます。|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|この状態からの遷移時に発生するアクションを指定します。<xref:System.Activities.Statements.State> アクティビティが展開されているとき、この値は **\[ツールボックス\]** からアクティビティをドラッグし、状態の **\[終了\]** セクションにドロップして設定できます。|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|<xref:System.Activities.Statements.State> から発生する可能性のある遷移を示します。リスト内の各項目には、関連付けられた <xref:System.Activities.Statements.Transition> と遷移先の <xref:System.Activities.Statements.State> へのリンクがあります。リンクをクリックすると、デザイナーを <xref:System.Activities.Statements.Transition> または <xref:System.Activities.Statements.State> の展開されたビューに切り替えます。|  
  
## 参照  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Transition](../workflow-designer/transition-activity-designer.md)