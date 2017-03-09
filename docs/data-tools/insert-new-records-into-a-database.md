---
title: "方法 : データベースに新しいレコードを挿入する | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "データ [Visual Studio], 保存"
  - "データベース, 挿入 (新しいレコードを)"
  - "レコード, 挿入"
  - "保存 (データを)"
  - "TableAdapter, 挿入 (新しいレコードを)"
ms.assetid: ea118fff-69b1-4675-b79a-e33374377f04
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : データベースに新しいレコードを挿入する
データベースに新しいレコードを挿入するには、`TableAdapter.Update` メソッドを使用するか、または TableAdapter の DBDirect のメソッドの 1 つ \(つまり `TableAdapter.Insert` メソッド\) を使用します。  詳細については、「[TableAdapter の概要](../data-tools/tableadapter-overview.md)」を参照してください。  
  
 アプリケーションが TableAdapter を使用しない場合は、<xref:System.Data.SqlClient.SqlCommand> などのコマンド オブジェクトを使用してやり取りし、新しいレコードをデータベースに挿入します。  
  
 アプリケーションがデータセットを使用してデータを格納する場合は、`TableAdapter.Update` メソッドを使用します。  `Update` メソッドは、すべての変更内容 \(更新、挿入、および削除\) をデータベースに送ります。  
  
 アプリケーションがオブジェクトを使用してデータを格納する場合、またはデータベースにおけるレコードの新規作成をより細かく制御する場合は、`TableAdapter.Insert` メソッドを使用します。  
  
 TableAdapter に `Insert` メソッドがない場合は、TableAdapter がストアド プロシージャを使用するように構成されているか、または `GenerateDBDirectMethods` プロパティが `false` に設定されています。  [データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)で TableAdapter の `GenerateDBDirectMethods` プロパティを `true` に設定し、データセットを保存して TableAdapter を再作成してみてください。  それでも TableAdapter に `Insert` メソッドがない場合は、テーブルが個々の行を区別するために十分なスキーマ情報を提供していないことが考えられます \(テーブルに主キーが設定されていないなど\)。  
  
## TableAdapter による新規レコードの挿入  
 TableAdapter は、アプリケーションの要件によってデータベースに新規レコードを挿入するための複数の方法を提供します。  
  
 アプリケーションがデータセットを使用してデータを格納する場合は、単にデータセットの目的の <xref:System.Data.DataTable> に新規レコードを追加し、その後に `TableAdapter.Update` メソッドを呼び出すことができます。  `TableAdapter.Update` メソッドは、変更および削除されたレコードを含む <xref:System.Data.DataTable> のすべての変更を受け取ってデータベースに送ります。  
  
#### TableAdapter.Update メソッドを使用してデータベースに新規レコードを挿入するには  
  
1.  <xref:System.Data.DataRow> を新規作成して <xref:System.Data.DataTable.Rows%2A> コレクションに追加することによって、新しいレコードを目的の <xref:System.Data.DataTable> に追加します。  詳細については、「[方法 : DataTable に行を追加する](../Topic/How%20to:%20Add%20Rows%20to%20a%20DataTable.md)」を参照してください。  
  
2.  <xref:System.Data.DataTable> に新しい行を追加した後に、`TableAdapter.Update` メソッドを呼び出します。  更新するデータの量は、<xref:System.Data.DataSet> 全体、単一の <xref:System.Data.DataTable>、<xref:System.Data.DataRow> の配列、または単一の <xref:System.Data.DataRow> を渡すことによって制御できます。  
  
     <xref:System.Data.DataTable> に新規レコードを追加し、`TableAdapter.Update` メソッドを呼び出してデータベースに新しい行を保存するコード例を次に示します。  この例では、Northwind データベースの `Region` テーブルを使用します。  
  
     [!code-vb[VbRaddataSaving#14](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#14](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_1.cs)]  
  
 アプリケーションがオブジェクトを使用してデータを格納する場合、`TableAdapter.Insert` メソッドを使用してデータベースに直接新しい行を作成できます。  `Insert` メソッドは、各列の値をパラメーターとして受け取ります。  このメソッドを呼び出すと、渡されたパラメーター値を使用してデータベースに新規レコードが挿入されます。  
  
 次の手順では、例として Northwind データベースの `Region` テーブルを使用します。  
  
#### TableAdapter.Insert メソッドを使用してデータベースに新規レコードを挿入するには  
  
-   各列の値をパラメーターとして渡して TableAdapter の `Insert` メソッドを呼び出します。  
  
    > [!NOTE]
    >  使用できるインスタンスがない場合は、使用する TableAdapter をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_2.cs)]  
  
## コマンド オブジェクトによる新規レコードの挿入  
 コマンド オブジェクトを使用してデータベースに新規レコードを直接挿入する例を次に示します。  コマンド オブジェクトによるコマンドとストアド プロシージャの実行の詳細については、「[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)」を参照してください。  
  
 次の手順では、例として Northwind データベースの `Region` テーブルを使用します。  
  
#### コマンド オブジェクトを使用してデータベースに新規レコードを挿入するには  
  
-   新しいコマンド オブジェクトを作成し、`Connection`、`CommandType`、および `CommandText` の各プロパティを設定します。  
  
     [!code-vb[VbRaddataSaving#16](../data-tools/codesnippet/VisualBasic/insert-new-records-into-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#16](../data-tools/codesnippet/CSharp/insert-new-records-into-a-database_3.cs)]  
  
## .NET Framework セキュリティ  
 目的のテーブルで挿入を実行する許可および接続するデータベースに対するアクセス許可が必要です。  
  
## 参照  
 [方法 : データベースのレコードを削除する](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [方法 : データベースのレコードを更新する](../data-tools/how-to-update-records-in-a-database.md)   
 [方法 : オブジェクトからデータベースにデータを保存する](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [ID 値および Autonumber 値の取得](../Topic/Retrieving%20Identity%20or%20Autonumber%20Values.md)