---
title: ワークフロー デザイナー - Assign アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Assign.UI
ms.assetid: ba3feb3c-f144-47ea-926d-cf752b804153
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44d825d5d6ee36876c807ce067c71c1b10896623
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="assign-activity-designer"></a>Assign アクティビティ デザイナー

**割り当てる**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.Assign>アクティビティ。

## <a name="the-assign-activity"></a>Assign アクティビティ

<xref:System.Activities.Statements.Assign> アクティビティで、変数または引数に値を割り当てます。

### <a name="using-the-assign-activity-designer"></a>Assign アクティビティ デザイナーの使用

**割り当てる**アクティビティ デザイナーは含まれて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブ (または、選択**ツールボックス**から、**ビュー**メニューまたは CTRL + ALT + X です)。

**割り当てる**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**、ずっとアクティビティを配置して、このような内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>です。 削除する、**割り当てる**アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.Assign> 、既定値を持つアクティビティ**DisplayName**割り当てのです。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**割り当てる**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-assign-properties"></a>Assign のプロパティ

次の表に、<xref:System.Activities.Statements.Assign> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集することができ、それらの一部は、ワークフロー デザイナー画面で編集することができます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Assign> アクティビティの表示名。 既定値は Assign です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Assign.To%2A>|True|<xref:System.Activities.Statements.Assign.Value%2A> を割り当てる変数または引数。 値は、有効な Visual Basic 識別子でなければなりません。 プロパティを設定するには、Visual Basic の式を入力、**に**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|
|<xref:System.Activities.Statements.Assign.Value%2A>|True|変数に割り当てられる値。 設定する、 <xref:System.Activities.Statements.Assign.Value%2A>、Visual Basic の式を入力、**値**ボックスに、**割り当てる**アクティビティ デザイナーまたはプロパティ グリッドでします。|

## <a name="see-also"></a>関連項目

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [遅延](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)