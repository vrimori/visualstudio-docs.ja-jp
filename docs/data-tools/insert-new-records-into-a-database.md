---
title: データベースに新しいレコードを挿入する
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: de9da74b8760a15ac55d5339aacacdd89deaef28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966339"
---
# <a name="insert-new-records-into-a-database"></a>データベースに新しいレコードを挿入する

使用することができますをデータベースに新しいレコードを挿入するのには、`TableAdapter.Update`メソッド、または TableAdapter の DBDirect メソッドのいずれか (具体的には、`TableAdapter.Insert`メソッド)。 詳細については、次を参照してください。 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)します。

アプリケーションでは、Tableadapter を使用しない場合は、コマンド オブジェクトを使用することができます (たとえば、 <xref:System.Data.SqlClient.SqlCommand>)、データベースに新しいレコードを挿入します。

アプリケーションでは、データを格納するデータセットを使用する場合は、使用、`TableAdapter.Update`メソッド。 `Update`メソッドは、データベースにすべての変更 (更新、挿入、および削除) を送信します。

アプリケーションがデータを格納または使用して、データベースに新しいレコードの作成をより細かく制御する場合にオブジェクトを使用するかどうか、`TableAdapter.Insert`メソッド。

TableAdapter を持っていない場合、`Insert`メソッド、TableAdapter のいずれかがストアド プロシージャを使用して構成されていることを意味またはその`GenerateDBDirectMethods`プロパティに設定されて`false`します。 TableAdapter を設定してみてください`GenerateDBDirectMethods`プロパティを`true`内から、**データセット デザイナー**、データセットを保存します。 これには、TableAdapter が再生成します。 TableAdapter がまだない場合、`Insert`メソッド、表に、おそらくは示しません個々 の行を区別するための十分なスキーマ情報 (たとえば、ある可能性がありますいないテーブルに主キーのセット)。

## <a name="insert-new-records-by-using-tableadapters"></a>Tableadapter を使用して新しいレコードを挿入します。

Tableadapter では、アプリケーションの要件に応じて、データベースに新しいレコードを挿入するさまざまな方法を提供します。

必要な新しいレコードを追加するアプリケーションでは、データを格納するデータセットを使用する場合だけできます<xref:System.Data.DataTable>データセット、および次の呼び出しで、`TableAdapter.Update`メソッド。 `TableAdapter.Update`ですべての変更を送信するメソッド、 <xref:System.Data.DataTable> (変更および削除されたレコードを含む)、データベースにします。

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterupdate-method"></a>TableAdapter.Update メソッドを使用して、データベースに新しいレコードを挿入するには

1. 新しいレコードの追加に必要な<xref:System.Data.DataTable>新しい<xref:System.Data.DataRow>に追加することと、<xref:System.Data.DataTable.Rows%2A>コレクション。

2. 新しい行を追加した後、<xref:System.Data.DataTable>を呼び出し、`TableAdapter.Update`メソッド。 全体のいずれかで渡すことで更新するデータの量を制御できます<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、配列の<xref:System.Data.DataRow>、または 1 つ<xref:System.Data.DataRow>します。

   次のコードは新しいレコードを追加する方法、<xref:System.Data.DataTable>を呼び出して、`TableAdapter.Update`を新しい行をデータベースに保存するメソッド。 (この例では、 `Region` Northwind データベースのテーブルです)。

   [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
   [!code-csharp[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]

### <a name="to-insert-new-records-into-a-database-by-using-the-tableadapterinsert-method"></a>TableAdapter.Insert メソッドを使用して、データベースに新しいレコードを挿入するには

アプリケーションでは、データを格納するオブジェクトを使用する場合は使用できます、`TableAdapter.Insert`メソッドを直接データベースに新しい行を作成します。 `Insert`メソッドはパラメーターとして各列の値を受け取ります。 メソッドを呼び出すことで渡されたパラメーター値をデータベースに新しいレコードを挿入します。

- 呼び出す TableAdapter の`Insert`メソッド、パラメーターとして各列の値で渡します。

次の手順では、使用方法を示します、`TableAdapter.Insert`行を挿入するメソッド。 この例にデータを挿入、 `Region` Northwind データベースのテーブル。

> [!NOTE]
> 使用可能なインスタンスがいない場合に使用する TableAdapter をインスタンス化します。

[!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
[!code-csharp[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]

## <a name="insert-new-records-by-using-command-objects"></a>コマンド オブジェクトを使用して新しいレコードを挿入します。

コマンド オブジェクトを使用してデータベースに直接新しいレコードを挿入することができます。

### <a name="to-insert-new-records-into-a-database-by-using-command-objects"></a>コマンド オブジェクトを使用して、データベースに新しいレコードを挿入するには

- 新しいコマンド オブジェクトを作成し、設定、 `Connection`、 `CommandType`、および`CommandText`プロパティ。

次の例では、コマンド オブジェクトを使用してデータベースにレコードを挿入することを示します。 データを挿入、 `Region` Northwind データベースのテーブル。

[!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
[!code-csharp[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]

## <a name="net-framework-security"></a>.NET Framework のセキュリティ

データベースに接続しようとするいると、目的のテーブルに挿入を実行するアクセス許可へのアクセスが必要です。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)