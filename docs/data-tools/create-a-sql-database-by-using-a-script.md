---
title: "チュートリアル: サイズの小さいサンプル データベースの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル: サイズの小さいサンプル データベースの作成
このチュートリアルでは、「[チュートリアル: ADO.NET を使用した単純なデータ アプリケーションの作成](../data-tools/create-a-simple-data-application-by-using-adonet.md)」のサンプル コードを含む小さなデータベースを作成するために Visual Studio を使用します。  
  
 **このトピックの内容**  
  
-   [データベース スキーマを含むスクリプトの作成](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [データベース プロジェクトの作成とそのスキーマのインポート](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [データベースの配置](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] がインストールされている必要があります。  データベースを作成、配置するアクセス許可がある、データベース サーバーまたは LocalDB データベースに、接続できる必要があります。  
  
##  <a name="CreateScript"></a> データベース スキーマを含むスクリプトの作成  
  
#### スキーマのインポートに使用するスクリプトを作成するには  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で、メニュー バーの **\[ファイル\]**、**\[新規作成\]**、**\[ファイル\]** の順にクリックします。  
  
     **\[新しいファイル\]** ダイアログ ボックスが表示されます。  
  
2.  **\[カテゴリ\]** ボックスの一覧の **\[全般\]** をクリックします。  
  
3.  **\[テンプレート\]** ボックスの一覧の **\[SQL ファイル\]**、**\[開く\]** の順にクリックします。  
  
     Transact\-SQL エディターが開きます。  
  
4.  次の Transact\-SQL コードをコピーし、Transact\-SQL エディターに貼り付けます。  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  メニュー バーで **\[ファイル\]**、**\[名前を付けて SqlQuery\_1.sql を保存\]** の順に選択します。  
  
     **\[名前を付けてファイルを保存\]** ダイアログ ボックスが表示されます。  
  
6.  **\[ファイル名\]** ボックスに「`SampleImportScript.sql`」と入力し、ファイルの保存場所を確認し、**\[保存\]** をクリックします。  
  
7.  メニュー バーで **\[ファイル\]**、**\[ソリューションを閉じる\]** の順に選択します。  
  
     次に、データベース プロジェクトを作成し、作成したスクリプトからスキーマをインポートします。  
  
##  <a name="CreateProject"></a> データベース プロジェクトの作成とそのスキーマのインポート  
  
#### データベース プロジェクトを作成するには  
  
1.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
     **\[新しいプロジェクト\]** ダイアログ ボックスが表示されます。  
  
2.  **\[インストール済み\]** の下で **\[テンプレート\]** のノードを展開して **\[他の言語\]** のノードを展開し、**\[SQL Server\]** のカテゴリ、**SQL Server データベース プロジェクト** テンプレートの順に選択します。  
  
    > [!NOTE]
    >  **\[他の言語\]** ノードは、Visual Studio のインストールに表示されないことがあります。  
  
3.  **\[名前\]** ボックスに「`Small Database`」と入力します。  
  
4.  **\[ソリューションのディレクトリを作成\]** チェック ボックスがオンになっていない場合はオンにします。  
  
5.  **\[ソース管理に追加\]** チェック ボックスがオフになっていない場合はオフにし、**\[OK\]** をクリックします。  
  
     データベース プロジェクトが作成され、**ソリューション エクスプローラー**に表示されます。  
  
     次に、スクリプトからデータベース スキーマをインポートします。  
  
#### スクリプトからデータベース スキーマをインポートするには  
  
1.  メニュー バーで **\[プロジェクト\]**、**\[インポート\]**、**\[スクリプト\]** の順に選択します。  
  
2.  \[ようこそ\] ページで、テキストを確認し、**\[次へ\]** をクリックします。  
  
3.  **\[単一ファイル\]** をクリックし、**\[参照\]** をクリックします。  
  
     **\[SQL スクリプトのインポート\]** ダイアログ ボックスが表示されます。  
  
4.  SampleImportScript.sql ファイルを保存したフォルダーを開いて選択し、**\[開く\]** をクリックします。  
  
5.  **\[完了\]** をクリックして、**\[SQL スクリプトのインポート\]** ダイアログ ボックスを閉じます。  
  
     スクリプトがインポートされ、このスクリプトで定義したオブジェクトがデータベース プロジェクトに追加されます。  
  
6.  概要を確認した後、**\[完了\]** をクリックして **\[SQL スクリプト ファイルのインポート\]** ダイアログ ボックスを閉じます。  
  
7.  **\[ソリューション エクスプローラー\]** で、プロジェクトの Sales、Scripts、および Security のフォルダーを展開し、.sql ファイルが含まれていることを確認します。  
  
8.  **\[SQL Server オブジェクト エクスプローラー\]** で、データベースが **\[プロジェクト\]** ノードの下に表示されていることを確認します。  
  
     この時点で、データベースには、テーブル、ストアド プロシージャなどのシステム オブジェクトのみが格納されています。  データベースを配置した後に、スクリプトに定義されたユーザー テーブルとストアド プロシージャが含まれます。  
  
##  <a name="DeployDatabase"></a> データベースの配置  
 F5 キーを選択すると、データベースを既定で LocalDB のデータベースに配置 \(または発行\) します。  プロジェクトのプロパティ ページを開き、**\[デバッグ\]** をクリックして接続文字列を変更すると、データベースを別の場所に配置できます。