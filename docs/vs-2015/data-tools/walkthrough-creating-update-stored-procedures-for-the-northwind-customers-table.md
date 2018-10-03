---
title: 'チュートリアル: Northwind の Customers テーブル ストアド プロシージャを更新プログラムを作成する |Microsoft Docs'
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
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: bbcd68b7604f7a80546168406146f326e1bac224
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533650"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>チュートリアル: Northwind の Customers テーブル用 Update ストアド プロシージャの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

一部のヘルプ トピック、[!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]ドキュメントは、Customers テーブルのデータの更新 (挿入、更新、および削除) を実行するため、Northwind サンプル データベースで追加のストアド プロシージャを必要とします。  
  
 このチュートリアルでは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の Northwind サンプル データベースで追加ストアド プロシージャを作成する手順について説明します。  
  
 このトピックの「次の手順」のセクションでは、これらの追加ストアド プロシージャの使用方法を説明するトピックへのリンクを示します。  
  
 このチュートリアルでは、次のタスクを実行する方法を学習します。  
  
-   Northwind サンプル データベースへのデータ接続を作成します。  
  
-   ストアド プロシージャを作成します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、次の条件が必要です。  
  
-   Northwind サンプル データベースの SQL Server バージョンにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="connecting-to-the-northwind-database"></a>Northwind データベースへの接続  
 このチュートリアルでは Northwind データベースの SQL Server バージョンへの接続が必要です。 次の手順では、データ接続を作成する手順について説明します。  
  
> [!NOTE]
>  既に Northwind データベースへのデータ接続がある場合は、次のセクションの「ストアド プロシージャの作成」に進むことができます。  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Northwind SQL Server データベースへのデータ接続を作成するには  
  
1.  **ビュー**  メニューのをクリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  右クリック**データ接続**クリック**接続の追加**します。  
  
3.  **データ ソースの選択**ダイアログ ボックスで、をクリックして**Microsoft SQL Server**、順にクリックします**OK**。  
  
     場合、**接続の追加** ダイアログ ボックスが開き、および**データ ソース**ない**Microsoft SQL Server (SqlClient)**、 をクリックして**変更**を開く、**データ ソースの選択/変更**ダイアログ ボックスで、をクリックして**Microsoft SQL Server**、順にクリックします**OK**します。  
  
4.  をクリックして、**サーバー名**ドロップダウン リストで一覧表示、または、Northwind データベースが配置されているサーバーの名前を入力します。  
  
5.  クリックするか、データベースまたはアプリケーションの要件に基づき、 **Windows 認証を使用して**か特定のユーザー名とパスワードを使用して SQL Server を実行しているコンピューターにログオン (**SQL Server 認証**).  
  
6.  Northwind データベースをクリックして、**を選択するか、データベース名を入力**一覧。  
  
7.  **[OK]** をクリックします。  
  
     データ接続が追加**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
## <a name="creating-the-stored-procedures"></a>ストアド プロシージャの作成  
 使用して、Northwind データベースに対して指定された SQL スクリプトを実行してストアド プロシージャの作成、 [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1)で使用できる**サーバー エクスプ ローラー** / **データベース エクスプ ローラー**します。  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>SQL スクリプトを使用してストアド プロシージャを作成するには  
  
1.  Northwind データベースを展開**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  右クリックし、 **Stored Procedures**ノードをクリックします**新しいストアド プロシージャの追加**します。  
  
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
  
4.  コード エディターでのすべてのテキストを選択し、選択したテキストを右クリックし、クリックして**選択範囲の実行**します。  
  
     SelectCustomers、InsertCustomers、UpdateCustomers、DeleteCustomers ストアド プロシージャが Northwind データベースに作成されます。  
  
## <a name="next-steps"></a>次の手順  
 ストアド プロシージャを作成したので、その使用方法を次のチュートリアルで確認します。  
  
 [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [チュートリアル: LINQ to SQL クラス (O/R デザイナー) を作成します。](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [チュートリアル : エンティティ クラスの挿入、更新、および削除の動作のカスタマイズ](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Visual Studio での SQL ツール](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)