---
title: DoWhile アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ec9bc21095905f373cf302deedd73bbce678a6de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227657"
---
# <a name="dowhile-activity-designer"></a>DoWhile アクティビティ デザイナー
<xref:System.Activities.Statements.DoWhile>アクティビティに含まれるアクティビティを実行します。 その<xref:System.Activities.Statements.DoWhile.Body%2A>を少なくとも 1 回に、指定した条件が評価されるまで**false**します。 ループの本体に含まれるアクティビティを 0 回以上実行する必要がある場合は、代わりに、<xref:System.Activities.Statements.While> アクティビティを使用します。  
  
## <a name="dowhile-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの DoWhile のプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.DoWhile> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|条件がときに実行するアクティビティ**true**します。 追加する、<xref:System.Activities.Statements.DoWhile.Body%2A>アクティビティ、アクティビティをツールボックスからドロップ、**本文**ボックスに、 **DoWhile**アクティビティ デザイナーの「ドロップ アクティビティここ」ヒント テキスト。|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|ループの各繰り返しの後に評価する条件。 設定する、 <xref:System.Activities.Statements.DoWhile.Condition%2A>、タイプ a[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]内の式、**条件**ボックスに、 **DoWhile**アクティビティ デザイナーまたはプロパティ グリッドで。|  
  
## <a name="see-also"></a>関連項目  
 [while](../workflow-designer/while-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)