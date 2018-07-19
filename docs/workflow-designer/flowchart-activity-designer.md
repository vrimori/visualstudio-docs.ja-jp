---
title: ワークフロー デザイナー、フローチャート アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Flowchart.UI
- System.Activities.Statements.FlowStep.UI
- System.Activities.Core.Presentation.FlowStart.UI
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dd44a91ac2a3d823c5a5690edbdd57422857ea9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755629"
---
# <a name="flowchart-activity-designer"></a>フローチャート アクティビティ デザイナー

<xref:System.Activities.Statements.Flowchart> アクティビティは、複雑なフロー制御を定義および管理するワークフローを作成するために使用します。 A<xref:System.Activities.Statements.Flowchart>コードまたはワークフロー デザイナーを使用して作成できます。 このトピックでは、ワークフロー デザイナーのエクスペリエンスを説明します。 ワークフロー デザイナー ワークフローのアクティビティ デザイナーには、自然な形でワークフローを作成する開発者が使用できます。

## <a name="the-flowchart-activity"></a>Flowchart アクティビティ

<xref:System.Activities.Statements.Flowchart> では、ワークフローの開始時に実行される一意の <xref:System.Activities.Statements.Flowchart.StartNode%2A> を指定します。また、リンクされた <xref:System.Activities.Statements.Flowchart.Nodes%2A> のネットワークを使用して、任意のループを作成したり、特定の時点で実行フローの経路をワークフロー内の任意のポイントへ移動したりします。

### <a name="using-the-flowchart-activity-designer"></a>Flowchart アクティビティ デザイナーの使用

**フローチャート**アクティビティ デザイナーが記載されて、**フローチャート**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**フローチャート**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティ デザイナーは通常配置して、ルート アクティビティとして、またはとして任意の場所は、ワークフロー デザイナー画面にドロップし、もう 1 つの制御フロー アクティビティの子です。 場合、**フローチャート**アクティビティ デザイナーが空のワークフロー デザイナー画面にドロップされる、作成、<xref:System.Activities.Statements.Flowchart>アクティビティは、既定では実行を開始する開始ノードの展開ビューに表示されます緑色のボールとして表されます。 場合、**フローチャート**アクティビティ デザイナーが別の制御フロー アクティビティにドロップをダブルクリックして展開できる最小化されたビューで表示されます、**フローチャート**アクティビティ デザイナー。 任意の動作、**ツールボックス**に直接ドラッグすることができます、**フローチャート**など他の制御フロー アクティビティのアクティビティ デザイナー。

さまざまなアクティビティ デザイナーをワークフロー デザイナー キャンバスにドラッグした後、<xref:System.Activities.Activity>を表すオブジェクトをリンクする実行の順序を指定するためにします。 接続元アクティビティと接続先アクティビティの間のリンクを作成するには、接続元アクティビティのデザイナー上にマウス ポインターを置きます。これで、その両側に正方形のハンドルが表示されます。 そのハンドルのどちらかをクリックし、マウス ボタンを押したまま、接続先アクティビティをマウスでポイントしたときにその周りに同様に表示されるハンドルのどちらかにドラッグします。 マウス ボタンを放すと、この 2 つのアクティビティの間にリンクが作成されます。このリンクは、接続元デザイナーから接続先デザイナーへの矢印で表されます。

### <a name="flowchart-activity-properties"></a>Flowchart アクティビティのプロパティ

次の表に、<xref:System.Activities.Statements.Flowchart> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドまたはデザイナー画面で編集できます。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーのアクティビティ デザイナーの表示名を指定します。 既定値は Flowchart です。 値を編集できる、**プロパティ**ウィンドウまたは直接アクティビティ デザイナーのヘッダー。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|子アクティビティ間で状態を共有するために、この <xref:System.Activities.Statements.Flowchart> 内にスコープ設定された変数のコレクション。|
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|<xref:System.Activities.Statements.FlowNode> の開始時に実行される <xref:System.Activities.Statements.Flowchart>。|
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|<xref:System.Activities.Statements.FlowNode> 内の <xref:System.Activities.Statements.Flowchart> オブジェクトのコレクションが格納されます。|

## <a name="see-also"></a>関連項目

- [フローチャート](../workflow-designer/flowchart-activity-designers.md)
- [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)
- [FlowSwitch\<T>](../workflow-designer/flowswitch-t-activity-designer.md)