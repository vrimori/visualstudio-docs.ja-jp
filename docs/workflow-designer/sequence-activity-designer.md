---
title: "アクティビティ デザイナーをシーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 51f138d17c2b0f8d8a483ef09c298d1dbbf9345c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="sequence-activity-designer"></a>Sequence アクティビティ デザイナー
<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。  
  
 他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。 使用を検討して、[フローチャート](../workflow-designer/flowchart-activity-designer.md)がある場合、単純な分岐または図をモデル化するプログラム フローをループします。  
  
## <a name="using-the-sequence-activity-designer"></a>Sequence アクティビティ デザイナーの使用  
 追加する、<xref:System.Activities.Statements.Sequence>アクティビティをドラッグ、**シーケンス**からアクティビティ デザイナー、**ツールボックス**にドロップし、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]画面。 これに子アクティビティを追加する<xref:System.Activities.Statements.Sequence>アクティビティから他のアクティビティをドラッグして、**ツールボックス**し、「ここにアクティビティをドロップ」というヒント テキストをボックスにある三角形にドロップします。  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Sequence アクティビティのプロパティ  
 次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。 既定値は Sequence です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
  
## <a name="see-also"></a>関連項目  
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)