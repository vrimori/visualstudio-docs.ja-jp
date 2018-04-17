---
title: '方法: ワークフロー デザイナーでワークフローにコメントを追加 |Microsoft ドキュメント'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: fb7505d773f26a26df0b31477d99f7f5636d8c40
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>ワークフロー デザイナーでワークフローにコメントを追加する方法

より大きく複雑なワーク フローを簡単に作成するため、[!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] では開発者がデザイナーで次の種類の項目に注釈を追加できます。

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   クラス (派生) <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> 注釈の内容はワーク フローに関連付けられた XAML ファイルにテキスト形式で保存され、他のユーザーに読み取られる可能性があります。 注釈に機密情報を入力する場合は注意してください。

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>デザイナーのアクティビティへの注釈の追加

1. ワークフロー デザイナーと選択内の項目を右クリックし、ワークフロー デザイナーで**注釈**、**注釈の追加**です。

1. 注釈のテキストを提供された領域に追加します。

   アイテムには、注釈アイコンが表示されます。 注釈アイコンの上にマウスには、注釈のテキストが表示されます。

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>アクティビティのデザイナーへの注釈の表示

1.  アクティビティの外部に注釈表示するアクティビティ デザイナー、をクリックして、 **Pin**注釈の装飾のアイコン。

   注釈は、アクティビティのデザイナーに表示されます。 次のスクリーンショットでは、「ワーク フローのアクティビティを開始する」という注釈がアクティビティ デザイナーに表示されています。

   ![注釈がアクティビティ デザイナーに表示されている](../workflow-designer/media/annotationindesigner.png "AnnotationInDesigner")

1. アクティビティ デザイナーの外部に注釈を表示するアクティビティ デザイナーの注釈の領域を合わせるし をクリックして、**ピン解除** アイコン

   ![アクティビティのデザイナーの外部に表示される注釈](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>すべての注釈の表示または非表示

1. 注釈を持つアクティビティを右クリックします。 選択**注釈**、**すべての注釈を表示する**です。

   すべての注釈は、アクティビティのデザイナーに表示されます。

1. クリックし、アクティビティを右クリックし、アクティビティのデザイナーの外部のすべての注釈を表示する**注釈**、**すべての注釈を非表示に**です。

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>アクティビティの注釈の編集または削除

1. 注釈を持つアクティビティを右クリックします。

1. 選択**注釈**、 **注釈の編集**または**注釈を削除**です。

   注釈は編集用に開くか、削除します。

1. すべての注釈を一度に削除するには、ワークフロー デザイナーと選択を右クリックして**注釈**、**注釈をすべて削除**です。

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>変数または引数の注釈の追加、編集、削除

1. 変数または引数を右クリックし、[注釈の追加] をクリックします。

1. 注釈のテキストを入力します。 変数または引数に注釈アイコンが表示されます。

1. 注釈を持つ変数または引数を右クリックします。 [注釈の編集] をクリックします。

   注釈は編集用に開きます。

1. 注釈を持つ変数または引数を右クリックします。 [注釈の削除] をクリックします。

   注釈は削除されます。