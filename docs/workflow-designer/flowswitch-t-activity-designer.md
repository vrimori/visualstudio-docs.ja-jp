---
title: "FlowSwitch&lt;T&gt; アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# FlowSwitch&lt;T&gt; アクティビティ デザイナー
<xref:System.Activities.Statements.FlowSwitch%601> アクティビティは、3 つ以上の代替分岐が必要な場合に、一致条件に基づいて制御フローの分岐を提供する条件ノードです。フローの分岐に必要なパスが 2 つのみである場合は、代わりに <xref:System.Activities.Statements.FlowDecision> アクティビティを使用します。  
  
## FlowSwitch\<T\> アクティビティ  
 <xref:System.Activities.Statements.FlowSwitch%601> アクティビティには、評価時に *T* 型の値 \(ジェネリック パラメーターにより指定される\) を返す <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> が含まれます。アクティビティには、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> のセットも含まれます。これは、この評価の想定される結果から、<xref:System.Activities.Statements.FlowNode> オブジェクトへの一意のマッピングを指定します。実行された <xref:System.Activities.Statements.FlowNode> は、その *T* 型のオブジェクトが、評価された <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の値と一致します。<xref:System.Activities.Statements.FlowSwitch%601.Default%2A> case は、一致が取得されない case に対して \(必要に応じて\) 提供できます。  
  
### FlowSwitch\<T\> アクティビティ デザイナーの使用  
 **FlowSwitch\<T\>** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[フローチャート\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の左側にある **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **FlowSwitch\<T\>** デザイナーは、**\[ツールボックス\]** からドラッグして、**Flowchart** アクティビティ デザイナー内の[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面にドロップできます。表示される **\[型の選択\]** ウィンドウを使用して、<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の評価から取得される型 \(コード内でそのジェネリック パラメーターにより <xref:System.Activities.Statements.FlowSwitch%601> に関連付けられる\) を指定します。この手順により、<xref:System.Activities.Statements.Flowchart> アクティビティ内に、"**Switch**" というラベルの付いた <xref:System.Activities.Statements.FlowSwitch%601> アクティビティが作成されます。"VB の式を入力してください" というヒント テキストが表示される場所をクリックすると、**\[プロパティ\]** ウィンドウの **\[式\]** ボックスに <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> を入力できます。  
  
 **FlowSwitch\<T\>** アクティビティ デザイナーにマウス ポインターを重ねると、正方形のハンドルが端に表示されます。これを使って、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> をリンクできます。**FlowSwitch\<T\>** などのアクティビティ デザイナーを **Flowchart** にドラッグすると、それらが表す <xref:System.Activities.Activity> オブジェクトを相互にリンクして、実行の順序を指定できるようになります。<xref:System.Activities.Statements.FlowSwitch%601> に関連付けられた <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> の 1 つを作成するには、**FlowSwitch\<T\>** の周囲にある正方形の case ハンドルの 1 つをクリックし、マウス ボタンを押したまま、接続先のアクティビティの周囲にある同様のハンドルの 1 つにドラッグします。このハンドルは、デザイナーにマウス ポインターを置くと表示されます。マウス ボタンを放すと、**FlowSwitch\<T\>** から接続先のデザイナーまで、この case を表す矢印が表示されます。この case の既定値が矢印に表示されます。その値は、**\[プロパティ\]** ウィンドウの **\[Case\]** ボックスで編集できます。  
  
### FlowSwitch\<T\> プロパティ  
 次の表に、<xref:System.Activities.Statements.FlowSwitch%601> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|必須|実行パスのどの <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> に切り替えるかを決定するために評価される式を指定します。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|省略可|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の評価によって得られる可能性のある結果から、<xref:System.Activities.Statements.FlowNode> オブジェクトのセットへの一意のマッピングを指定します。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|必須|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の評価が、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> オブジェクトに含まれる値のいずれにも一致しない場合のマッピングを指定します。|  
  
## 参照  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)   
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)