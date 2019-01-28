---
title: ワークフロー デザイナーで Pick アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Pick.UI
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3afd20b75bdb2c00317f9acf6ec6adcd12f6f949
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069784"
---
# <a name="pick-activity-designer"></a>Pick アクティビティ デザイナー

<xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御フローを提供します。 このアクティビティは、トリガー起動イベントに応答して、複数の分岐のいずれか 1 つを実行します。

## <a name="the-pick-activity"></a>Pick アクティビティ

<xref:System.Activities.Statements.Pick> アクティビティには、<xref:System.Activities.Statements.PickBranch> オブジェクトのコレクションが含まれており、<xref:System.Activities.Statements.Pick> アクティビティはそのオブジェクトの 1 つを、トリガーの役割を果たす受信イベントに応答して実行できます。 この方法では、ワークフロー デザイナーは、イベント ベースの制御フロー モデリングを提供します。 各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。 先頭に、<xref:System.Activities.Statements.Pick>アクティビティの実行のすべてのトリガー アクティビティ、<xref:System.Activities.Statements.PickBranch>要素がスケジュールされます。 最初のアクティビティが完了すると、対応するアクション アクティビティがスケジュールされ、他のすべてのトリガー アクティビティは取り消されます。

### <a name="how-to-use-the-pick-activity-designer"></a>Pick アクティビティ デザイナーの使用方法

アクセス、**選択**内のアクティビティ デザイナー、**制御フロー**のカテゴリ、**ツールボックス**します。 **選択**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティ デザイナーは通常、配置内での例についてはどこにも、ワークフロー デザイナー画面にドロップし、 **シーケンス**アクティビティ デザイナー。 ワークフロー デザイナーにドロップすると、作成、<xref:System.Activities.Statements.Pick>を既定で 2 つの空を含むアクティビティは、<xref:System.Activities.Statements.PickBranch>で要素としてのアクティビティは、Branch1 および Branch2 の名前を表示します。 これらそれぞれ<xref:System.Activities.Statements.PickBranch.DisplayName%2A>でプロパティ値を編集できる、 **PickBranch**アクティビティ デザイナーのヘッダー内、または、**プロパティ**各分岐はウィンドウ。

追加する 2 つの方法はあります<xref:System.Activities.Statements.PickBranch>のコレクションにアクティビティを<xref:System.Activities.Statements.Pick>オブジェクト: ドラッグ アンド ドロップ、 **PickBranch**からデザイナー、**ツールボックス**または右クリック メニューを使用して内から、**選択**デザイン サーフェイス。 詳細については、次を参照してください。、 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)トピック。 内に配置できることのみいる項目に注意してください、**選択**アクティビティ デザイナーは、 **PickBranch**アクティビティ デザイナー。

### <a name="pick-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの Pick アクティビティのプロパティ

次の表に、<xref:System.Activities.Statements.Pick> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.Pick> アクティビティ デザイナーの表示名を指定します。 既定値は Pick です。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)
- [Pick アクティビティ](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick アクティビティの使用](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)