---
title: "TableAdapter でデータベースに直接アクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: bd8a4c54ba67af567e28e27e5d70d3576645f496
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>TableAdapter でデータベースに直接アクセスします。
加え、 `InsertCommand`、 `UpdateCommand`、および`DeleteCommand`Tableadapter の作成が、データベースに対して直接実行できるメソッドです。 これらのメソッド (`TableAdapter.Insert`、 `TableAdapter.Update`、および`TableAdapter.Delete`)、データベース内で直接データを操作を呼び出すことができます。  
  
 これらの直接メソッドを作成しない場合は、設定、TableAdapter の`GenerateDbDirectMethods`プロパティを`false`で、**プロパティ**ウィンドウです。 すべてのクエリは、TableAdapter のメインのクエリだけでなく、TableAdapter に追加する場合は、これらの DbDirect メソッドを生成しないスタンドアロン クエリになります。  
  
## <a name="send-commands-directly-to-a-database"></a>データベースに直接コマンドを送信します。  
 実行しようとしているタスクを実行する TableAdapter の DbDirect メソッドを呼び出します。  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>データベースに直接新しいレコードを挿入するには  
  
-   呼び出す TableAdapter の`Insert`パラメーターとして各列の値で渡す方法です。 次の手順を使用して、`Region`例として、Northwind データベース内のテーブルです。  
  
    > [!NOTE]
    >  使用可能なインスタンスがあるない場合は、TableAdapter を使用する場合をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>データベースで直接レコードを更新するには  
  
-   呼び出す TableAdapter の`Update`新しいと元の値の各列をパラメーターとして渡す方法です。  
  
    > [!NOTE]
    >  使用可能なインスタンスがあるない場合は、TableAdapter を使用する場合をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-csharp[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>データベースから直接レコードを削除するには  
  
-   呼び出す TableAdapter の`Delete`のパラメーターとして各列の値を渡して、メソッド、`Delete`メソッドです。 次の手順を使用して、`Region`例として、Northwind データベース内のテーブルです。  
  
    > [!NOTE]
    >  使用可能なインスタンスがあるない場合は、TableAdapter を使用する場合をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-csharp[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## <a name="see-also"></a>関連項目  
 [TableAdapters を使用してデータセットを入力する](../data-tools/fill-datasets-by-using-tableadapters.md)