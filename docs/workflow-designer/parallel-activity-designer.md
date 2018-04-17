---
title: アクティビティ デザイナーの並列 |Microsoft ドキュメント
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1c3f24af736dfd3762de7942ba1f52442dfd20c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="parallel-activity-designer"></a>Parallel アクティビティ デザイナー
<xref:System.Activities.Statements.Parallel> アクティビティは、一連の子アクティビティを同時に実行するアクティビティです。

## <a name="the-parallel-activity"></a>Parallel アクティビティ
 <xref:System.Activities.Statements.Parallel> アクティビティは、子アクティビティを <xref:System.Activities.Statements.Parallel.Branches%2A> コレクションに格納します。 一部の子アクティビティがアイドル状態になる可能性がある場合は、<xref:System.Activities.Statements.Parallel> アクティビティの代わりに <xref:System.Activities.Statements.Sequence> アクティビティを使用してください。

 <xref:System.Activities.Statements.Parallel> アクティビティには、ユーザーによって指定された <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> 式を保持する [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] プロパティがあります。 このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.Parallel> アクティビティによって評価されます。 評価結果が場合**True**、<xref:System.Activities.Statements.Parallel>アクティビティは他の分岐を実行せずに完了します。 場合、<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>に評価されない**True**、<xref:System.Activities.Statements.Parallel>アクティビティのすべての子アクティビティが完了したときに完了します。

### <a name="using-the-parallel-activity-designer"></a>Parallel アクティビティ デザイナーの使用
 **並列**アクティビティ デザイナーは含まれて、**制御フロー**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。

 **並列**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所アクティビティ デザイナーを通常配置しているなど、の内部で**シーケンス**アクティビティ デザイナー。 ドロップすた後、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]、作成、<xref:System.Activities.Statements.Parallel>アクティビティで、既定で含まれて、<xref:System.Activities.Activity.DisplayName%2A>の**並列**

 活動を追加する、 <xref:System.Activities.Statements.Parallel.Branches%2A> 、並列アクティビティのコレクションから他のアクティビティ デザイナーをドラッグして、**ツールボックス**内の三角形の上にドロップし、**並列**アクティビティ デザイナー。 分岐に含まれるアクティビティのそばに三角形が配置されます。 この手順を繰り返すことによって、さらにアクティビティを追加できます。 ドラッグ アンド ドロップします内でアクティビティを並べ替えることができます、**並列**アクティビティ デザイナー。

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Parallel アクティビティのプロパティ
 次の表に、Parallel アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーのアクティビティ デザイナーの表示名を指定します。 既定値は**並列**です。 値を必要に応じて編集できます、**プロパティ**グリッド アクティビティ デザイナーのヘッダーで直接またはします。|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|実行される子アクティビティのコレクションが格納されます。|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|分岐の完了後に評価されます。 評価された場合**True**、スケジュールされた保留分岐はキャンセルされます。 このプロパティが設定されていないかに評価される場合**False**、すべての子アクティビティが完了すると、アクティビティが完了します。 既定値は**null**です。|

## <a name="see-also"></a>関連項目

- [シーケンス](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)