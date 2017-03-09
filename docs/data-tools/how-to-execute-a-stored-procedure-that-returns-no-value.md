---
title: "方法 : 値を返さないストアド プロシージャを実行する | Microsoft Docs"
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
  - "ExecuteNonQuery メソッド"
  - "ストアド プロシージャ, 作成"
  - "ストアド プロシージャ, 実行"
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : 値を返さないストアド プロシージャを実行する
値を返さないストアド プロシージャを実行するには、ストアド プロシージャを実行するように構成した TableAdapter クエリを実行します \(たとえば、`CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\)。  
  
 アプリケーションで TableAdapter を使用していない場合は、コマンド オブジェクトの `ExecuteNonQuery` メソッドを呼び出し、そのメソッドの `CommandType` プロパティを <xref:System.Data.CommandType> に設定します    \("コマンド オブジェクト" は、アプリケーションで使用している [.NET Framework データ プロバイダー](../Topic/.NET%20Framework%20Data%20Providers.md)に固有のコマンドを表します。  たとえば、アプリケーションで .NET Framework SQL Server 用データ プロバイダーを使用している場合、コマンド オブジェクトは <xref:System.Data.SqlClient.SqlCommand> です\)。  
  
 次の例では、TableAdapter またはコマンド オブジェクトを使用して、データベースから値を返さないストアド プロシージャを実行する方法を示します。  TableAdapter やコマンドを使用してクエリを実行する方法の詳細については、「[データセットへのデータの読み込み](../data-tools/fill-datasets-by-using-tableadapters.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## TableAdapter を使用した値を返さないストアド プロシージャの実行  
 この例では [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を使用して TableAdapter クエリを作成する方法を示した後、TableAdapter のインスタンスを宣言してクエリを実行する方法について説明します。  
  
#### TableAdapter を使用して値を返さないストアド プロシージャを作成するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  TableAdapter がない場合は、TableAdapter を作成します。  TableAdapter の作成方法の詳細については、「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。  
  
3.  ストアド プロシージャを使用する値を返さないクエリが TableAdapter に既にある場合は、これ以降の手順をスキップし、「TableAdapter のインスタンスを宣言してクエリを実行するには」に進んでください。このクエリがない場合は、手順 4 から継続し、値を返さない新しいクエリを作成します。  
  
4.  目的の TableAdapter を右クリックし、ショートカット メニューを使用してクエリを追加します。  
  
     **TableAdapter クエリの構成ウィザード**が開きます。  
  
5.  **\[既存のストアド プロシージャを使用\]** を選択し、**\[次へ\]** をクリックします。  
  
6.  ドロップダウン リストからストアド プロシージャを選択し、**\[次へ\]** をクリックします。  
  
7.  **\[値なし\]** を返すオプションを選択し、**\[次へ\]** をクリックします。  
  
8.  クエリの名前を入力します。  
  
9. **\[次へ\]** または **\[完了\]** をクリックしてウィザードを完了します。クエリが TableAdapter に追加されます。  
  
10. プロジェクトをビルドします。  
  
#### TableAdapter のインスタンスを宣言してクエリを実行するには  
  
1.  実行するクエリが含まれた TableAdapter のインスタンスを宣言します。  
  
    -   デザイン時ツールを使ってインスタンスを作成するには、目的の TableAdapter を**ツールボックス**からドラッグします。   \(プロジェクト内のコンポーネントは、**ツールボックス**内のプロジェクト名と同じ見出しの下に表示されています\)。**ツールボックス**に TableAdapter が表示されない場合は、プロジェクトのビルドが必要になる場合があります。  
  
         または  
  
    -   コードでインスタンスを作成するには、次のコードを <xref:System.Data.DataSet> の名前と TableAdapter の名前に置き換えます。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapter は、実際には関連するデータセット クラスの中に存在しません。  各データセットは、対応する TableAdapter のコレクションを独自の名前空間内に保有しています。  たとえば、`SalesDataSet` という名前のデータセットがある場合、その TableAdapter が格納された `SalesDataSetTableAdapters` 名前空間が存在します。  
  
2.  コード内の他のメソッドを呼び出すのと同じようにクエリを呼び出します。  このクエリは、TableAdapter のメソッドです。  次のコードを TableAdapter とクエリの名前に置き換えます。  クエリに必要なすべてのパラメーターも渡す必要があります。  クエリにパラメーターが必要かどうか不明な場合、または必要なパラメーターが不明な場合は、IntelliSense でクエリに必要なシグネチャを確認します。  クエリでパラメーターを使用するかどうかに応じて、コードは次の例のいずれかのようになります。  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     TableAdapter のインスタンスを宣言してクエリを実行する完全なコードは、次のようになります。  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_1.vb)]  
  
## コマンド オブジェクトを使用した値を返さないストアド プロシージャの実行  
 次の例では、コマンドを作成し、値を返さないストアド プロシージャを実行する方法を示します。  コマンドにパラメーター値を設定および取得する方法については、「[方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)」を参照してください。  
  
 この例では <xref:System.Data.SqlClient.SqlCommand> オブジェクトを使用します。次の要素が必要です。  
  
-   <xref:System>、<xref:System.Data>、および <xref:System.Xml> の各名前空間への参照。  
  
#### DataCommand を使用して値を返さないストアド プロシージャを実行するには  
  
-   ストアド プロシージャを実行するメソッドに次のコードを追加します。  値を返さないコマンドの `ExecuteNonQuery` メソッドを呼び出します \(たとえば、<xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>\)。  
  
     [!code-cs[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/CSharp/how-to-execute-a-stored-procedure-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../data-tools/codesnippet/VisualBasic/how-to-execute-a-stored-procedure-that-returns-no-value_2.vb)]  
  
## .NET Framework セキュリティ  
 アプリケーションには、データベースにアクセスし、SQL ステートメントを実行するためのアクセス許可が必要です。  
  
## 参照  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)   
 [方法 : TableAdapter クエリを編集する](../data-tools/how-to-edit-tableadapter-queries.md)   
 [方法 : データセットにデータを読み込む](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [データセットへのデータの読み込み](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)