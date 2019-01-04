---
title: ワークフロー デザイナー - TerminateWorkflow アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.TerminateWorkflow.UI
ms.assetid: 08e632ed-0724-4fb4-9df1-f8d443eaf0ac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8dc6328e2363e802d05093bfebd25479d67c6ffa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858501"
---
# <a name="terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナー

**TerminateWorkflow**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.TerminateWorkflow>アクティビティ。

## <a name="the-terminateworkflow-activity"></a>TerminateWorkflow アクティビティ

<xref:System.Activities.Statements.TerminateWorkflow> アクティビティは、ワークフローの実行を停止します。

### <a name="using-the-terminateworkflow-activity-designer"></a>TerminateWorkflow アクティビティ デザイナーの使用

**TerminateWorkflow**アクティビティ デザイナーが記載されて、**ランタイム**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X)。

**TerminateWorkflow**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.TerminateWorkflow> 、既定値は、アクティビティ**DisplayName** TerminateWorkflow の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **TerminateWorkflow**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-terminateworkflow-properties"></a>TerminateWorkflow のプロパティ

次の表に、<xref:System.Activities.Statements.TerminateWorkflow> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集することができ、その一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.TerminateWorkflow> アクティビティの表示名。 既定値は TerminateWorkflow です。 表示名は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.TerminateWorkflow.Exception%2A>|False|ワークフローが停止されたときにスローする例外。 このプロパティは、プロパティ グリッドで設定します。|
|<xref:System.Activities.Statements.TerminateWorkflow.Reason%2A>|False|ワークフローが停止された理由。 このプロパティは、プロパティ グリッドで設定します。|

## <a name="see-also"></a>関連項目

- [ランタイム](../workflow-designer/runtime-activity-designers.md)
- [Persist](../workflow-designer/persist-activity-designer.md)