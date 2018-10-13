---
title: FlowDecision アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.FlowDecision.UI
ms.assetid: 4a49edc3-3662-4b7b-812e-0a5ba00d6c94
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7109b779cf33d226f44853e3f67c8609bd42fc1b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212889"
---
# <a name="flowdecision-activity-designer"></a>FlowDecision アクティビティ デザイナー
<xref:System.Activities.Statements.FlowDecision> ノードは条件ノードであり、指定した条件を満たすかどうかに基づいて、2 つの選択肢のどちらかに進む制御フローの分岐を提供します。 フローに 3 つ以上の分岐が必要な場合は、代わりに <xref:System.Activities.Statements.FlowSwitch%601> を使用します。  
  
## <a name="the-flowdecision-node"></a>FlowDecision ノード  
 <xref:System.Activities.Statements.FlowDecision> は、フローを 2 つに分岐できる場合に使用します。 <xref:System.Activities.Statements.FlowDecision> ノードには、<xref:System.Activities.Statements.FlowDecision.Condition%2A> および <xref:System.Activities.Statements.FlowNode> があり、<xref:System.Activities.Statements.FlowDecision.True%2A> または <xref:System.Activities.Statements.FlowDecision.False%2A> という、想定される 2 つの結果のそれぞれに関連付けられています。 <xref:System.Activities.Statements.FlowDecision.Condition%2A> が評価され、この評価の値により、次に <xref:System.Activities.Statements.FlowNode> 内で処理される <xref:System.Activities.Statements.Flowchart> が決定されます。  
  
### <a name="using-the-flowdecision-designer"></a>FlowDecision デザイナーの使用  
 **FlowDecision**で見つかるデザイナー、**フローチャート**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブで、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **FlowDecision**からデザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]内でサーフェスを**フローチャート**アクティビティ デザイナー。 これを作成、<xref:System.Activities.Statements.FlowDecision>というラベルの付いた**デシジョン**内、<xref:System.Activities.Statements.Flowchart>アクティビティ。 デザイナー上にマウス、 **True**と**False** 2 つの分岐の正方形のハンドルが表示されます。  
  
 ドラッグした後、 **FlowDecision**デザイナーおよびその他のデザイナー上に、**フローチャート**ノードをリンクする実行の順序を指定するために。 ソース ノード間のリンクを作成する (など、 **True**と**False**の分岐、 **FlowDecision**) と、ソース ノードのデザイナー上にマウスを移動先のノードその両側に正方形のハンドルが表示されます。 そのハンドルのどちらかをクリックし、マウス ボタンを押したまま、接続先ノードにマウス ポインターを置いたときと同じように表示されるハンドルのどちらかにドラッグします。 マウス ボタンを放すと、これら 2 つのノードの間にリンクが作成されます。このリンクは、接続元デザイナーから接続先デザイナーへの矢印で表されます。  
  
 示す式、<xref:System.Activities.Statements.FlowDecision.Condition%2A>で入力することができます、**条件**のボックス、**プロパティ**というヒント テキストが「VB の式を入力」を表示 ウィンドウをクリックします。  
  
### <a name="the-flowdecision-properties"></a>FlowDecision プロパティ  
 次の表に、<xref:System.Activities.Statements.FlowDecision> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowDecision.Condition%2A>|True|フロー制御が使用するパスを決定する条件。|  
|<xref:System.Activities.Statements.FlowDecision.True%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> が満たされた場合にフロー制御で使用されるパス。|  
|<xref:System.Activities.Statements.FlowDecision.False%2A>|False|<xref:System.Activities.Statements.FlowDecision.Condition%2A> が満たされない場合にフロー制御で使用されるパス。|  
  
## <a name="see-also"></a>関連項目  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)   
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)