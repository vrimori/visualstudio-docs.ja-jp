---
title: "TerminateWorkflow アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: e114f95baf771d8138fd155cf79f6e0ddbf14485
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナー
**TerminateWorkflow**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.TerminateWorkflow>アクティビティ。  
  
## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow アクティビティ  
 <xref:System.Activities.Statements.TerminateWorkflow> アクティビティは、ワークフローの実行を停止します。  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナーの使用  
 **TerminateWorkflow**アクティビティ デザイナーは含まれて、**ランタイム**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X です)。  
  
 **TerminateWorkflow**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>です。 これを作成、 <xref:System.Activities.Statements.TerminateWorkflow> 、既定値を持つアクティビティ**DisplayName** terminateworkflow であるのです。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TerminateWorkflow**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow のプロパティ  
 次の表に、<xref:System.Activities.Statements.TerminateWorkflow> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> アクティビティの表示名。 既定値は TerminateWorkflow です。 表示名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|ワークフローが停止されたときにスローする例外。 このプロパティは、プロパティ グリッドで設定します。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|ワークフローが停止された理由。 このプロパティは、プロパティ グリッドで設定します。|  
  
## <a name="see-also"></a>参照  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)   
 [永続化します。](../workflow-designer/persist-activity-designer.md)