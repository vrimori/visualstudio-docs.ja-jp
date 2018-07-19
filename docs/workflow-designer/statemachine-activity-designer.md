---
title: ワークフロー デザイナーの StateMachine アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9c7afb2131ae6e05c8232eb8dc735e5131698a69
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758233"
---
# <a name="statemachine-activity-designer"></a>StateMachine アクティビティ デザイナー

<xref:System.Activities.Statements.StateMachine> アクティビティには状態のコレクションが含まれており、一般的なステート マシン パラダイムを使用してワーク フローをモデル化します。

## <a name="using-the-statemachine-activity-designer"></a>StateMachine アクティビティ デザイナーの使用

追加する、<xref:System.Activities.Statements.StateMachine>アクティビティをドラッグ、 **StateMachine**からアクティビティ デザイナー、**ステート マシン**のセクション、**ツールボックス**し、ワークフロー デザイナーにドロップします。画面。 この子の状態を追加する<xref:System.Activities.Statements.StateMachine>アクティビティをドラッグ、<xref:System.Activities.Statements.State>または<xref:System.Activities.Core.Presentation.FinalState>から、**ツールボックス**にドロップし、 **StateMachine**します。

### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの StateMachine アクティビティのプロパティ

次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.StateMachine> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部はデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.StateMachine> アクティビティ デザイナーの表示名を指定します。 既定値は**StateMachine**します。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。 <xref:System.Activities.Activity.DisplayName%2A> は、ワークフロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [フローチャート](../workflow-designer/flowchart-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)