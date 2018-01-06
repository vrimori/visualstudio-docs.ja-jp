---
title: "FlowSwitch&lt;T&gt;アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Core.Presentation.FlowSwitchLink.UI
- System.Activities.Statements.FlowSwitch`1.UI
- System.Activities.Core.Presentation.FlowSwitchLink`1.UI
- System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: c3e757d8ffea7e91c2d5e51bc4a04e6225d1064f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="flowswitchlttgt-activity-designer"></a>FlowSwitch&lt;T&gt;アクティビティ デザイナー
<xref:System.Activities.Statements.FlowSwitch%601> アクティビティは、3 つ以上の代替分岐が必要な場合に、一致条件に基づいて制御フローの分岐を提供する条件ノードです。 フローの分岐に必要なパスが 2 つのみである場合は、代わりに <xref:System.Activities.Statements.FlowDecision> アクティビティを使用します。  
  
## <a name="the-flowswitcht-activity"></a>FlowSwitch < T\>アクティビティ  
 <xref:System.Activities.Statements.FlowSwitch%601>アクティビティが含まれています、<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>型の値を返す*T* (ジェネリック パラメーターで指定) が評価されるときです。 アクティビティには、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> のセットも含まれます。これは、この評価の想定される結果から、<xref:System.Activities.Statements.FlowNode> オブジェクトへの一意のマッピングを指定します。 <xref:System.Activities.Statements.FlowNode>型のオブジェクトが、1 つは、実行*T*評価の値と一致する<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>です。 <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> case は、一致が取得されない case に対して (必要に応じて) 提供できます。  
  
### <a name="using-the-flowswitcht-activity-designer"></a>FlowSwitch を使用して\<T > アクティビティ デザイナー  
 **FlowSwitch\<T >**アクティビティ デザイナーは含まれて、**フローチャート**のカテゴリ、**ツールボックス**、 をクリックしてアクセスされる**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。  
  
 **FlowSwitch\<T >**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]内でサーフェス、**フローチャート**アクティビティ デザイナー。 使用して、**タイプの選択**型の指定に表示するウィンドウ (コードで関連付けられている、<xref:System.Activities.Statements.FlowSwitch%601>でそのジェネリック パラメーター) の評価から取得した、<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>です。 この手順で作成、<xref:System.Activities.Statements.FlowSwitch%601>というラベルの付いたアクティビティ**スイッチ**内で、<xref:System.Activities.Statements.Flowchart>アクティビティ。 <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>で入力することができます、**式**のボックス、**プロパティ**というヒント テキストが「VB の式の入力」を表示 ウィンドウをクリックします。  
  
 マウス ポインター、 **FlowSwitch\<T >**リンク アップに使用される四角形のハンドルが発生するアクティビティ デザイナー<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>の端の周りにします。 ドラッグした後、 **FlowSwitch < T\>** アクティビティ デザイナーおよびその他のアクティビティ デザイナーを**フローチャート**、<xref:System.Activities.Activity>それらが表すオブジェクトが一緒にリンクする準備完了実行の順序を指定します。 いずれかを作成する、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>に関連付けられている、<xref:System.Activities.Statements.FlowSwitch%601>の周囲に四角形の case ハンドルのいずれかをクリックして、 **FlowSwitch < T\>** ハンドルのいずれかに (ボタンを押し、マウスをドラッグマウスがデザイナー上に置いたときに、接続先アクティビティ周りに同様に表示されるとします。 マウス ボタンをクリックしてから矢印のリリース、 **FlowSwitch < T\>** への接続先のデザイナーには、この case を表すが表示されます。 このケースを矢印を表示しで編集できますの既定値、**ケース**のボックス、**プロパティ**ウィンドウです。  
  
### <a name="the-flowswitcht-properties"></a>FlowSwitch < T\>プロパティ  
 次の表に、<xref:System.Activities.Statements.FlowSwitch%601> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|実行パスのどの <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> に切り替えるかを決定するために評価される式を指定します。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の評価によって得られる可能性のある結果から、<xref:System.Activities.Statements.FlowNode> オブジェクトのセットへの一意のマッピングを指定します。|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> の評価が、<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> オブジェクトに含まれる値のいずれにも一致しない場合のマッピングを指定します。|  
  
## <a name="see-also"></a>参照  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)   
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)