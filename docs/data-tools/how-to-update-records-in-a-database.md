---
title: "方法 : データベースのレコードを更新する | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "データベース, 更新"
  - "レコード, 編集"
  - "レコード, 更新"
  - "TableAdapter.Update メソッド"
ms.assetid: cdc8a8e4-a5fa-40dd-9221-97b8571d802a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : データベースのレコードを更新する
データベースのレコードを更新 \(編集\) するには、`TableAdapter.Update` メソッドを使用できます。  `TableAdapter.Update` メソッドは、渡されるパラメーターによって異なる操作を実行するオーバーロードを提供します。  この一連のメソッド署名を呼び出した結果の違いを理解することは重要です。  
  
> [!NOTE]
>  アプリケーションが TableAdapter を使用しない場合は、<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> などのコマンド オブジェクトを使用してデータベースのレコードを更新します。  コマンド オブジェクトによるデータの更新の詳細については、次の「コマンド オブジェクトによるレコードの更新」を参照してください。  
  
 次の表に、各種の `TableAdapter.Update` メソッドの動作を説明します。  
  
|メソッド|Description|  
|----------|-----------------|  
|`TableAdapter.Update(DataTable)`|<xref:System.Data.DataTable> のすべての変更をデータベースに保存します。  これには、テーブルから削除された行の除去、テーブルに挿入された行の追加、テーブルで変更された行の更新が含まれます。|  
|`TableAdapter.Update(DataSet)`|パラメーターはデータセットを受け取りますが、TableAdapter は TableAdapter に関連付けられている <xref:System.Data.DataTable> のすべての変更をデータベースに保存します。  これには、テーブルから削除された行の除去、テーブルに挿入された行の追加、テーブルで変更された行の更新が含まれます。 **Note:**  TableAdapter に関連付けられている <xref:System.Data.DataTable> は、TableAdapter が最初に構成された際に作成された <xref:System.Data.DataTable> です。|  
|`TableAdapter.Update(DataRow)`|指定された <xref:System.Data.DataRow> における変更をデータベースに保存します。|  
|`TableAdapter.Update(DataRows())`|<xref:System.Data.DataRow> の配列のすべての行の変更をデータベースに保存します。|  
|`TableAdapter.Update("new column values", "original column values")`|元の列値によって識別される単一の列の変更を保存します。|  
  
 アプリケーションがデータを格納するためにデータセットを排他的に使用する場合は、一般に <xref:System.Data.DataSet>、<xref:System.Data.DataTable>、または <xref:System.Data.DataRow> を受け取る `TableAdapter.Update` メソッドを使用します。  
  
 アプリケーションがオブジェクトを使用してデータを格納する場合は、一般に列値を受け取る `TableAdapter.Update` メソッドを使用します。  
  
 TableAdapter に列値を受け取る `Update` メソッドがない場合は、TableAdapter がストアド プロシージャを使用するように構成されているか、または `GenerateDBDirectMethods` プロパティが `false` に設定されています。  [データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)で TableAdapter の `GenerateDBDirectMethods` プロパティを `true` に設定し、データセットを保存して TableAdapter を再作成してみてください。  それでも TableAdapter に列値を受け取る `Update` メソッドがない場合は、テーブルが個々の行を区別するために十分なスキーマ情報を提供していないことが考えられます \(テーブルに主キーが設定されていないなど\)。  
  
## TableAdapter による既存のレコードの更新  
 TableAdapter は、アプリケーションの要件によってデータベースのレコードを更新するための複数の方法を提供します。  
  
 アプリケーションがデータセットを使用してデータを格納する場合、目的の <xref:System.Data.DataTable> でレコードを更新し、次に `TableAdapter.Update` メソッドを呼び出して、<xref:System.Data.DataSet>、<xref:System.Data.DataTable>、<xref:System.Data.DataRow>、または <xref:System.Data.DataRow> の配列を渡すだけで済みます。  上の表では、各種の `Update` メソッドを説明しています。  
  
#### DataSet、DataTable、DataRow、または DataRows\(\) を受け取る TableAdapter.Update メソッドを使用してデータベースのレコードを更新するには  
  
1.  <xref:System.Data.DataTable> の <xref:System.Data.DataRow> を直接編集することによって、目的の <xref:System.Data.DataTable> のレコードを編集します。  詳細については、「[方法 : DataTable の行を編集する](../Topic/How%20to:%20Edit%20Rows%20in%20a%20DataTable.md)」を参照してください。  
  
2.  <xref:System.Data.DataTable> の行を編集した後に、`TableAdapter.Update` メソッドを呼び出します。  更新するデータの量は、<xref:System.Data.DataSet> 全体、単一の <xref:System.Data.DataTable>、<xref:System.Data.DataRow> の配列、または単一の <xref:System.Data.DataRow> を渡すことによって制御できます。  
  
     <xref:System.Data.DataTable> のレコードを編集し、`TableAdapter.Update` メソッドを呼び出してデータベースに変更内容を保存するコード例を次に示します。  この例では、Northwind データベースの Region テーブルを使用します。  
  
     [!code-vb[VbRaddataSaving#17](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_1.vb)]
     [!code-cs[VbRaddataSaving#17](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_1.cs)]  
  
 アプリケーションがデータをアプリケーションに格納するためにオブジェクトを使用する場合、TableAdapter の `DBDirect` のメソッドを使用してオブジェクトからデータベースに直接データを送ることができます。  この一連のメソッドでは、各列の個々の値をメソッド パラメーターとして渡すことができます。  このメソッドを呼び出すと、メソッドに渡された列値を使用してデータベースの既存のレコードが更新されます。  
  
 次の手順では、例として Northwind の `Region` テーブルを使用します。  
  
#### 列値を受け取る TableAdapter.Update メソッドを使用してデータベースのレコードを更新するには  
  
-   各列の新しい値と元の値をパラメーターとして渡して TableAdapter の `Update` メソッドを呼び出します。  
  
    > [!NOTE]
    >  使用できるインスタンスがない場合は、使用する TableAdapter をインスタンス化します。  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_2.cs)]  
  
## コマンド オブジェクトによるレコードの更新  
 コマンド オブジェクトを使用してデータベースの既存のレコードを直接更新する例を次に示します。  コマンド オブジェクトによるコマンドとストアド プロシージャの実行の詳細については、「[アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)」を参照してください。  
  
 次の手順では、例として Northwind の `Region` テーブルを使用します。  
  
#### コマンド オブジェクトを使用してデータベースの既存のレコードを更新するには  
  
-   新しいコマンド オブジェクトを作成し、`Connection`、`CommandType`、および `CommandText` の各プロパティを設定し、次に接続を開いてコマンドを実行します。  
  
     [!code-vb[VbRaddataSaving#19](../data-tools/codesnippet/VisualBasic/how-to-update-records-in-a-database_3.vb)]
     [!code-cs[VbRaddataSaving#19](../data-tools/codesnippet/CSharp/how-to-update-records-in-a-database_3.cs)]  
  
## .NET Framework セキュリティ  
 目的のテーブルでレコードを更新する許可および接続するデータベースに対するアクセス許可が必要です。  
  
## 参照  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法 : データベースのレコードを削除する](../Topic/How%20to:%20Delete%20Records%20in%20a%20Database.md)   
 [方法 : データベースに新しいレコードを挿入する](../data-tools/insert-new-records-into-a-database.md)   
 [方法 : オブジェクトからデータベースにデータを保存する](../data-tools/save-data-from-an-object-to-a-database.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)