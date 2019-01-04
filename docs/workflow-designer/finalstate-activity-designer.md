---
title: ワークフロー デザイナーで FinalState アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 55fc609ffd327d1e3bea8ee52849c92746055410
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950528"
---
# <a name="finalstate-activity-designer"></a>FinalState アクティビティ デザイナー

<xref:System.Activities.Core.Presentation.FinalState> デザイナーは、ステート マシンのインスタンスを終了する <xref:System.Activities.Statements.State> を作成するために使用されます。

## <a name="using-the-finalstate-activity-designer"></a>FinalState アクティビティ デザイナーの使用

**FinalState**デザイナーを使用して、作成、<xref:System.Activities.Statements.State>がステート マシン内の最終状態として事前に構成します。 A<xref:System.Activities.Statements.State>で作成した、<xref:System.Activities.Core.Presentation.FinalState>アクティビティ デザイナーがその<xref:System.Activities.Statements.State.IsFinal%2A>プロパティに設定**true**、にない<xref:System.Activities.Statements.State.Exit%2A>アクティビティとその送信元から遷移はありません。 使用する、<xref:System.Activities.Core.Presentation.FinalState>を追加するアクティビティ デザイナー、 <xref:System.Activities.Statements.State> 、ステート マシン内の最終状態として事前構成済みであるアクティビティをドラッグ、 **FinalState**からアクティビティ デザイナー、**ステート マシン**のセクション、**ツールボックス**し、ワークフロー デザイナーにドロップします。 <xref:System.Activities.Core.Presentation.FinalState> アクティビティ デザイナーは、<xref:System.Activities.Statements.StateMachine> にドロップして遷移を後で追加できます。または遷移は、<xref:System.Activities.Core.Presentation.FinalState> アクティビティ デザイナーをドロップしたときに作成できます。 遷移の作成の詳細については、次を参照してください。[遷移](../workflow-designer/transition-activity-designer.md)します。

### <a name="state-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの State アクティビティのプロパティ

次の表に、<xref:System.Activities.Core.Presentation.FinalState> デザイナーを使用して設定できるプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティの中には、プロパティ グリッドで編集できるものがあります。また、その一部はデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.State> アクティビティ デザイナーの表示名を指定します。 既定値は**状態**します。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。 <xref:System.Activities.Statements.State.DisplayName%2A> は、ワークフロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.State.Entry%2A>|False|この状態の遷移時に発生するアクションを指定します。 アクティビティをドラッグしてこの値を設定することができます、**ツールボックス**にドロップし、<xref:System.Activities.Statements.State.Entry%2A>状態のセクション。|

## <a name="see-also"></a>関連項目

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [状態](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)