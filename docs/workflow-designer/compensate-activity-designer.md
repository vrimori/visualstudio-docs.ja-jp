---
title: ワークフロー デザイナーでは、Compensate アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1bca40a093f228f22919b7734e387a4bc191316c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756371"
---
# <a name="compensate-activity-designer"></a>Compensate アクティビティ デザイナー

**補正**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Compensate>アクティビティ。

## <a name="the-compensate-activity"></a>Compensate アクティビティ

<xref:System.Activities.Statements.Compensate> アクティビティは、<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> に含まれているアクティビティの <xref:System.Activities.Statements.CompensableActivity> を明示的に呼び出します。 <xref:System.Activities.Statements.Compensate> アクティビティが <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> の <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 内、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> 内、および <xref:System.Activities.Statements.CompensableActivity> 内のいずれでも使用されていない場合は、<xref:System.Activities.Statements.Compensate.Target%2A> プロパティを指定する必要があります。

<xref:System.Activities.Statements.CompensationToken> で指定された <xref:System.Activities.Statements.Compensate.Target%2A> は、<xref:System.Activities.Statements.CompensableActivity> の <xref:System.Activities.Statements.CompensableActivity.Body%2A> が正常に完了した後に <xref:System.Activities.Statements.CompensableActivity> を明示的に確認または補正する手段を提供します。

### <a name="using-the-compensate-activity-designer"></a>Compensate アクティビティ デザイナーの使用

**補正**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ、**ツールボックス**します。 開くには**ツールボックス**を選択、**ツールボックス**ワークフロー デザイナーの左側にあるタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

**補正**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**アクティビティを配置して、このような内の場所には、ワークフロー デザイナー画面にドロップし、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップを作成、 <xref:System.Activities.Statements.Compensate> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>補正の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、**補正**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-compensate-properties"></a>Compensate のプロパティ

次の表に、<xref:System.Activities.Statements.CancellationScope> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A>プロパティ グリッドで、またはワークフロー デザイナー画面で、プロパティを編集できます。 編集、<xref:System.Activities.Statements.Compensate.Target%2A>プロパティ グリッド内のプロパティ。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Compensate> アクティビティの表示名を指定します (省略可能)。 既定値は Compensate です。|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|この <xref:System.Activities.InArgument%601> アクティビティの <xref:System.Activities.Statements.CompensationToken> を含む <xref:System.Activities.Statements.Compensate> を指定します。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate アクティビティ デザイナー](../workflow-designer/compensate-activity-designer.md)
- [確認します](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)