---
title: "While アクティビティ デザイナー |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 541113e598246cf20f9fe625f57c51f68d7e9ca8
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="while-activity-designer"></a>While アクティビティ デザイナー
<xref:System.Activities.Statements.While>に含まれているアクティビティを実行、<xref:System.Activities.Statements.While.Body%2A>中に、指定した<xref:System.Activities.Statements.While.Condition%2A>に評価される**true**です。 場合によっては、含まれているアクティビティが実行されない可能性があります。 含まれているアクティビティを少なくとも 1 回は実行する必要がある場合は、<xref:System.Activities.Statements.DoWhile> アクティビティを代わりに使用します。

## <a name="while-properties-in-workflow-designer"></a>ワークフロー デザイナーでの While のプロパティ
 次の表に、最も役に立つ <xref:System.Activities.Statements.While> アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.While> アクティビティ デザイナーの表示名を指定します。 既定値は While です。 値を編集できます、**プロパティ**ウィンドウ アクティビティ デザイナーのヘッダーで直接またはします。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.While.Body%2A>|False|実行するアクティビティを含む中に、<xref:System.Activities.Statements.While.Condition%2A>に評価される**true**です。|
|<xref:System.Activities.Statements.While.Condition%2A>|True|[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] に含まれるアクティビティを実行するかどうかを決定するために評価される <xref:System.Activities.Statements.While.Body%2A> の式が含まれます。|

## <a name="see-also"></a>関連項目

- [制御フロー](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)