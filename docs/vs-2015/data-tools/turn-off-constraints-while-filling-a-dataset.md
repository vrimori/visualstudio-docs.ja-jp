---
title: データセットの読み込み中に制約を無効にする |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.BeginEdit
- DataRow.EndEdit
- DataRow.CancelEdit
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- updating datasets, constraints
- constraints [Visual Basic], datasets
- datasets [Visual Basic], constraints
- constraints [Visual Basic], suspending during dataset update
ms.assetid: 553f7d0c-2faa-4c17-b226-dd02855bf1dc
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4b14830b7ed4922b4e383ef245c0366c184b606e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537646"
---
# <a name="turn-off-constraints-while-filling-a-dataset"></a>データセットの読み込み中に制約をオフにする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[データセットの読み込み中に制約を無効に](https://docs.microsoft.com/visualstudio/data-tools/turn-off-constraints-while-filling-a-dataset)します。  
  
  
データセットに制約 (外部キー制約) などが含まれている場合、theycan は、データセットに対して実行される操作の順序に関連するエラーを発生します。 たとえば、loadingrelated 親レコードの前に子レコードを読み込むことができます制約に違反する、エラーが発生します。 子レコードを読み込むとすぐに制約は、関連する親レコードをチェックし、エラーを発生させます。  
  
 一時的に制約を中断する機構がない場合は、レコードを子テーブルに読み込もうとするたびにエラーが生成されます。 データセットのすべての制約を中断する別の方法として、<xref:System.Data.DataRow.BeginEdit%2A> プロパティおよび <xref:System.Data.DataRow.EndEdit%2A> プロパティを使用できます。  
  
> [!NOTE]
>  検証イベント (たとえば、<xref:System.Data.DataTable.ColumnChanging>と<xref:System.Data.DataTable.RowChanging>) 制約がになっているときに発生しません。  
  
### <a name="to-suspend-update-constraints-programmatically"></a>更新制約をプログラムによって中断するには  
  
-   次の例は、データセットでの制約チェックを一時的に無効にする方法を示しています。  
  
     [!code-csharp[VbRaddataEditing#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#10)]
     [!code-vb[VbRaddataEditing#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#10)]  
  
### <a name="to-suspend-update-constraints-using-the-dataset-designer"></a>データセット デザイナーを使って更新制約を中断するには  
  
1.  データセットを開き、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  **プロパティ**ウィンドウで、設定、<xref:System.Data.DataSet.EnforceConstraints%2A>プロパティを`false`します。  
  
## <a name="see-also"></a>関連項目  
 [Tableadapter を使用してデータセットを入力します。](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [データセットのリレーションシップ](../data-tools/relationships-in-datasets.md)

