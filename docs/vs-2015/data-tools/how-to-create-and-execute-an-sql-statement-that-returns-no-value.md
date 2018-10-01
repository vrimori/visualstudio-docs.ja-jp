---
title: '方法: を作成し、値を返さない SQL ステートメントの実行 |Microsoft Docs'
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2dd78fe0144718337fc589e0d8f8948d5353dd6c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539043"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>方法 : 値を返さない SQL ステートメントを作成および実行する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

値を返さない SQL ステートメントを実行するには、SQL ステートメントを実行するように構成された TableAdapter クエリを実行することができます (たとえば、 `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`)。  
  
 アプリケーションで Tableadapter を使用しない場合は、呼び出し、`ExecuteNonQuery`設定、コマンド オブジェクトのメソッドをその`CommandType`プロパティを<xref:System.Data.CommandType>します。 (「コマンド オブジェクト」の特定のコマンドを参照、 [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)アプリケーションで使用します。 たとえば、アプリケーションは、SQL Server の .NET Framework Data Provider を使用されている場合、コマンド オブジェクトになります<xref:System.Data.SqlClient.SqlCommand>)。  
  
 次の例では、またはオブジェクトをコマンドに Tableadapter を使用してデータベースから値が返されない SQL ステートメントを実行する方法を示します。 Tableadapter とコマンドを使用したクエリの詳細については、次を参照してください。 [Tableadapter を使用してデータセットを入力](../data-tools/fill-datasets-by-using-tableadapters.md)します。  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>TableAdapter を使用して値を返さない SQL ステートメントの実行  
 この例を使用して TableAdapter クエリを作成する方法を示しています、 [TableAdapters の編集](../data-tools/editing-tableadapters.md)、TableAdapter のインスタンスを宣言し、クエリを実行する方法の情報を示します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>TableAdapter を使用して値を返さない SQL ステートメントを作成するには  
  
1.  データセットを開き、**データセット デザイナー**します。 詳細については、次を参照してください。[方法: データセット デザイナーでデータセットを開く](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3)します。  
  
2.  いない 1 つ場合、は、TableAdapter を作成します。 Tableadapter を作成する方法の詳細については、次を参照してください。[作成し、Tableadapter 構成](../data-tools/create-and-configure-tableadapters.md)します。  
  
3.  値を返さない SQL ステートメントを使用して、TableAdapter にクエリを既にがある場合、"を TableAdapter のインスタンスを宣言し、クエリを実行します"で、次の手順に進みます それ以外の場合、新しい値を返さないクエリを作成する 4 の手順に進みます。  
  
4.  ように、TableAdapter を右クリックし、ショートカット メニューを使用してクエリを追加します。  
  
     **TableAdapter クエリ構成ウィザード**が開きます。  
  
5.  既定値をそのまま**SQL ステートメントを使用**、 をクリックし、**次**。  
  
6.  選択、**更新**、**挿入**または**削除**オプションをクリックして**次**。  
  
7.  SQL ステートメントを入力するか、使用、**クエリ ビルダー**をクリックして、1 つの作成を支援**次**。  
  
8.  クエリの名前を指定します。  
  
9. ウィザードを完了します。クエリは、TableAdapter に追加されます。  
  
10. プロジェクトをビルドします。  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>TableAdapter のインスタンスを宣言し、クエリを実行するには  
  
1.  実行するクエリを含む、TableAdapter のインスタンスを宣言します。  
  
    -   デザイン時ツールを使用してインスタンスを作成するから使用する TableAdapter をドラッグ、**ツールボックス**します。 (プロジェクト内のコンポーネントで表示、**ツールボックス**プロジェクトの名前に一致する見出しの下)。TableAdapter に表示されない場合、**ツールボックス**、プロジェクトをビルドする必要があります。  
  
         - または -  
  
    -   コードでインスタンスを作成するには、名前を持つ次のコードを置き換える、<xref:System.Data.DataSet>および TableAdapter。  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Tableadapter は、関連付けられているデータセット クラス内で実際に置かれていません。 各データセットには、Tableadapter の独自の名前空間に対応するコレクションがあります。 たとえば、という名前のデータセットがある場合`SalesDataSet`があります、 `SalesDataSetTableAdapters` Tableadapter を含む名前空間。  
  
2.  コードでは、他のメソッドを呼び出すと同様に、クエリを呼び出します。 クエリは、TableAdapter のメソッドです。 次のコードを TableAdapter およびクエリの名前に置き換えます。 また、クエリに必要なすべてのパラメーターを渡す必要があります。 不明の場合は、クエリ パラメーターが必要な場合や、必要などのようなパラメーターがクエリの必要な署名をし、IntelliSense を確認します。 クエリでパラメーターを使用するかどうかに応じて、コードは次の例のいずれかのようになります。  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     クエリの値を返さないと思われるものは実際には、値を返す操作を行います: クエリによって影響を受ける行の数を表す整数。 TableAdapter のインスタンスを宣言し、クエリを実行する完全なコードは、次のようになります。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>コマンド オブジェクトを使用して値を返さない SQL ステートメントを実行します。  
 次の例では、コマンドを作成し、値を返さない SQL ステートメントを実行する方法を示します。 設定とコマンドのパラメーター値を取得するのには、次を参照してください。[方法: セットとコマンド オブジェクトのパラメーターを取得](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)します。  
  
 この例では、<xref:System.Data.SqlClient.SqlCommand>オブジェクトし、が必要です。  
  
-   参照、 <xref:System>、 <xref:System.Data>、および<xref:System.Xml>名前空間。  
  
-   という名前のデータ接続`SqlConnection1`します。  
  
-   という名前のテーブル`Customers`、データ ソースが`SqlConnection1`に接続します。 (それ以外の場合、必要な有効な SQL ステートメント、データ ソースの)。  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>DataCommand を使用して値を返さない SQL ステートメントを実行するには  
  
-   メソッドからの SQL ステートメントを実行するには、次のコードを追加します。 呼び出す、`ExecuteNonQuery`メソッドの値を返さないコマンド (たとえば、 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>)。  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 アプリケーションでは、データベースにアクセスし、SQL ステートメントを実行する権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)   
 [方法: TableAdapter クエリの編集](../data-tools/how-to-edit-tableadapter-queries.md)   
 [方法: データセットにデータ](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Tableadapter を使用してデータセットを入力します。](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [方法: 設定し、コマンド オブジェクトのパラメーターを取得](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)