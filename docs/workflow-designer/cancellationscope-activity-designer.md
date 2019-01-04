---
title: ワークフロー デザイナー、CancellationScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 124b4d5d1b8e35611d990fd6c169a880a4e13a5c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872253"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナー

**CancellationScope**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.CancellationScope>アクティビティ。

## <a name="the-cancellationscope-activity"></a>CancellationScope アクティビティ

<xref:System.Activities.Statements.CancellationScope> アクティビティを使用すると、実行のアクティビティと、そのアクティビティの取り消しロジックを指定できます。

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナーの使用

**CancellationScope**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ**ツールボックス**します。 開くには**ツールボックス**を選択、**ツールボックス**ワークフロー デザイナーのタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**CancellationScope**からアクティビティ デザイナーをドラッグできる**ツールボックス**アクティビティを配置して、このような内の場所には、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 削除、 **CancellationScope**アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.CancellationScope> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>CancellationScope の。 編集、<xref:System.Activities.Activity.DisplayName%2A>のヘッダー値、 **CancellationScope**アクティビティ デザイナー。 編集することも、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-cancellationscope-properties"></a>CancellationScope プロパティ

次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A>プロパティ グリッドでプロパティを編集できますが、その他のプロパティは、ワークフロー デザイナー画面で編集する必要があります。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> アクティビティの省略可能な表示名。 既定では、CancellationScope です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|取り消しロジックの対象となるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.Body%2A>アクティビティからアクティビティのドロップ**ツールボックス**に、**本文**ボックスに、 **CancellationScope**アクティビティ デザイナー。 ヒント テキストを「アクティビティここにドロップ」を追加します。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|取り消しがある場合に実行されるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>アクティビティからアクティビティのドロップ**ツールボックス**に、 **CancellationHandler**ボックスに、 **CancellationScope**アクティビティ デザイナー。 ヒント テキストを「アクティビティここにドロップ」を追加します。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)