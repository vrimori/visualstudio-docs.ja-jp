---
title: スクリプトを使用して SQL database の作成 |Microsoft Docs
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9a2e3fdeccf8e3b094bd5fb1519d740cee7ce41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533673"
---
# <a name="create-a-sql-database-by-using-a-script"></a>スクリプトを使用して SQL database を作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[スクリプトを使用して SQL database を作成する](https://docs.microsoft.com/visualstudio/data-tools/create-a-sql-database-by-using-a-script)します。  
  
  
このチュートリアルでのサンプル コードを含む小さなデータベースを作成する Visual Studio を使用する[ADO.NET を使用して単純なデータ アプリケーションを作成する](../data-tools/create-a-simple-data-application-by-using-adonet.md)します。  
  
 **このトピックの内容**  
  
-   [データベース スキーマを含むスクリプトを作成します。](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [データベース プロジェクトを作成し、スキーマのインポート](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [データベースをデプロイします。](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、SQL Server Express LocalDB またはインストールされている別の SQL database が必要です。  
  
##  <a name="CreateScript"></a> データベース スキーマを含むスクリプトを作成します。  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>スキーマのインポートに使用するスクリプトを作成するには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、メニュー バーで選択**ファイル** > **新規** > **ファイル**します。  
  
     **新しいファイル** ダイアログ ボックスが表示されます。  
  
2.  **カテゴリ**一覧で、**全般**します。  
  
3.  **テンプレート**一覧で、 **Sql ファイル**を選び、**オープン**ボタンをクリックします。  
  
     TRANSACT-SQL エディターが開きます。  
  
4.  次の TRANSACT-SQL コードをコピーし、TRANSACT-SQL エディターに貼り付けます。  
  
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
  
5.  メニュー バーで選択**ファイル** > **付けて SqlQuery_1.sql を保存**します。  
  
     **ファイルに名前を付けて** ダイアログ ボックスが表示されます。  
  
6.  **ファイル名**ボックスに、入力`SampleImportScript.sql`、ここでファイルを保存したり、選択の場所に注意してください、**保存**ボタンをクリックします。  
  
7.  メニュー バーで選択**ファイル** > **ソリューションを閉じる**します。  
  
     次に、データベース プロジェクトを作成し、作成したスクリプトからスキーマをインポートします。  
  
##  <a name="CreateProject"></a> データベース プロジェクトを作成し、スキーマのインポート  
  
#### <a name="to-create-a-database-project"></a>データベース プロジェクトを作成するには  
  
1.  メニュー バーで **[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  **インストール済み**、展開、**テンプレート**ノード、展開、**他の言語**ノードを選択、 **SQL Server**カテゴリ、し、選択、 **SQL Server データベース プロジェクト**テンプレート。  
  
    > [!NOTE]
    >  **他の言語**ノードは、Visual Studio のすべてのインストールに表示されません。  
  
3.  **名前**ボックスに、入力`Small Database`します。  
  
4.  選択、**ソリューションのディレクトリを作成**チェック ボックスが選択されていない場合。  
  
5.  クリア、**ソース管理に追加**でない場合、消去、および順に選択します チェック ボックス、 **OK**ボタンをクリックします。  
  
     データベース プロジェクトが作成され**ソリューション エクスプ ローラー**します。  
  
     次に、スクリプトからデータベース スキーマをインポートします。  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>スクリプトからデータベース スキーマをインポートするには  
  
1.  メニュー バーで選択**プロジェクト** > **インポート** > **スクリプト**します。  
  
2.  **ようこそ**ページで、テキストを確認し、選択、 **[次へ]** ボタンをクリックします。  
  
3.  選択、 **1 つのファイル**オプション ボタンを選び、**参照**ボタンをクリックします。  
  
     **SQL スクリプトのインポート** ダイアログ ボックスが表示されます。  
  
4.  SampleImportScript.sql ファイルを保存したフォルダーを開き、ファイルを選択して選択し、、**オープン**ボタンをクリックします。  
  
5.  選択、**完了**を閉じる ボタン、 **SQL スクリプトのインポート** ダイアログ ボックス。  
  
     スクリプトがインポートされ、このスクリプトで定義したオブジェクトがデータベース プロジェクトに追加されます。  
  
6.  概要を確認し、**完了**を閉じる ボタン、 **SQL スクリプト ファイルのインポート** ダイアログ ボックス。  
  
7.  **ソリューション エクスプ ローラー**Sales、Scripts、およびセキュリティを展開し、プロジェクトのフォルダーを .sql ファイルが含まれることを確認します。  
  
8.  **SQL Server オブジェクト エクスプ ローラー**、下に、データベースが表示されることを確認、**プロジェクト**ノード。  
  
     この時点で、データベースには、テーブル、ストアド プロシージャなどのシステム オブジェクトのみが格納されています。 データベースを配置した後に、スクリプトに定義されたユーザー テーブルとストアド プロシージャが含まれます。  
  
##  <a name="DeployDatabase"></a> データベースをデプロイします。  
 押したときに、 **F5**キー、配置 (または発行する) 既定の LocalDB データベースにデータベース。 データベースを別の場所に配置するには、プロジェクトのプロパティ ページを開いて選択すると、**デバッグ**タブをクリックし、接続文字列を変更します。

