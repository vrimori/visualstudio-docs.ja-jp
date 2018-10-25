---
title: ワークフロー デザイナーの Sequence アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 288e184f2ae2b4df74860a2cd8066d00e02a44c2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950590"
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