---
title: ワークフロー デザイナー - Rethrow アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d441724afa1cf481bc15e2a43e6ec744a951187
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973837"
---
# <a name="rethrow-activity-designer"></a>Rethrow アクティビティ デザイナー

**Rethrow**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.Rethrow>アクティビティ。

## <a name="the-rethrow-activity"></a>Rethrow アクティビティ
 <xref:System.Activities.Statements.Rethrow> アクティビティでは、以前にスローされた例外をスローします。 このアクティビティは、<xref:System.Activities.Statements.Catch> アクティビティの <xref:System.Activities.Statements.TryCatch> ハンドラーでのみ使用できます。

### <a name="using-the-rethrow-activity-designer"></a>ReThrow アクティビティ デザイナーの使用
 **Rethrow**アクティビティ デザイナーは含まれて、 **Error Handling**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**ワークフロー デザイナーの左側にあるタブ (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。

 **Rethrow**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを通常配置しているような内の場所に、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>です。 これを作成、 <xref:System.Activities.Statements.Rethrow> 、既定値を持つアクティビティ**DisplayName** Throw のです。 <xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **Rethrow**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-rethrow-properties"></a>Rethrow のプロパティ
 次の表に、<xref:System.Activities.Statements.Rethrow> のプロパティと、デザイナーでのその使用方法を示します。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> アクティビティの表示名を指定します (省略可能)。 既定値は Rethrow です。|

## <a name="see-also"></a>関連項目

- [コレクション](../workflow-designer/collection-activity-designers.md)
- [Throw](../workflow-designer/throw-activity-designer.md)
- [TryCatch](../workflow-designer/trycatch-activity-designer.md)