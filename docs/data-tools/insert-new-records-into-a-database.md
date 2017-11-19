---
title: "データベースに新しいレコードを挿入 |Microsoft ドキュメント"
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
- TableAdapters, inserting new records into
- data [Visual Studio], saving
- databases, inserting new records into
- records, inserting
- saving data
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 2450ed950227b6755b57f20f3520a1e75034aafe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="insert-new-records-into-a-database"></a>データベースに新しいレコードを挿入します。
データベースに新しいレコードを挿入するに使用することができます、`TableAdapter.Update`メソッド、または、TableAdapter の DBDirect メソッドのいずれか (具体的には、`TableAdapter.Insert`メソッド)。 詳細については、次を参照してください。 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)です。  
  
 アプリケーションで Tableadapter を使用していない場合は、コマンド オブジェクトを使用できます (たとえば、 <xref:System.Data.SqlClient.SqlCommand>)、データベースに新しいレコードを挿入します。
  
 アプリケーションでは、データを格納するデータセットを使用する場合を使用して、`TableAdapter.Update`メソッドです。 `Update`メソッドは、データベースにすべての変更 (更新、挿入、および削除) を送信します。  
  
 かどうか、アプリケーション オブジェクトを使用してデータを格納または使用して、データベースに新しいレコードの作成をより細かく制御する場合、`TableAdapter.Insert`メソッドです。  
  
 TableAdapter を持っていない場合、`Insert`ストアド プロシージャを使用するか、TableAdapter が構成されていることを意味、メソッド、またはその`GenerateDBDirectMethods`プロパティに設定されている`false`です。 TableAdapter を設定してみてください`GenerateDBDirectMethods`プロパティを`true`内から、**データセット デザイナー**、データセットを保存します。 これには、TableAdapter が再生成します。 TableAdapter がまだない場合、`Insert`メソッド後の表は、おそらく十分なスキーマ情報は提供されません個々 の行を区別するために (たとえば、ある可能性がありますいないテーブルに主キーのセット)。  
  
## <a name="insert-new-records-by-using-tableadapters"></a>Tableadapter を使用して、新しいレコードを挿入します。  
 Tableadapter では、アプリケーションの要件に応じて、データベースに新しいレコードを挿入するさまざまな方法を提供します。  
  
 かどうか、アプリケーションでは、データセットを使用してデータを格納しに必要な新しいレコードを単に追加できる<xref:System.Data.DataTable>、データセットと、呼び出しで、`TableAdapter.Update`メソッドです。 `TableAdapter.Update`ですべての変更を送信するメソッド、 <xref:System.Data.DataTable> (変更および削除されたレコードを含む)、データベースにします。  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter.Update メソッドを使用して、データベースに新しいレコードを挿入するには  
  
1.  新しいレコードに必要な追加<xref:System.Data.DataTable>新しいを作成して<xref:System.Data.DataRow>に追加することと、<xref:System.Data.DataTable.Rows%2A>コレクション。 
  
2.  新しい行が追加した後、<xref:System.Data.DataTable>を呼び出して、`TableAdapter.Update`メソッド。 全体のいずれかに渡すことによって更新するデータの量を制御することができます<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、配列の<xref:System.Data.DataRow>、または単一<xref:System.Data.DataRow>です。  
  
 次のコードは、新しいレコードを追加する方法を示します、<xref:System.Data.DataTable>を呼び出すと、`TableAdapter.Update`を新しい行をデータベースに保存するメソッド。 (この例では、 `Region` Northwind データベース内のテーブルです)。  
  
 [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
 [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
#### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter.Insert メソッドを使用して、データベースに新しいレコードを挿入するには  
使用することができます、アプリケーションは、データを格納するオブジェクトを使用する場合、`TableAdapter.Insert`メソッドを直接データベースに新しい行を作成します。 `Insert`メソッドはパラメーターとして各列の値を受け取ります。 メソッドを呼び出すことで渡されたパラメーター値をデータベースに新しいレコードを挿入します。  
  
- 呼び出す TableAdapter の`Insert`パラメーターとして各列の値で渡す方法です。  

 次の手順では、使用方法を示します、`TableAdapter.Insert`行を挿入するメソッド。 この例にデータを挿入する、 `Region` Northwind データベースのテーブルにします。  
  
 > [!NOTE]
 >  使用可能なインスタンスがあるない場合に使用する TableAdapter をインスタンス化します。  
  
 [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
 [!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## <a name="insert-new-records-by-using-command-objects"></a>コマンド オブジェクトを使用して新しいレコードを挿入します。  
コマンド オブジェクトを使用してデータベースに直接新しいレコードを挿入することができます。    
  
#### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>コマンド オブジェクトを使用して、データベースに新しいレコードを挿入するには  
  
-   新しいコマンド オブジェクトを作成し、設定、 `Connection`、 `CommandType`、および`CommandText`プロパティです。  

 次の例では、コマンド オブジェクトを使用してデータベースにレコードの挿入を示します。 データを挿入、 `Region` Northwind データベースのテーブルにします。
  
 [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
 [!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 データベースに接続しようとするいると、目的のテーブルに挿入を実行する権限へのアクセスが必要です。  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)