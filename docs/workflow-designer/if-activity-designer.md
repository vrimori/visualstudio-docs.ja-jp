---
title: "場合はアクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.If.UI
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 950bff10372c9c40e047f891049e7cc387c8efc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="if-activity-designer"></a>If アクティビティ デザイナー
<xref:System.Activities.Statements.If> アクティビティでは、条件を評価し、その評価の結果に応じてアクティビティを実行します。 このアクティビティは、手順型モデルのプログラミング スタイルを使用する場合に最も役立ちます。 <xref:System.Activities.Statements.If> アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Parallel> アクティビティなどの内部に入れ子にすることができます。 <xref:System.Activities.Statements.Flowchart> アクティビティを使用している場合は、代わりに、<xref:System.Activities.Statements.FlowDecision> アクティビティの使用を検討してください。  
  
## <a name="if-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの If のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.If> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|実行する子アクティビティを決定する条件。 設定する、 <xref:System.Activities.Statements.If.Condition%2A>、種類 a[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]内の式、**条件**ボックスに、**場合**アクティビティ デザイナーまたはプロパティ グリッドでします。|  
|<xref:System.Activities.Statements.If.Else%2A>|False|場合に実行されるアクティビティ、<xref:System.Activities.Statements.If.Condition%2A>は**false**です。 によって実行されるアクティビティを追加する、<xref:System.Activities.Statements.If.Else%2A>分岐からアクティビティをドロップ、**ツールボックス**に、 **Else**ボックスに、**場合**アクティビティ デザイナーのヒント テキストが"ここにアクティビティをドロップ"です。|  
|<xref:System.Activities.Statements.If.Then%2A>|False|場合に実行されるアクティビティ、<xref:System.Activities.Statements.If.Condition%2A>は**true**です。 によって実行されるアクティビティを追加する、<xref:System.Activities.Statements.If.Then%2A>分岐からアクティビティをドロップ、**ツールボックス**に、**し**ボックスに、**場合**アクティビティ デザイナーのヒント テキストが"ここにアクティビティをドロップ"です。|  
  
## <a name="see-also"></a>参照  
 [シーケンス](../workflow-designer/sequence-activity-designer.md)   
 [並列](../workflow-designer/parallel-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)