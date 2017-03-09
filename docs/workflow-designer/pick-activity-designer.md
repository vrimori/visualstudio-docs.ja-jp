---
title: "Pick アクティビティ デザイナー | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Pick アクティビティ デザイナー
<xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御フローを提供します。このアクティビティは、トリガー起動イベントに応答して、複数の分岐のいずれか 1 つを実行します。  
  
## Pick アクティビティ  
 <xref:System.Activities.Statements.Pick> アクティビティには、<xref:System.Activities.Statements.PickBranch> オブジェクトのコレクションが含まれており、<xref:System.Activities.Statements.Pick> アクティビティはそのオブジェクトの 1 つを、トリガーの役割を果たす受信イベントに応答して実行できます。このようにして、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]では、イベント ベースの制御フロー モデリングが提供されます。各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。<xref:System.Activities.Statements.Pick> アクティビティの実行の開始時に、<xref:System.Activities.Statements.PickBranch> 要素のすべてのトリガー アクティビティがスケジュールされます。最初のアクティビティが完了すると、対応するアクション アクティビティがスケジュールされ、他のすべてのトリガー アクティビティは取り消されます。  
  
### Pick アクティビティ デザイナーの使用方法  
 **Pick** アクティビティ デザイナーは、**\[ツールボックス\]** の **\[制御フロー\]** カテゴリにあります。\[ツールボックス\] にアクセスするには、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]の **\[ツールボックス\]** タブをクリックします \(または、**\[表示\]** メニューの **\[ツール バー\]** をクリックするか、Ctrl キーと Alt キーを押しながら X キーを押します\)。  
  
 **Pick** アクティビティ デザイナーは、**\[ツールボックス\]** からドラッグして、アクティビティ デザイナーを通常配置している[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面の任意の場所 \(**Sequence** アクティビティ デザイナー内など\) にドロップできます。[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]にドロップすると、<xref:System.Activities.Statements.Pick> アクティビティが作成されます。このアクティビティには、既定で、Branch1 および Branch2 という表示名を持つ 2 つの空の <xref:System.Activities.Statements.PickBranch> アクティビティが要素として格納されます。それぞれの <xref:System.Activities.Statements.PickBranch.DisplayName%2A> プロパティの値は、**PickBranch** アクティビティ デザイナーのヘッダー内、または各分岐の **\[プロパティ\]** ウィンドウ内で編集できます。  
  
 <xref:System.Activities.Statements.PickBranch> アクティビティを <xref:System.Activities.Statements.Pick> オブジェクトのコレクションに追加する方法は 2 つあります。**\[ツールボックス\]** から **PickBranch** デザイナーをドラッグ アンド ドロップする方法と、**Pick** デザイン画面内からコンテキスト メニューを使用する方法です。詳細については、「[PickBranch](../workflow-designer/pickbranch-activity-designer.md)」を参照してください。**Pick** アクティビティ デザイナー内に配置できる項目は、**PickBranch** アクティビティ デザイナーのみです。  
  
### ワークフロー デザイナーでの Pick アクティビティのプロパティ  
 次の表に、<xref:System.Activities.Statements.Pick> のプロパティと、デザイナーでのその使用方法を示します。これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用法|  
|------------|--------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|省略可|ヘッダーの <xref:System.Activities.Statements.Pick> アクティビティ デザイナーの表示名を指定します。既定値は Pick です。この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
  
## 参照  
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)   
 [Pick アクティビティ](../Topic/Pick%20Activity.md)   
 [Pick アクティビティの使用](../Topic/Using%20the%20Pick%20Activity.md)