---
title: TerminateWorkflow アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 67681982c9c8d77df77242be5c07679f3b0d24ff
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225723"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナー
**TerminateWorkflow**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.TerminateWorkflow>アクティビティ。  
  
## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow アクティビティ  
 <xref:System.Activities.Statements.TerminateWorkflow> アクティビティは、ワークフローの実行を停止します。  
  
### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナーの使用  
 **TerminateWorkflow**アクティビティ デザイナーが記載されて、**ランタイム**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **TerminateWorkflow**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.TerminateWorkflow> 、既定値は、アクティビティ**DisplayName** TerminateWorkflow の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TerminateWorkflow**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow のプロパティ  
 次の表に、<xref:System.Activities.Statements.TerminateWorkflow> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> アクティビティの表示名。 既定値は TerminateWorkflow です。 表示名は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|ワークフローが停止されたときにスローする例外。 このプロパティは、プロパティ グリッドで設定します。|  
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|ワークフローが停止された理由。 このプロパティは、プロパティ グリッドで設定します。|  
  
## <a name="see-also"></a>関連項目  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)   
 [Persist](../workflow-designer/persist-activity-designer.md)