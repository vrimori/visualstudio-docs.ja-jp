---
title: ワークフロー デザイナー - CancellationScope アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975342"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナー

**CancellationScope**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.CancellationScope>アクティビティ。

## <a name="the-cancellationscope-activity"></a>CancellationScope アクティビティ
 <xref:System.Activities.Statements.CancellationScope> アクティビティを使用すると、実行のアクティビティと、そのアクティビティの取り消しロジックを指定できます。

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope アクティビティ デザイナーの使用
 **CancellationScope**アクティビティ デザイナーは含まれて、**トランザクション**のカテゴリ**ツールボックス**です。 開くには**ツールボックス**、select、**ツールボックス**ワークフロー デザイナーのタブです。 また、選択**ツールバー**から、**ビュー**メニューのまたは ctrl キーと alt キーを押しながら X キーを押します。

 **CancellationScope**からアクティビティ デザイナーをドラッグできる**ツールボックス**アクティビティを配置して、このような内の場所に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>です。 削除する、 **CancellationScope**アクティビティ デザイナーを作成、 <xref:System.Activities.Statements.CancellationScope> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>CancellationScope のです。 編集、<xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値、 **CancellationScope**アクティビティ デザイナー。 編集することも、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-cancellationscope-properties"></a>CancellationScope プロパティ
 次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A>プロパティは、プロパティ グリッドで編集できますが、ワークフロー デザイナー画面で、他のプロパティを編集する必要があります。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> アクティビティの省略可能な表示名。 既定では、CancellationScope です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|取り消しロジックの対象となるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.Body%2A>アクティビティ、アクティビティをドロップ**ツールボックス**に、**本文**ボックスに、 **CancellationScope**アクティビティ デザイナー。 "ドロップ アクティビティ Here"というヒント テキストを追加します。|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|取り消しがある場合に実行されるアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>アクティビティ、アクティビティをドロップ**ツールボックス**に、 **CancellationHandler**ボックスに、 **CancellationScope**アクティビティ デザイナー。 "ドロップ アクティビティ Here"というヒント テキストを追加します。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [補正](../workflow-designer/compensate-activity-designer.md)
- [確認します。](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)