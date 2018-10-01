---
title: '方法: データベース内のレコードの更新 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- records, updating
- data [Visual Studio], saving
- records, editing
- databases, updating
- TableAdapter.Update method
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 73ca33f9fb30a178addab6dee136d3b441bd81d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533874"
---
# <a name="how-to-update-records-in-a-database"></a>方法 : データベースのレコードを更新する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用することができます、`TableAdapter.Update`データベースのレコードを更新 (編集) する方法。 `TableAdapter.Update`メソッドに渡されるパラメーターに応じてさまざまな操作を実行する複数のオーバー ロードを提供します。 これらの異なるメソッド シグネチャの呼び出しの結果を理解しておく必要があります。  
  
> [!NOTE]
>  アプリケーションは、Tableadapter を使用しないかどうかは、コマンド オブジェクトを使用して、データベース内のレコードを更新することができます (たとえば、 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>)。 コマンド オブジェクトでデータを更新する方法の詳細については、以下の「レコードの更新プログラムにコマンド オブジェクトを使用して」を参照してください。  
  
 次の表は、さまざまな動作`TableAdapter.Update`メソッド。  
  
|メソッド|説明|  
|------------|-----------------|  
|`TableAdapter.Update(DataTable)`|すべての変更を保存しようとしています、<xref:System.Data.DataTable>データベースにします。 (これを含む、テーブルに挿入された行を追加および変更されたテーブルの行を更新、テーブルから削除された行を削除します。)|  
|`TableAdapter.Update(DataSet)`|TableAdapter でのすべての変更の保存を試行する TableAdapter の関連パラメーターは、データセットを受け取りが<xref:System.Data.DataTable>データベースにします。 (これを含む、テーブルに挿入された行を追加および変更されたテーブルの行を更新、テーブルから削除された行を削除します。)**注:** TableAdapter に関連付けられた<xref:System.Data.DataTable>は、 <xref:System.Data.DataTable> TableAdapter が最初に構成されたときに作成します。|  
|`TableAdapter.Update(DataRow)`|指定された変更を保存しようとしています。<xref:System.Data.DataRow>データベースにします。|  
|`TableAdapter.Update(DataRows())`|配列の任意の行で変更を保存しようとしています。<xref:System.Data.DataRow>データベースにします。|  
|`TableAdapter.Update("new column values", "original column values")`|元の列の値によって識別される 1 つの行で変更を保存しようとします。|  
  
 通常使用する、`TableAdapter.Update`を受け取るメソッドを<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataRow>(s)、アプリケーション データを格納するだけのデータセットを使用するとします。  
  
 通常、使用、`TableAdapter.Update`をアプリケーションがデータを格納するオブジェクトを使用するときに、列の値を受け取るメソッド。  
  
 TableAdapter があるない場合、`Update`をストアド プロシージャを使用するか、TableAdapter が構成されていることを意味し、列の値を受け取るメソッドまたはその`GenerateDBDirectMethods`プロパティに設定されて`false`します。 TableAdapter を設定してみてください`GenerateDBDirectMethods`プロパティを`true`内から、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)し、TableAdapter を再生成するデータセットを保存します。 TableAdapter は持っていない場合、`Update`でしょうし、列の値、テーブルを受け取るメソッドが個々 の行を区別するための十分なスキーマ情報を提供しない (テーブルに主キーが設定されていないなど)。  
  
## <a name="update-existing-records-using-tableadapters"></a>Tableadapter を使用して既存のレコードを更新します。  
 Tableadapter では、アプリケーションの要件に応じて、データベース内のレコードを更新するさまざまな方法を提供します。  
  
 かどうか、アプリケーションでは、データセットを使用してデータを格納し、目的のレコードを更新して<xref:System.Data.DataTable>を呼び出して、`TableAdapter.Update`メソッドとのいずれかのパス、 <xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、 <xref:System.Data.DataRow>、または配列の<xref:System.Data.DataRow>秒。 上記の表は、異なるについて説明します`Update`メソッド。  
  
#### <a name="to-update-records-in-a-database-with-the-tableadapterupdate-method-that-takes-dataset-datatable-datarow-or-datarows"></a>DataSet、DataTable、DataRow、または DataRows() を受け取る TableAdapter.Update メソッドを使用してデータベース内のレコードを更新するには  
  
1.  目的のレコードを編集<xref:System.Data.DataTable>を直接編集して、<xref:System.Data.DataRow>で、<xref:System.Data.DataTable>します。 詳細については、次を参照してください。[方法: DataTable の行の編集](http://msdn.microsoft.com/library/d5eea200-9bfa-4956-bf7c-08dd6fb6663c)します。  
  
2.  行を編集した後、<xref:System.Data.DataTable>を呼び出し、`TableAdapter.Update`メソッド。 全体のいずれかで渡すことで更新するデータの量を制御できます<xref:System.Data.DataSet>、 <xref:System.Data.DataTable>、配列の<xref:System.Data.DataRow>、または 1 つ<xref:System.Data.DataRow>します。  
  
     次のコード内のレコードを編集する方法を示しています、<xref:System.Data.DataTable>を呼び出して、`TableAdapter.Update`メソッドをデータベースに変更を保存します。 (この例は、Northwind データベースのリージョンのテーブルを使用します)。  
  
     [!code-csharp[VbRaddataSaving#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form5.cs#17)]
     [!code-vb[VbRaddataSaving#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form5.vb#17)]  
  
 アプリケーションは、アプリケーションでデータを格納するオブジェクトを使用する場合は、TableAdapter を使用することができます`DBDirect`オブジェクトからデータをデータベースに直接送信する方法。 これらのメソッドを使用すると、メソッドのパラメーターとして各列の個別の値を渡すことができます。 このメソッドを呼び出すと、メソッドに渡された列の値を持つデータベースの既存のレコードが更新されます。  
  
 次の手順は、Northwind`Region`例としてテーブル。  
  
#### <a name="to-update-records-in-a-database-using-the-tableadapterupdate-method-that-takes-column-values"></a>列の値を受け取る TableAdapter.Update メソッドを使用してデータベースにレコードを更新するには  
  
-   呼び出す TableAdapter の`Update`メソッド、パラメーターとして各列の新しいと、元の値を渡します。  
  
    > [!NOTE]
    >  使用可能なインスタンスがいない場合に使用する TableAdapter をインスタンス化します。  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
## <a name="update-records-using-command-objects"></a>コマンド オブジェクトを使用してレコードを更新します。  
 次の例では、コマンド オブジェクトを使用してデータベースで直接、既存のレコードを更新します。 コマンド オブジェクトを使用して、コマンドやストアド プロシージャを実行する詳細については、次を参照してください。[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)します。  
  
 次の手順は、Northwind`Region`例としてテーブル。  
  
#### <a name="to-update-existing-records-in-a-database-using-command-objects"></a>コマンド オブジェクトを使用してデータベース内の既存のレコードを更新するには  
  
-   新しいコマンド オブジェクトでは; を作成します。設定の`Connection`、 `CommandType`、および`CommandText`; のプロパティとの接続を開くし、コマンドを実行します。  
  
     [!code-csharp[VbRaddataSaving#19](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#19)]
     [!code-vb[VbRaddataSaving#19](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#19)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 データベースに接続しようとするいると、目的のテーブル内のレコードを更新するアクセス許可へのアクセスが必要です。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法: データベース内のレコードの削除](../data-tools/how-to-delete-records-in-a-database.md)   
 [データベースに新しいレコードを挿入します。](../data-tools/insert-new-records-into-a-database.md)   
 [オブジェクトからデータをデータベースに保存します。](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio でのデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)