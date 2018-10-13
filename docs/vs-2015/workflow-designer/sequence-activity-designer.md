---
title: アクティビティ デザイナーをシーケンス処理 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: d676c4270d636d0869d5b2f95f7a265bf0a085ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282777"
---
# <a name="sequence-activity-designer"></a>Sequence アクティビティ デザイナー
<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。  
  
 他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。 使用を検討して、[フローチャート](../workflow-designer/flowchart-activity-designer.md)単純な分岐またはループのダイアグラムでモデル化するプログラム フローがある場合。  
  
## <a name="using-the-sequence-activity-designer"></a>Sequence アクティビティ デザイナーの使用  
 追加する、<xref:System.Activities.Statements.Sequence>アクティビティをドラッグ、**シーケンス**からアクティビティ デザイナー、**ツールボックス**にドロップし、[!INCLUDE[wfd1](../includes/wfd1-md.md)]画面。 これに子アクティビティを追加する<xref:System.Activities.Statements.Sequence>アクティビティから他のアクティビティをドラッグ、**ツールボックス**し、「ここにアクティビティをドロップ」というヒント テキスト ボックスにある三角形にドロップします。  
  
### <a name="sequence-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Sequence アクティビティのプロパティ  
 次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。 既定値は Sequence です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
  
## <a name="see-also"></a>関連項目  
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)