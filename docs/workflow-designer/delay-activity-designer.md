---
title: ワークフロー デザイナー - Delay アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c26bcbe535d45e81cb37138d26192271437b9fb6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981572"
---
# <a name="delay-activity-designer"></a>Delay アクティビティ デザイナー

**遅延**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Delay>アクティビティ。

## <a name="the-delay-activity"></a>Delay アクティビティ

<xref:System.Activities.Statements.Delay> アクティビティで、ワークフローの実行を、指定した時間だけ遅らせます。

### <a name="use-the-delay-activity-designer"></a>Delay アクティビティ デザイナーを使用します。

**遅延**アクティビティ デザイナーが記載されて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**遅延**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**どこにも、アクティビティを通常配置など内に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップする作成されます、 <xref:System.Activities.Statements.Delay> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>の遅延。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**遅延**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-delay-properties"></a>Delay のプロパティ

次の表は、<xref:System.Activities.Statements.Delay>プロパティと、デザイナーでの使用方法について説明します。 これらのプロパティは、プロパティ グリッドで編集でき、その一部は、ワークフロー デザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> アクティビティの表示名。 既定値は Delay です。 ただし、<xref:System.Activities.Activity.DisplayName%2A>値が厳密には必要ありません、1 つを使用することをお勧めします。|
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|ワークフローの実行を遅らせる時間の長さ。 このプロパティは、プロパティ グリッドで設定します。 時間の長さを指定するには、00:00:00 という形式のリテラル <xref:System.TimeSpan>、または Visual Basic の式を入力します。|

## <a name="see-also"></a>関連項目

- [Primitives](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Delay アクティビティ デザイナー](../workflow-designer/delay-activity-designer.md)
- [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)