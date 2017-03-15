---
title: "方法 : 単一の値を返す SQL ステートメントを作成および実行する | Microsoft Docs"
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
  - "データ コマンド, 返す (スカラー値を)"
  - "データ リーダー"
  - "DataReader オブジェクト"
  - "スカラー値"
  - "SQL ステートメント, データ コマンド"
  - "ストアド プロシージャ, 返す (1 つの値を)"
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : 単一の値を返す SQL ステートメントを作成および実行する
単一の値を返す SQL ステートメントを実行するには、SQL ステートメントを実行するように設定されている TableAdapter クエリ \(`CustomersTableAdapter.CustomerCount()` など\) を実行できます。  
  
 アプリケーションで TableAdapter を使用していない場合は、コマンド オブジェクトの `ExecuteScalar` メソッドを呼び出し、そのメソッドの `CommandType` プロパティを <xref:System.Data.CommandType> に設定します    \("コマンド オブジェクト" は、アプリケーションで使用している [.NET Framework データ プロバイダー](../Topic/.NET%20Framework%20Data%20Providers.md)に固有のコマンドを表します。  たとえば、アプリケーションで .NET Framework SQL Server 用データ プロバイダーを使用している場合、コマンド オブジェクトは <xref:System.Data.SqlClient.SqlCommand> です\)。  
  
 次の例では、TableAdapter またはコマンド オブジェクトのいずれかを使用してデータベースから単一の値を返す SQL ステートメントを実行する方法を示します。  TableAdapter やコマンドを使用してクエリを実行する方法の詳細については、「[データセットへのデータの読み込み](../data-tools/fill-datasets-by-using-tableadapters.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## TableAdapter を使用して単一の値を返す SQL ステートメントの実行  
 この例では [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を使用して TableAdapter クエリを作成する方法を示した後、TableAdapter のインスタンスを宣言してクエリを実行する方法について説明します。  
  
#### TableAdapter を使用して単一の値を返す SQL ステートメントを作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  TableAdapter がない場合は、TableAdapter を作成します。  TableAdapter の作成方法の詳細については、「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。  
  
3.  SQL ステートメントを使用して単一の値を返すクエリが TableAdapter に既にある場合は、これ以降の手順をスキップし、「TableAdapter のインスタンスを宣言してクエリを実行するには」に進んでください。このクエリがない場合は、手順 4 から継続し、単一の値を返す新しいクエリを作成します。  
  
4.  目的の TableAdapter を右クリックし、ショートカット メニューを使用してクエリを追加します。  
  
     **TableAdapter クエリの構成ウィザード**が開きます。  
  
5.  **\[SQL ステートメントを使用する\]** を既定値のまま残し、**\[次へ\]** をクリックします。  
  
6.  **\[単一の値を返す SELECT\]** オプションを選択し、**\[次へ\]** をクリックします。  
  
7.  SQL ステートメントを入力するか、または**クエリ ビルダー**を使用してステートメントを作成し、**\[次へ\]** をクリックします。  
  
8.  クエリの名前を入力します。  
  
9. ウィザードが完了し、TableAdapter にクエリが追加されます。  
  
10. プロジェクトをビルドします。  
  
#### TableAdapter のインスタンスを宣言してクエリを実行するには  
  
1.  実行するクエリが含まれた TableAdapter のインスタンスを宣言します。  
  
    -   デザイン時ツールを使ってインスタンスを作成するには、目的の TableAdapter を**ツールボックス**からドラッグします。   \(プロジェクト内のコンポーネントは、**ツールボックス**内のプロジェクト名と同じ見出しの下に表示されています\)。**ツールボックス**に TableAdapter が表示されない場合は、プロジェクトのビルドが必要になる場合があります。  
  
         または  
  
    -   コードでインスタンスを作成するには、次のコードを <xref:System.Data.DataSet> の名前と TableAdapter の名前に置き換えます。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter は、実際には関連するデータセット クラスの中に存在しません。  各データセットは、対応する TableAdapter のコレクションを独自の名前空間内に保有しています。  たとえば、`SalesDataSet` という名前のデータセットがある場合、その TableAdapter が格納された `SalesDataSetTableAdapters` 名前空間が存在します。  
  
2.  コード内の他のメソッドを呼び出すのと同じようにクエリを呼び出します。  このクエリは、TableAdapter のメソッドです。  次のコードを TableAdapter とクエリの名前に置き換えます。  クエリに必要なパラメーターをすべて渡し、戻り値を処理する必要があります \(変数への割り当てなど\)。  クエリにパラメーターが必要かどうか不明な場合、または必要なパラメーターが不明な場合は、IntelliSense でクエリに必要なシグネチャを確認します。  クエリでパラメーターを使用するかどうかに応じて、コードは次の例のいずれかのようになります。  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  通常は、クエリから返された値を変数に割り当てる必要があります。  単一の値を返す TableAdapter クエリは、\(オブジェクトを返す `ExecuteScalar` メソッドとは異なり\) そのクエリに基づいてデータ型を返します。  たとえば、TableAdapter クエリで、データ型が整数である単一の列を選択すると、このクエリの戻り値は整数になります。  列に null 値を格納できる場合、戻り値は、NULL 許容型 \(`Nullable(Of Integer)` など\) になります。  NULL 許容型の詳細については、「<xref:System.Nullable>」を参照してください。  TableAdapter のインスタンスを宣言して、クエリを実行するコードの完成形は、次のようになります \(この例では、戻り値が整数であることを前提としています。使用するクエリで返されるデータ型に合わせてコードを調整してください\)。  
  
     [!code-cs[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_1.vb)]  
  
## コマンド オブジェクトを使用して単一の値を返す SQL ステートメントの実行  
 次の例では、コマンドを作成し、単一の値を返す SQL ステートメントを実行する方法を示します。  コマンドにパラメーター値を設定および取得する方法については、「[方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)」を参照してください。  
  
 この例では <xref:System.Data.SqlClient.SqlCommand> オブジェクトを使用します。次の要素が必要です。  
  
-   <xref:System>、<xref:System.Data>、および <xref:System.Xml> の各名前空間への参照。  
  
-   `SqlConnection1` という名前のデータ接続。  
  
-   `SqlConnection1` の接続先となるデータ ソースの `Customers` という名前のテーブル   \(これがない場合は、データ ソース用の有効な SQL ステートメントが必要です\)。  
  
#### DataCommand を使用して単一の値を返す SQL ステートメントを実行するには  
  
-   コードを実行するメソッドに次のコードを追加します。  このコマンド \(たとえば、<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>\) の `ExecuteScalar` メソッドを呼び出すと、単一の値が返されます。  データは、<xref:System.Object> に返されます。  
  
     [!code-cs[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value_2.vb)]  
  
## .NET Framework セキュリティ  
 アプリケーションには、データベースにアクセスし、SQL ステートメントを実行するためのアクセス許可が必要です。  
  
## 参照  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)   
 [方法 : TableAdapter クエリを編集する](../data-tools/how-to-edit-tableadapter-queries.md)   
 [方法 : データセットにデータを読み込む](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [データセットへのデータの読み込み](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)