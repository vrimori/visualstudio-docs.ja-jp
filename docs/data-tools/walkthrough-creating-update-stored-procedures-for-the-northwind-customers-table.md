---
title: "チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成 | Microsoft Docs"
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
  - "Northwind サンプル データベース"
  - "O/R デザイナー, ストアド プロシージャ"
  - "ストアド プロシージャ [Visual Studio]"
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成
[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] ドキュメントのヘルプ トピックの中には、Customers テーブルのデータの更新 \(挿入、更新、削除\) を実行するために、Northwind サンプル データベースに追加のストアド プロシージャが必要となるものがあります。  
  
 このチュートリアルでは [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] の Northwind サンプル データベースで追加ストアド プロシージャを作成する手順について説明します。  
  
 このトピックの「次の手順」のセクションでは、これらの追加ストアド プロシージャの使用方法を説明するトピックへのリンクを示します。  
  
 このチュートリアルでは、次のタスクを実行する方法を学習します。  
  
-   Northwind サンプル データベースへのデータ接続を作成します。  
  
-   ストアド プロシージャを作成します。  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、次の条件が必要です。  
  
-   Northwind サンプル データベースの SQL Server バージョンにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## Northwind データベースへの接続  
 このチュートリアルでは Northwind データベースの SQL Server バージョンへの接続が必要です。  次の手順では、データ接続を作成する手順について説明します。  
  
> [!NOTE]
>  既に Northwind データベースへのデータ接続がある場合は、次のセクションの「ストアド プロシージャの作成」に進むことができます。  
  
#### Northwind SQL Server データベースへのデータ接続を作成するには  
  
1.  **\[表示\]** メニューの **\[サーバー エクスプローラー\]** または **\[データベース エクスプローラー\]** をクリックします。  
  
2.  **\[データ接続\]** を右クリックし、**\[接続の追加\]** をクリックします。  
  
3.  **\[データ ソースの選択\]** ダイアログ ボックスで、**\[Microsoft SQL Server\]** をクリックして **\[OK\]** をクリックします。  
  
     **\[接続の追加\]** ダイアログ ボックスが開き、**\[データ ソース\]** が **\[Microsoft SQL Server \(SqlClient\)\]** でない場合は、**\[変更\]** をクリックして **\[データ ソースの選択\] または \[データ ソースの変更\]** ダイアログ ボックスを開いて、**\[Microsoft SQL Server\]** をクリックし、**\[OK\]** をクリックします。  
  
4.  ドロップダウン リストで **\[サーバー名\]** をクリックするか、Northwind データベースがあるサーバーの名前を入力します。  
  
5.  データベースまたはアプリケーションの要件に基づいて、**\[Windows 認証を使用する\]** をクリックするか、SQL Server を実行しているコンピューターにログオンするための特定のユーザー名とパスワードを使用します \(**\[SQL Server 認証\]**\)。  
  
6.  **\[データベース名の選択または入力\]** ボックスの一覧で Northwind データベースをクリックします。  
  
7.  **\[OK\]** をクリックします。  
  
     データ接続が**サーバー エクスプローラー**または**データベース エクスプローラー**に追加されます。  
  
## ストアド プロシージャの作成  
 **サーバー エクスプローラー**または**データベース エクスプローラー**で [Visual Database Tools](http://msdn.microsoft.com/ja-jp/6b145922-2f00-47db-befc-bf351b4809a1) を使用して Northwind データベースに対して指定された SQL スクリプトを実行することにより、ストアド プロシージャを作成します。  
  
#### SQL スクリプトを使用してストアド プロシージャを作成するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で Northwind データベースを展開します。  
  
2.  **\[ストアド プロシージャ\]** ノードを右クリックし、**\[新しいストアド プロシージャの追加\]** をクリックします。  
  
3.  `CREATE PROCEDURE` テンプレートを置き換えるコード エディターに次のコードを貼り付けます。  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  コード エディターのすべてのテキストを選択し、選択したテキストを右クリックして、**\[選択範囲の実行\]** をクリックします。  
  
     SelectCustomers、InsertCustomers、UpdateCustomers、DeleteCustomers ストアド プロシージャが Northwind データベースに作成されます。  
  
## 次の手順  
 ストアド プロシージャを作成したので、その使用方法を次のチュートリアルで確認します。  
  
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)  
  
 [Walkthrough: Customizing the Insert, Update, and Delete Behavior of Entity Classes](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)