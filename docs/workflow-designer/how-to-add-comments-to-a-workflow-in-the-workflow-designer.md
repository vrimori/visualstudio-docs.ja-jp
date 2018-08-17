---
title: 'ワークフロー デザイナー - 方法: ワークフローにコメントを追加'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 0555968f67d804060437df272927aa3ee89c730c
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379950"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>ワークフロー デザイナーでワークフローにコメントを追加する方法

.NET Framework 4.5 では、大規模でより複雑なワークフローを作成するためには、デザイナー内の項目の次の型に注釈を追加する開発者を使用できます。

-   <xref:System.Activities.Activity>

-   <xref:System.Activities.Statements.State>

-   <xref:System.Activities.Statements.Transition>

-   クラス (派生) <xref:System.Activities.Statements.FlowNode>

-   <xref:System.Activities.Variable>

-   <xref:System.Activities.Argument>

> [!IMPORTANT]
> 注釈の内容はワーク フローに関連付けられた XAML ファイルにテキスト形式で保存され、他のユーザーに読み取られる可能性があります。 注釈に機密情報を入力する場合は注意してください。

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>デザイナーのアクティビティへの注釈の追加

1. デザイナーで選択し、ワークフロー内の項目を右クリックし、ワークフロー デザイナーで**注釈**、**注釈の追加**します。

1. 注釈のテキストを提供された領域に追加します。

   アイテムには、注釈アイコンが表示されます。 注釈アイコンにカーソルを合わせると、注釈のテキストが表示されます。

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>アクティビティのデザイナーへの注釈の表示

1.  アクティビティの外部に注釈を表示するアクティビティ デザイナー、をクリックして、 **Pin**注釈の装飾のアイコン。

   注釈は、アクティビティのデザイナーに表示されます。 次のスクリーンショットでは、「ワーク フローのアクティビティを開始する」という注釈がアクティビティ デザイナーに表示されています。

   ![注釈がアクティビティ デザイナーに表示されている](../workflow-designer/media/annotationindesigner.png)

1. アクティビティ デザイナーの外部に注釈を表示するアクティビティのデザイナーでの注釈の領域をポイントし、をクリックして、**ピン解除**アイコン

   ![注釈がアクティビティのデザイナーの外に表示されます。](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>すべての注釈の表示または非表示

1. 注釈を持つアクティビティを右クリックします。 選択**注釈**、**すべての注釈を表示する**します。

   アクティビティのデザイナーには、すべての注釈が表示されます。

1. アクティビティのデザイナーの外部のすべての注釈を表示するには、アクティビティを選択します右クリックして**注釈**、**すべての注釈を非表示に**します。

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>アクティビティの注釈の編集または削除

1. 注釈を持つアクティビティを右クリックします。

1. 選択**注釈**、 **注釈の編集**または**注釈の削除**します。

   注釈が編集用に開くか、削除します。

1. すべての注釈を一度に削除するには、ワークフローのデザイナーと選択を右クリックして**注釈**、**注釈をすべて削除**します。

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>変数または引数の注釈の追加、編集、削除

1. 変数または引数を右クリックし、[注釈の追加] をクリックします。

1. 注釈のテキストを入力します。 変数または引数に注釈アイコンが表示されます。

1. 注釈を持つ変数または引数を右クリックします。 [注釈の編集] をクリックします。

   注釈は編集用に開かれます。

1. 注釈を持つ変数または引数を右クリックします。 [注釈の削除] をクリックします。

   注釈は削除されます。