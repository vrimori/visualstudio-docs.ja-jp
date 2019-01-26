---
title: ワークフロー デザイナーの Sequence アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82d7f8d61f3aa170d20bc46e1d7f530d56de0f25
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001109"
---
# <a name="sequence-activity-designer"></a>Sequence アクティビティ デザイナー

<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。

他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。 使用を検討して、[フローチャート](../workflow-designer/flowchart-activity-designer.md)単純な分岐またはループのダイアグラムでモデル化するプログラム フローがある場合。

## <a name="using-the-sequence-activity-designer"></a>Sequence アクティビティ デザイナーの使用

追加する、<xref:System.Activities.Statements.Sequence>アクティビティをドラッグ、**シーケンス**からアクティビティ デザイナー、**ツールボックス**し、ワークフロー デザイナー画面にドロップします。 これに子アクティビティを追加する<xref:System.Activities.Statements.Sequence>アクティビティから他のアクティビティをドラッグ、**ツールボックス**し、「ここにアクティビティをドロップ」というヒント テキスト ボックスにある三角形にドロップします。

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Sequence アクティビティのプロパティ

次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。 既定値は Sequence です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [フローチャート](../workflow-designer/flowchart-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)