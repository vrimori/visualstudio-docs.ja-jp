---
title: "アクティビティ デザイナーをシーケンス |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Sequence.UI
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 64ec037433ca4ff984628994ba2bf353ad8e365c
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="sequence-activity-designer"></a>Sequence アクティビティ デザイナー
<xref:System.Activities.Statements.Sequence> アクティビティには、子アクティビティの順序付きコレクションが含まれており、これらのコレクションが順番に実行されます。

 他の方法でアクティビティのセットを順番に実行するには、<xref:System.Activities.Statements.Flowchart> アクティビティを使用します。 使用を検討して、[フローチャート](../workflow-designer/flowchart-activity-designer.md)がある場合、単純な分岐または図をモデル化するプログラム フローをループします。

## <a name="using-the-sequence-activity-designer"></a>Sequence アクティビティ デザイナーの使用
 追加する、<xref:System.Activities.Statements.Sequence>アクティビティをドラッグ、**シーケンス**からアクティビティ デザイナー、**ツールボックス**し、Windows ワークフロー デザイナーのサーフェイスにドロップします。 これに子アクティビティを追加する<xref:System.Activities.Statements.Sequence>アクティビティから他のアクティビティをドラッグして、**ツールボックス**し、「ここにアクティビティをドロップ」というヒント テキストをボックスにある三角形にドロップします。

### <a name="sequence-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Sequence アクティビティのプロパティ
 次の表に、<xref:System.Activities.Statements.Sequence> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Sequence> アクティビティ デザイナーの表示名を指定します。 既定値は Sequence です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [フローチャート](../workflow-designer/flowchart-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)