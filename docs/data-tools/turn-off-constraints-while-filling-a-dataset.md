---
title: データセットの読み込み中に制約をオフにする
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: aaf566c211cd79657b67a5af72d53c718cd2507a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951460"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>データセットの読み込み中に制約をオフにする

データセットに制約 (外部キー制約) などが含まれている場合、データセットに対して実行される操作の順序に関連するエラーを発行できます。 親レコードの制約に違反してエラーが発生することができますが、関連読み込み前に子レコードの読み込み。 子レコードを読み込んだ直後に、関連する親があるかどうかが制約でチェックされ、エラーが生成されます。

一時的に制約を中断する機構がない場合は、レコードを子テーブルに読み込もうとするたびにエラーが生成されます。 データセットのすべての制約を中断する別の方法として、<xref:System.Data.DataRow.BeginEdit%2A> プロパティおよび <xref:System.Data.DataRow.EndEdit%2A> プロパティを使用できます。

> [!NOTE]
> 検証イベント (たとえば、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>) 制約がになっているときに発生しません。

## <a name="to-suspend-update-constraints-programmatically"></a>更新制約をプログラムによって中断するには

-   次の例は、データセットでの制約チェックを一時的に無効にする方法を示しています。

     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]

## <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>データセット デザイナーを使って更新制約を中断するには

1.  **データセット デザイナー**でご自分のデータセットを開きます。 詳細については、「[チュートリアル:データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)します。

2.  **[プロパティ]** ウィンドウで、 <xref:System.Data.DataSet.EnforceConstraints%2A> プロパティを `false`に設定します。

## <a name="see-also"></a>関連項目

- [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)
- [データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)