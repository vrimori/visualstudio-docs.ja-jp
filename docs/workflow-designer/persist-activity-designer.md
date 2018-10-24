---
title: ワークフロー デザイナー - Persist アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51f74b5348c7e99824659ee713171bd71c5f522e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831343"
---
# <a name="persist-activity-designer"></a>Persist アクティビティ デザイナー

**Persist**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Persist>アクティビティ。

## <a name="the-persist-activity"></a>Persist アクティビティ

<xref:System.Activities.Statements.Persist> アクティビティで、ワークフローをディスクに保存します (可能な場合)。 <xref:System.Activities.Statements.Persist> アクティビティは、<xref:System.Activities.Statements.TransactionScope> アクティビティ内などの非永続化ゾーンでは実行できません。 非永続化スコープで <xref:System.Activities.Statements.Persist> アクティビティを使用すると、実行時に例外がスローされます。

### <a name="using-the-persist-activity-designer"></a>Persist アクティビティ デザイナーの使用

**Persist**アクティビティ デザイナーが記載されて、**ランタイム**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X)。

**Persist**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.Persist> 、既定値は、アクティビティ**DisplayName**の永続化します。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、 **Persist**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-persist-properties"></a>Persist のプロパティ

次の表に、<xref:System.Activities.Statements.Persist> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集することができ、その一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> アクティビティの表示名。 既定値は Persist です。 表示名は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [ランタイム](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)