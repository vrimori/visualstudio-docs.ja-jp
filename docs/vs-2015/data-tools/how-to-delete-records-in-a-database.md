---
title: '方法: データベース内のレコードの削除 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], saving
- records, deleting
- TableAdapter.Delete method
- databases, deleting records
- deleting data
- TableAdapter.Update method
- saving data
ms.assetid: d74d2130-9732-4648-abea-241059c4a372
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: aff5a67d54376488ccce2bca5dd67b84d6c73949
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210185"
---
# <a name="how-to-delete-records-in-a-database"></a>方法 : データベースのレコードを削除する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データベースからレコードを削除するには、使用、`TableAdapter.Update`メソッドまたは`TableAdapter.Delete`メソッド。 または、データベースからレコードを削除するコマンド オブジェクトを使用するには、アプリケーションで Tableadapter を使用しない場合 (たとえば、 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>)。  
  
 `TableAdapter.Update`メソッドは通常、アプリケーションは、一方のデータを格納するデータセットを使用するときに使用、`TableAdapter.Delete`メソッドは通常、アプリケーションがデータを格納するオブジェクトを使用するときに使用します。  
  
 TableAdapter があるない場合、`Delete`メソッド、TableAdapter のいずれかがストアド プロシージャを使用して構成されていることを意味またはその`GenerateDBDirectMethods`プロパティに設定されて`false`します。 TableAdapter を設定してみてください`GenerateDBDirectMethods`プロパティを`true`内から、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)し、TableAdapter を再生成するデータセットを保存します。 TableAdapter は持っていない場合、`Delete`個々 の行を区別するために十分なスキーマはおそらくは行いませんメソッドでは、次の表に、(テーブルに主キーが設定されていないなど)。  
  
## <a name="delete-records-using-tableadapters"></a>Tableadapter を使用してレコードを削除します。  
 Tableadapter では、アプリケーションの要件に応じて、データベースからレコードを削除するさまざまな方法を提供します。  
  
 だけですから、必要なレコードを削除することができます、アプリケーション データを格納するデータセットを使用している場合<xref:System.Data.DataTable>で、<xref:System.Data.DataSet>を呼び出して、`TableAdapter.Update`メソッド。 `TableAdapter.Update`メソッドがデータ テーブルのすべての変更を取得し、(挿入、更新、および削除されたレコードを含む)、データベースにそれらの変更を送信します。  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterupdate-method"></a>TableAdapter.Update メソッドを使用してデータベースからレコードを削除するには  
  
-   必要なレコードを削除<xref:System.Data.DataTable>を削除して<xref:System.Data.DataRow>テーブルからのオブジェクト。 詳細については、次を参照してください。[方法: DataTable の行の削除](http://msdn.microsoft.com/library/add481e5-08c7-4923-9276-f036ae29d31e)します。 行を削除した後、<xref:System.Data.DataTable>を呼び出し、`TableAdapter.Update`メソッド。 全体を渡すことで更新するデータの量を制御できます<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、配列の<xref:System.Data.DataRow>、または 1 つ<xref:System.Data.DataRow>します。 次のコードからレコードを削除する方法を示します、<xref:System.Data.DataTable>を呼び出して、`TableAdapter.Update`メソッドは通信の変更をデータベースから行を削除します。 (この例の Northwind データベースの`Region`テーブルです)。  
  
     [!code-csharp[VbRaddataSaving#20](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#20)]
     [!code-vb[VbRaddataSaving#20](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#20)]  
  
 アプリケーションは、アプリケーションでデータを格納するオブジェクトを使用する場合は、データベースから直接データを削除する TableAdapter の DBDirect メソッドを使用できます。 呼び出す、`Delete`メソッドに渡されたパラメーター値に基づいて、データベースからレコードを削除します。  
  
#### <a name="to-delete-records-from-a-database-using-the-tableadapterdelete-method"></a>TableAdapter.Delete メソッドを使用してデータベースからレコードを削除するには  
  
-   呼び出す TableAdapter の`Delete`メソッドのパラメーターとして各列の値を渡す、`Delete`メソッド。 (この例の Northwind データベースの`Region`テーブルです)。  
  
    > [!NOTE]
    >  使用可能なインスタンスがいない場合に使用する TableAdapter をインスタンス化します。  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="delete-records-using-command-objects"></a>コマンド オブジェクトを使用してレコードを削除します。  
 次の例では、コマンド オブジェクトを使用してデータベースから直接レコードを削除します。 コマンド オブジェクトを使用して、コマンドやストアド プロシージャを実行する詳細については、次を参照してください。[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)します。  
  
#### <a name="to-delete-records-from-a-database-using-command-objects"></a>コマンド オブジェクトを使用してデータベースからレコードを削除するには  
  
-   新しいコマンド オブジェクトを作成、設定、 `Connection`、 `CommandType`、および`CommandText`プロパティ。 (この例の Northwind データベースの`Region`テーブルです)。  
  
     [!code-csharp[VbRaddataSaving#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#22)]
     [!code-vb[VbRaddataSaving#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#22)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 データベースに接続しようとするいると、目的のテーブルからレコードを削除するアクセス許可へのアクセスが必要です。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [データベースに新しいレコードを挿入します。](../data-tools/insert-new-records-into-a-database.md)   
 [方法: データベース内のレコードを更新](../data-tools/how-to-update-records-in-a-database.md)   
 [オブジェクトからデータをデータベースに保存します。](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)