---
title: ワークフロー デザイナーの ForEach&lt;T&gt;アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.ForEach`1.UI
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 681a89bd9c31cc4682e3ba7f5b9b0762f0ad8983
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830311"
---
# <a name="foreachlttgt-activity-designer"></a>ForEach&lt;T&gt;アクティビティ デザイナー

<xref:System.Activities.Statements.ForEach%601> アクティビティは、指定した <xref:System.Activities.Statements.ForEach%601.Body%2A> コレクション内の各項目に対して、<xref:System.Activities.Statements.ForEach%601.Values%2A> に含まれるアクティビティを実行します。

## <a name="foreacht-properties-in-the-workflow-designer"></a>ForEach < T\>ワークフロー デザイナーでのプロパティ

次の表に、最も役に立つ <xref:System.Activities.Statements.ForEach%601> アクティビティのプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ForEach%601> アクティビティの表示名。 既定値は ForEach < Int32\>します。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|反復処理を行う項目のコレクション。 設定する、 <xref:System.Activities.Statements.ForEach%601.Values%2A>、Visual Basic の式を入力、**値**ボックスに、 **ForEach < T\>** アクティビティ デザイナーまたはプロパティ グリッドでします。|
|*TypeArgument*|True|内の項目の種類、<xref:System.Activities.Statements.ForEach%601.Values%2A>ジェネリック パラメーターで指定されたコレクション*T*します。既定では、 *TypeArgument*に設定されている**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドのコンボ ボックス。|

既定では、ループの反復子が名前付き**項目**します。 反復子変数の名前は、<xref:System.Activities.Statements.ForEach%601> アクティビティ デザイナーで変更できます。 ループ反復子は、<xref:System.Activities.Statements.ForEach%601> アクティビティの子の式で使用できます。

## <a name="see-also"></a>関連項目

- [ParallelForEach\<T>](../workflow-designer/parallelforeach-t-activity-designer.md)
- [制御フロー](../workflow-designer/control-flow-activity-designers.md)