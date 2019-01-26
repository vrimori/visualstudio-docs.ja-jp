---
title: アクティビティ デザイナーの中に、ワークフロー デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81caba883293a59fe67988d34785758340b4705a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54987038"
---
# <a name="while-activity-designer"></a>While アクティビティ デザイナー

<xref:System.Activities.Statements.While>アクティビティに含まれるアクティビティを実行します。 その<xref:System.Activities.Statements.While.Body%2A>中、指定した<xref:System.Activities.Statements.While.Condition%2A>に評価される**true**。 場合によっては、含まれているアクティビティが実行されない可能性があります。 含まれているアクティビティを少なくとも 1 回は実行する必要がある場合は、<xref:System.Activities.Statements.DoWhile> アクティビティを代わりに使用します。

## <a name="while-properties-in-workflow-designer"></a>ワークフロー デザイナーでの While のプロパティ

次の表に、最も役に立つ <xref:System.Activities.Statements.While> アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.While> アクティビティ デザイナーの表示名を指定します。 既定値は While です。 値を編集できる、**プロパティ**ウィンドウまたは直接アクティビティ デザイナーのヘッダー。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.While.Body%2A>|False|実行するアクティビティが含まれています中に、<xref:System.Activities.Statements.While.Condition%2A>に評価される**true**します。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|判断するために評価は、Visual Basic の式が含まれて かどうかのアクティビティ、<xref:System.Activities.Statements.While.Body%2A>を実行します。|

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)