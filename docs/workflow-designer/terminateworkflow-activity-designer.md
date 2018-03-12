---
title: "TerminateWorkflow アクティビティ デザイナー |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 683c482436e968ff9d2a1bd4ce0bbb8e173a5520
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
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

## <a name="see-also"></a>関連項目

- [ランタイム](../workflow-designer/runtime-activity-designers.md)
- [永続化します。](../workflow-designer/persist-activity-designer.md)