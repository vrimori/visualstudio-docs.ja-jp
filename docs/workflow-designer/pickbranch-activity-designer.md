---
title: ワークフロー デザイナー - PickBranch アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29b7cc9d61f7be551e5b53e053a86586bab8708b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916270"
---
# <a name="pickbranch-activity-designer"></a>PickBranch アクティビティ デザイナー

<xref:System.Activities.Statements.PickBranch> は、受信イベントによってトリガー可能な、<xref:System.Activities.Statements.Pick> アクティビティ内のイベント ベースの実行パスを提供します。

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick.Branches%2A> アクティビティの <xref:System.Activities.Statements.Pick> コレクションに格納されます。 各 <xref:System.Activities.Statements.PickBranch> は <xref:System.Activities.Statements.Pick> アクティビティの分岐に格納され、トリガーの役割を果たす受信イベントに応答して実行できます。 この方法では、ワークフロー デザイナーは、イベント ベースの制御フロー モデリングを提供します。 各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> および <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。

### <a name="how-to-use-the-pick-activity-designer"></a>Pick アクティビティ デザイナーの使用方法

アクセス、 **PickBranch**でデザイナー、**制御フロー**のカテゴリ、**ツールボックス**します。

2 つの空<xref:System.Activities.Statements.PickBranch>を持つオブジェクトの名前を表示する**Branch1**と**Branch2**の要素として、既定で作成された、<xref:System.Activities.Statements.Pick>アクティビティと、**選択**アクティビティ デザイナーはワークフロー デザイナーに最初に削除されます。 これらそれぞれ<xref:System.Activities.Statements.PickBranch.DisplayName%2A>でプロパティ値を編集できる、 **PickBranch**デザイナーのヘッダー内、または、**プロパティ**各分岐はウィンドウ。

追加する 2 つの方法はあります<xref:System.Activities.Statements.PickBranch>オブジェクトのコレクションを<xref:System.Activities.Statements.Pick>オブジェクト: ドラッグ アンド ドロップ、 **PickBranch**からデザイナー、**ツールボックス**を右クリック メニューを使用して、または内で、**選択**デザイン画面。

- **PickBranch**デザイナーを作成、<xref:System.Activities.Statements.PickBranch>からドラッグされるときに、**ツールボックス**の分岐の 1 つにドロップして、**選択**上のアクティビティ デザイナー、ワークフロー デザイナー画面。 新しい <xref:System.Activities.Statements.PickBranch> オブジェクトは、<xref:System.Activities.Statements.Pick> デザイナー内で、コレクションに含まれている既存の <xref:System.Activities.Statements.PickBranch> 要素の左側または右側に配置できます。 ドラッグしたときに、 **PickBranch**デザイナー上に、**選択**マウス、デザイナー、**選択**デザイナーでは、青灰色の縦の帯を使用して、場所を示します、 <xref:System.Activities.Statements.PickBranch>位置に追加されます。

- 右クリックして**選択**アクティビティ デザイナー (内部ではない**PickBranch**デザイナー) を選択し、コンテキスト メニューを**分岐の作成**新しいを追加する<xref:System.Activities.Statements.PickBranch>します。 注意して、新しい<xref:System.Activities.Statements.PickBranch>が既存の右側に追加<xref:System.Activities.Statements.PickBranch>内のオブジェクト、**選択**デザイナー。

**PickBranch**デザイナーを展開すると、**トリガー**と**アクション**ボックスまたはクリックすると、ヘッダーの右側にある二重のキャレットで折りたたまれています。 編集、<xref:System.Activities.Statements.PickBranch.Trigger%2A>と<xref:System.Activities.Statements.PickBranch.Action%2A>それぞれの<xref:System.Activities.Statements.PickBranch>にアクティビティをドロップすることによって、**トリガー**と**アクション**そのデザイナーのボックスです。

<xref:System.Activities.Statements.PickBranch>内のオブジェクト、<xref:System.Activities.Statements.Pick.Branches%2A>のコレクションを<xref:System.Activities.Statements.Pick>オブジェクトをドラッグ アンド ドロップし、内の新しい場所にして並べ替えることができる、**選択**デザイナー。 **選択**デザイナーは青灰色の縦の帯で示されます使用して、<xref:System.Activities.Statements.PickBranch>位置が追加されます。

<xref:System.Activities.Statements.PickBranch> は 2 とおりの方法で削除できます。

- 選択、 **PickBranch**デザイナーして削除します。
- 選択、 **PickBranch**デザイナー、右クリックして選択し、コンテキスト メニューを**削除**します。

オンにしてください、 **PickBranch**デザイナー内のアクティビティのいずれかを選択すると、その**トリガー**または**アクション**ボックスが、誤ってこれらの活動の 1 つを削除および not<xref:System.Activities.Statements.PickBranch>オブジェクト。

### <a name="pickbranch-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの PickBranch のプロパティ

次の表は、最も役に立つ<xref:System.Activities.Statements.PickBranch>プロパティと、ワークフロー デザイナーで使用する方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|ヘッダーに表示されるフレンドリ名、 **PickBranch**デザイナー。 既定値は Branch です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|各 <xref:System.Activities.Statements.PickBranch> には、<xref:System.Activities.Statements.PickBranch.Trigger%2A> を呼び出すことのできる <xref:System.Activities.Statements.PickBranch.Action%2A> アクションが含まれます。|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|各 <xref:System.Activities.Statements.PickBranch> には、トリガーされたときに実行される <xref:System.Activities.Statements.PickBranch.Action%2A> が含まれます。|

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)
- [Pick アクティビティ](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick アクティビティの使用](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)