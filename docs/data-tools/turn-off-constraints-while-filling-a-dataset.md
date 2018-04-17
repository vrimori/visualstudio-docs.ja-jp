---
title: データセットの読み込み中に制約をオフに |Microsoft ドキュメント
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e32aecbe10c9c02fec62240977b3f4e3a3338791
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>データセットの読み込み中に制約をオフにします。
データセットに制約 (外部キー制約) などが含まれている場合、そのデータセットに対して実行される操作を順序に関連するエラーを発行できます。 たとえば、読み込み前に、子レコードの読み込み関連する親レコードの制約に違反してエラーが発生することができます。 子レコードをロードするとすぐに、制約は、関連する親レコード チェックし、エラーが発生します。  
  
 一時的に制約を中断する機構がない場合は、レコードを子テーブルに読み込もうとするたびにエラーが生成されます。 データセットのすべての制約を中断する別の方法として、<xref:System.Data.DataRow.BeginEdit%2A> プロパティおよび <xref:System.Data.DataRow.EndEdit%2A> プロパティを使用できます。  
  
> [!NOTE]
>  入力規則イベント (たとえば、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>) 制約がになっているときに発生しません。  
  
### <a name="to-suspend-update-constraints-programmatically"></a>更新制約をプログラムによって中断するには  
  
-   次の例は、データセットでの制約チェックを一時的に無効にする方法を示しています。  
  
     [!code-csharp[VbRaddataEditing#10](../data-tools/codesnippet/CSharp/turn-off-constraints-while-filling-a-dataset_1.cs)]
     [!code-vb[VbRaddataEditing#10](../data-tools/codesnippet/VisualBasic/turn-off-constraints-while-filling-a-dataset_1.vb)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>データセット デザイナーを使って更新制約を中断するには  
  
1.  データセットを開き、**データセット デザイナー**です。 詳細については、次を参照してください。[チュートリアル: データセット デザイナーでデータセットを作成する](walkthrough-creating-a-dataset-with-the-dataset-designer.md)です。  
  
2.  **プロパティ**ウィンドウで、設定、<xref:System.Data.DataSet.EnforceConstraints%2A>プロパティを`false`です。  
  
## <a name="see-also"></a>関連項目  
 [Tableadapter を使用してデータセットを入力します。](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)