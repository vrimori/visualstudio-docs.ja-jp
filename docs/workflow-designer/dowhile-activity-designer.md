---
title: ワークフロー デザイナー - DoWhile アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a674cf58740fe914d00ae1ebfdeb5b642716e37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960556"
---
# <a name="dowhile-activity-designer"></a>DoWhile アクティビティ デザイナー

<xref:System.Activities.Statements.DoWhile>アクティビティに含まれるアクティビティを実行します。 その<xref:System.Activities.Statements.DoWhile.Body%2A>を少なくとも 1 回に、指定した条件が評価されるまで**false**します。 ループの本体に含まれるアクティビティを 0 回以上実行する必要がある場合は、代わりに、<xref:System.Activities.Statements.While> アクティビティを使用します。

## <a name="dowhile-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの DoWhile のプロパティ

次の表は、最も役に立つ<xref:System.Activities.Statements.DoWhile>アクティビティのプロパティをデザイナーで使用する方法について説明します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|条件がときに実行するアクティビティ**true**します。 追加する、<xref:System.Activities.Statements.DoWhile.Body%2A>アクティビティ、アクティビティをツールボックスからドロップ、**本文**ボックスに、 **DoWhile**アクティビティ デザイナーの「ドロップ アクティビティここ」ヒント テキスト。|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|ループの各繰り返しの後に評価する条件。 設定する、 <xref:System.Activities.Statements.DoWhile.Condition%2A>、Visual Basic の式を入力、**条件**ボックスに、 **DoWhile**アクティビティ デザイナーまたはプロパティ グリッドでします。|

## <a name="see-also"></a>関連項目

- [While](../workflow-designer/while-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)