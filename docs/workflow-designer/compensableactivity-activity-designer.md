---
title: "CompensableActivity アクティビティ デザイナー |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c45a0f2638a3d1fc5b6f4dc536cf051751c9c897
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナー
**CompensableActivity**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.CompensableActivity>アクティビティ。

## <a name="the-compensableactivity-activity"></a>CompensableActivity アクティビティ
 <xref:System.Activities.Statements.CompensableActivity> で、正常に完了した後に確認または補正できる作業単位を定義します。

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナーの使用
 **CompensableActivity**アクティビティ デザイナーは含まれて、**トランザクション**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**  タブの左側にある、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X です)。

 **CompensableActivity**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>です。 この操作により、CompensableActivity という既定の <xref:System.Activities.Statements.CompensableActivity> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **CompensableActivity**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-compensableactivity-properties"></a>CompensableActivity のプロパティ
 次の表に、<xref:System.Activities.Statements.CompensableActivity> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A> プロパティと <xref:System.Activities.Activity%601.Result%2A> プロパティはプロパティ グリッドで編集できますが、それ以外のプロパティは[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]画面で編集する必要があります。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> アクティビティの省略可能な表示名。 既定値は CompensableActivity です。|
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity> の戻り値を指定します。 このプロパティは、プロパティ グリッドで編集する必要があります。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|補正、取り消し、および確認の各ロジックの提供対象のアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CompensableActivity.Body%2A>アクティビティ、アクティビティをドロップ、**ツールボックス**に、**本文**ボックスに、 **CompensableActivity** "ドロップというヒント テキストを含むアクティビティ デザイナーここにアクティビティ"です。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|取り消しの際に実行されるアクティビティを指定します。 アクティビティを追加するからそのデザイナーをドロップ、**ツールボックス**に、 **CancellationHandler**ボックスに、 **CompensableActivity** "ドロップというヒント テキストを含むアクティビティ デザイナーここにアクティビティ"です。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティの補正を行うときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Compensate> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティ デザイナーをドロップ アクティビティを追加するには**ツールボックス**に、 **CompensationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキストが"ここにアクティビティをドロップ"です。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティを確認するときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Confirm> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティ デザイナーをドロップ アクティビティを追加するには**ツールボックス**に、 **ConfirmationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナーのヒント テキストが"ここにアクティビティをドロップ"です。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [補正](../workflow-designer/compensate-activity-designer.md)
- [確認します。](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)