---
title: "データセットへのデータの読み込み | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "データ [Visual Studio], データセット"
  - "データ [Visual Studio], 取得"
  - "データの取得"
  - "データセット [Visual Basic]"
  - "データセット [Visual Basic], 塗りつぶし"
  - "データセット [Visual Basic], 読み込み (データを)"
  - "取得 (データを)"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# データセットへのデータの読み込み
Transact\-SQL クエリの実行とデータセットの読み込みに使用する標準の Visual Studio 機構は、TableAdapter です。  
  
 TableAdapter またはコマンド オブジェクト \(<xref:System.Data.SqlClient.SqlCommand> など\) を使用すると、データ ソースに対して SQL ステートメントまたはストアド プロシージャを実行できます。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のデザイン ツールを使用して作成したデータセットにデータを読み込むには、TableAdapter を使用します。  プログラムで作成したデータセットにデータを読み込むには、データ アダプターを使用します。  アプリケーションでデータセットを使用しない場合は、コマンド オブジェクトを使用して、データベースに対して SQL ステートメントまたはストアド プロシージャを直接実行します。  
  
 次のトピックでは、Visual Studio でデータセットにデータを読み込む方法について詳細に説明します。  
  
|トピック|Description|  
|----------|-----------------|  
|[方法 : データセットにデータを読み込む](../data-tools/how-to-fill-a-dataset-with-data.md)|TableAdapter および DataAdapter を使用して、データセットにデータを読み込む方法を説明します。|  
|[方法 : 行を返す SQL ステートメントを作成および実行する](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)|TableAdapter のクエリおよび Command オブジェクトを使用して行を返す SQL ステートメントを作成および実行する方法を説明します。|  
|[方法 : 単一の値を返す SQL ステートメントを作成および実行する](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)|TableAdapter のクエリおよび Command オブジェクトを使用して単一の値を返す SQL ステートメントを作成および実行する方法を説明します。|  
|[方法 : 値を返さない SQL ステートメントを作成および実行する](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)|TableAdapter のクエリおよび Command オブジェクトを使用して値を返さない SQL ステートメントを作成および実行する方法を示します。|  
|[方法 : 行を返すストアド プロシージャを実行する](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)|TableAdapter のクエリおよび Command オブジェクトを使用して行を返すストアド プロシージャを実行する方法を説明します。|  
|[方法 : 単一の値を返すストアド プロシージャを実行する](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)|TableAdapter のクエリおよび Command オブジェクトを使用して単一の値を返すストアド プロシージャを実行する方法を説明します。|  
|[方法 : 値を返さないストアド プロシージャを実行する](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)|TableAdapter のクエリおよび Command オブジェクトを使用して値を返さないストアド プロシージャを実行する方法を説明します。|  
|[方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)|クエリおよびストアド プロシージャのパラメーターに値を割り当て、実行されたコマンドから返されたパラメーターの値を読み込む方法を説明します。|  
|[チュートリアル : データセットへのデータの読み込み](../Topic/Walkthrough:%20Filling%20a%20Dataset%20with%20Data.md)|データセットを作成し、そこにデータベースのデータを読み込む方法を説明します。|  
|[チュートリアル : データセットへの XML データの読み込み](../data-tools/read-xml-data-into-a-dataset.md)|XML データをデータセットに読み込んで、<xref:System.Windows.Forms.DataGridView> コントロール内にそのデータセットを表示する Windows アプリケーションの作成方法について説明します。|  
  
## データセットへのデータの読み込み  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] デザイン時ツール \([データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)や[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)など\) を使ってデータセットを作成した場合、TableAdapter を使ってデータセットにデータを読み込みます。  TableAdapter は、SQL ステートメントまたはストアド プロシージャを実行します。  
  
 デザイン時ツールを使わずにデータセットを作成した場合は、データの読み込みや更新にデータ アダプターを使用する必要があります。  TableAdapter は、[.NET Framework 4.6 および 4.5](../Topic/.NET%20Framework%204.6%20and%204.5.md) の実際のクラスではないため、デザイン時ツールを使わずに作成したデータセットを操作する手段としては不適切です。  TableAdapter またはデータ アダプターを使用したデータセットへのデータの読み込みの詳細については、「[方法 : データセットにデータを読み込む](../data-tools/how-to-fill-a-dataset-with-data.md)」を参照してください。  
  
## TableAdapter クエリ  
 TableAdapter クエリを実行してデータセットにデータを読み込むことができます \(より具体的には、データセットを構成する DataTable にデータを読み込みます\)。  TableAdapter クエリを作成するには、**データセット デザイナー**の [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を使用します。  TableAdapter クエリは指定されたメソッドとして TableAdapter に表示され、TableAdapter のメソッドを呼び出して実行します。  TableAdapter クエリの作成と実行の詳細については、次のトピックを参照してください。  
  
-   [方法 : 行を返す SQL ステートメントを作成および実行する](../Topic/How%20to:%20Create%20and%20Execute%20an%20SQL%20Statement%20that%20Returns%20Rows.md)  
  
-   [方法 : 単一の値を返す SQL ステートメントを作成および実行する](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-a-single-value.md)  
  
-   [方法 : 値を返さない SQL ステートメントを作成および実行する](../data-tools/how-to-create-and-execute-an-sql-statement-that-returns-no-value.md)  
  
-   [方法 : 行を返すストアド プロシージャを実行する](../Topic/How%20to:%20Execute%20a%20Stored%20Procedure%20that%20Returns%20Rows.md)  
  
-   [方法 : 単一の値を返すストアド プロシージャを実行する](../data-tools/how-to-execute-a-stored-procedure-that-returns-a-single-value.md)  
  
-   [方法 : 値を返さないストアド プロシージャを実行する](../data-tools/how-to-execute-a-stored-procedure-that-returns-no-value.md)  
  
## コマンド オブジェクト  
 コマンド オブジェクトを使用すると、<xref:System.Data.DataSet>、TableAdapter、または <xref:System.Data.Common.DataAdapter> を使用しなくても、データベースに対して SQL ステートメントとストアド プロシージャを直接実行できます  \(*コマンド オブジェクト*という用語は、アプリケーションで使用している .NET Framework データ プロバイダーに固有のコマンドを表します。  たとえば、アプリケーションで .NET Framework SQL Server 用データ プロバイダーを使用している場合、コマンド オブジェクトは <xref:System.Data.SqlClient.SqlCommand> です\)。  
  
 データ コマンドの `CommandType` プロパティを <xref:System.Data.IDbCommand.CommandType%2A> 列挙体のいずれかの値に設定することにより、SQL ステートメントまたはストアド プロシージャを使用してデータへのクエリを実行するコマンドを構成します。  SQL ステートメントを実行するには `CommandType` を <xref:System.Data.CommandType> に設定し、ストアド プロシージャを実行する場合は <xref:System.Data.CommandType> に設定します。  次に、`CommandText` プロパティに SQL ステートメントを設定するか、またはストアド プロシージャの名前を設定します。  続いて、実行メソッド \(`ExecuteReader`、`ExecuteScalar`、`ExecuteNonQuery`\) の 1 つを呼び出してデータ コマンドを実行できます。  
  
 それぞれの [.NET Framework データ プロバイダー](../Topic/.NET%20Framework%20Data%20Providers.md) に、特定のデータベース用に最適化されたコマンド オブジェクトが用意されています。  
  
 データ コマンドを使用することにより、アプリケーションで次の操作ができます。  
  
-   結果をデータセットに読み込まずに、結果を直接読み込むことのできる選択コマンドを実行できます。  結果を読み込むには、データ リーダー \(<xref:System.Data.OleDb.OleDbDataReader>、<xref:System.Data.SqlClient.SqlDataReader>、<xref:System.Data.Odbc.OdbcDataReader>、または <xref:System.Data.OracleClient.OracleDataReader> の各オブジェクト\) を使用します。このリーダーは、コントロールをバインドできる読み取り専用の前方向カーソルのように機能します。  この方法を使用すると、メモリの使用量を軽減し、読み取り専用データを迅速に読み込むことができます。  
  
-   データ定義言語 \(DDL: Database Definition Language\) コマンドを実行して、テーブルやストアド プロシージャなどのデータベース ストラクチャを作成、編集、および削除できます。  これらの操作を行うには、適切なアクセス許可が必要です。  
  
-   データベース カタログ情報を取得するコマンドを実行できます。  
  
-   データセット テーブルを更新して変更をデータベースにコピーする代わりに、動的な SQL コマンドを実行してレコードを更新、挿入、または削除できます。  
  
-   集約関数 \(SUM、COUNT、AVG など\) の結果のようなスカラー値 \(つまり、単一の値\) を返すコマンドを実行できます。  
  
-   SQL Server データベース \(バージョン 7.0 以降\) のデータを XML 形式で返すコマンドを実行できます。  一般的な使用法としては、クエリを実行してデータを XML 形式で取得し、XSLT 変換を適用してデータを HTML に変換してから、結果をブラウザーに送信します。  
  
 コマンドのプロパティには、データベースに対してコマンドを実行するために必要なすべての情報が含まれています。  具体的には、次の情報が含まれています。  
  
-   **接続** コマンドは、データベースとやり取りするために使用する接続を参照します。  
  
-   **コマンドの名前またはテキスト** コマンドには、SQL ステートメントの実際のテキスト、または実行するストアド プロシージャの名前が含まれています。  
  
-   **パラメーター** コマンドによっては、パラメーターに値を渡す必要があります \(入力パラメーター\)。  また、コマンドは、戻り値または出力パラメーター値の形で値を返す場合があります。  各コマンドにはパラメーターのコレクションがあり、個別に設定して値を渡したり、読み取って値を取得したりできます。  詳細については、「[方法 : コマンド オブジェクトのパラメーターを設定および取得する](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)」を参照してください。  
  
 取得する結果に適したメソッドを使用してコマンドを実行する必要があります。  たとえば、行を取得する場合は、コマンドの `ExecuteReader` メソッドを呼び出して、データ リーダーにレコードが返されるようにします。  UPDATE、INSERT、または DELETE の各コマンドを実行する場合は、コマンドの `ExecuteNonQuery` メソッドを呼び出して、対象となった行数を示す値が返るようにします。  顧客の注文の件数を返すような集約関数を実行する場合は、`ExecuteScalar` メソッドを呼び出します。  
  
### 複数結果セット  
 通常、コマンド オブジェクトは、データの単一のテーブル \(行セット\) を返すために使用されます。  しかし、コマンドは、複数の結果セットを返すプロシージャも実行できます。  これはいくつかの異なる方法で行われます。  1 つは、コマンドが、複数の結果セットを返すストアド プロシージャを参照する場合です。  または、コマンドが 2 つ以上のステートメントやストアド プロシージャ名を含む場合もあります。  その場合は、1 つの呼び出しでステートメントまたはプロシージャが順番に実行され、複数の結果セットが返されます。  
  
 コマンドに対して複数のステートメントまたはプロシージャを指定する場合、すべて同じ種類である必要があります。  たとえば、連続した SQL ステートメントや連続したストアド プロシージャは実行できますが、  ストアド プロシージャ呼び出しと SQL ステートメントを同じコマンドで実行することはできません。  詳細については、「[DataReader によるデータの取得](../Topic/Retrieving%20Data%20Using%20a%20DataReader.md)」を参照してください。  
  
> [!NOTE]
>  Oracle の場合、.NET Framework Oracle 用データ プロバイダーはバッチにまとめられた SQL ステートメントをサポートしていません。  ただし、複数の REF CURSOR 出力パラメーターをそれぞれ別個のデータ テーブルで使用してデータセットにデータを格納できます。  パラメーターを定義して出力パラメーターとしてマークし、REF CURSOR データ型であることを示す必要があります。  <xref:System.Data.OracleClient.OracleDataAdapter> オブジェクトのデータが REF CURSOR パラメーターからストアド プロシージャに格納される場合は、`Update` メソッドを使用できません。これは、SQL ステートメントが実行されるときに、テーブル名と列名を決定するために必要な情報が Oracle から提供されないためです。  
  
## セキュリティ  
 `CommandType` プロパティを <xref:System.Data.CommandType> に設定したデータ コマンドを使用するときは、クライアントから送信された情報をデータベースに渡す前に、その情報を十分にチェックしてください。  悪意のあるユーザーが、承認なしでデータベースにアクセスしたり、データベースを破壊したりする目的で、変更した SQL ステートメントや追加の SQL ステートメントの送信 \(挿入\) を試みる場合があります。  ユーザーの入力をデータベースに転送する前に、その情報が有効であることを常に検証する必要があります。  できる限り、常にパラメーター化されたクエリまたはストアド プロシージャを使用することをお勧めします。  
  
## 参照  
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [Visual Studio でデータ ソースを操作するためのツール](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)