---
title: デザイナーを使用して SQL database の作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0ef261ec4ea803dcfc42b6151a5c828d5b03811a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860332"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>デザイナーを使用して SQL database を作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
テーブルを追加して、Visual Studio を使用して作成し、SQL Server Express LocalDB にローカル データベース ファイルを更新して、列を定義するなど、基本的なタスクを調べることができます。 このチュートリアルを終了すると、ローカル データベースを使用してさらに高度な機能を使用できるようになり、こうした機能を必要とする他のチュートリアルへの準備となります。  
  
 SQL Server Management Studio (個別のダウンロード) または TRANSACT-SQL ステートメントを使用してデータベースを作成することも、 **SQL Server オブジェクト エクスプ ローラー** Visual Studio でツール ウィンドウです。  
  
 このチュートリアルには次のタスクがあります。  
  
-   [プロジェクトとローカル データベース ファイルを作成します。](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
-   [テーブル、列、主キー、および外部キーを作成します。](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
-   [テーブルにデータを設定します。](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、SQL Server Data Tools がインストールされているがあることを確認します。 **ビュー**が、表示する] メニューの [ **SQL Server オブジェクト エクスプ ローラー**します。 これがない場合を参照してください**プログラム追加と削除**、 をクリック**Visual Studio 2015**を選択します**変更**、次のボックスをオンおよび**SQL Server Data Tools。**.  
  
##  <a name="BKMK_CreateNewSQLDB"></a> プロジェクトとローカル データベース ファイルを作成します。  
  
#### <a name="to-create-a-project-and-a-database-file"></a>プロジェクトとローカル データベース ファイルを作成するには  
  
1. という名前の Windows フォーム プロジェクトを作成する`SampleDatabaseWalkthrough`します。  
  
2. メニュー バーで選択**プロジェクト** > **新しい項目の追加**します。  
  
3. 項目テンプレートの一覧で、下にスクロールし、選択**サービス ベースのデータベース**します。  
  
    ![項目テンプレート ダイアログ ボックス](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. データベースの名前**SampleDatabase**を選び、**追加**ボタンをクリックします。  
  
5. 場合、**データソース**Shift + Alt + D キーを選択してか、メニュー バーで選択すると開くウィンドウが開いていないことが**ビュー** > **その他の Windows**  > **データソース**します。  
  
6. **データ ソース**ウィンドウで、**新しいデータ ソースの追加**リンク。  
  
7. **データ ソース構成ウィザード**を選択します、 **[次へ]** 4 回の既定の設定をそのまま使用し、ボタン、**完了**ボタンをクリックします。  
  
   データベースのプロパティ ウィンドウを開くと、その接続文字列と、プライマリ .mdf ファイルの位置を確認できます。 データベース ファイルが、プロジェクト フォルダーが表示されます。  
  
-   Visual Studio で、次のように選択します。**ビュー** > **SQL Server オブジェクト エクスプ ローラー**そのウィンドウが開いていない場合。 展開して [プロパティ] ウィンドウを開き、**データ接続**ノードは、SampleDatabase.mdf のショートカット メニューを開き、選択し、**プロパティ**します。  
  
-   または、選択**ビュー** > **サーバー エクスプ ローラー**、そのウィンドウが開いていない場合。 展開して [プロパティ] ウィンドウを開き、**データ接続**ノード。 クリックして、SampleDatabase.mdf のショートカット メニューを開き**プロパティ**します。  
  
##  <a name="BKMK_CreateNewTbls"></a> テーブル、列、主キー、および外部キーを作成します。  
 このセクションでは、いくつかのテーブルと各テーブルの主キー、およびサンプル データの行を作成します。 次のチュートリアルでは、この情報がアプリケーションでどのように表示されるかを理解することができます。 また外部キーを作成して、1 つのテーブルのレコードが他のテーブルのレコードに対応する方法を指定できます。  
  
#### <a name="to-create-the-customers-table"></a>Customers テーブルを作成するには  
  
1.  **サーバー エクスプ ローラー**または**SQL Server オブジェクト エクスプ ローラー**、展開、**データ接続**ノードの順に展開し、 **SampleDatabase.mdf**ノード。  
  
2.  ショートカット メニューを開き**テーブル**、し、**新しいテーブルの追加**します。  
  
     **テーブル デザイナー**が開き、作成しているテーブル内 1 つの列を表す 1 つの既定の行とグリッドを表示します。 行をグリッドに追加することによって、テーブルに列を追加します。  
  
3.  グリッドで、次のエントリのそれぞれに行を追加します。  
  
    |列名|データの種類|Null を許容|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|false (オフ)|  
    |`CompanyName`|`nvarchar(50)`|false (オフ)|  
    |`ContactName`|`nvarchar (50)`|true (オン)|  
    |`Phone`|`nvarchar (24)`|true (オン)|  
  
4.  ショートカット メニューを開き、`CustomerID`行をクリックし **主キーの設定**します。  
  
5.  既定の行のショートカット メニューを開きを選択します**削除**します。  
  
6.  スクリプト ペインの最初の行の次のサンプルのように更新して、Customers (顧客) をテーブルと名前を付けます:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     次のように表示されます。  
  
     ![テーブル デザイナー](../data-tools/media/raddata-table-designer.png "raddata テーブル デザイナー")  
  
7.  左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。  
  
8.  **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
#### <a name="to-create-the-orders-table"></a>Orders テーブルを作成するには  
  
1.  別のテーブルを追加し、次の表の各エントリの行を追加します。  
  
    |列名|データの種類|Null を許容|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|false (オフ)|  
    |`CustomerID`|`nchar(5)`|false (オフ)|  
    |`OrderDate`|`datetime`|true (オン)|  
    |`OrderQuantity`|`int`|true (オン)|  
  
2.  設定**OrderID** primary key、および、削除、既定の行として。  
  
3.  スクリプト ペインの最初の行の次のサンプルのように更新して、Orders (注文) をテーブルと名前を付けます:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4.  左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。  
  
5.  **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
#### <a name="to-create-a-foreign-key"></a>外部キーを作成するには  
  
1.  グリッドの右側のコンテキスト ペインでショートカット メニューを開き、**外部キー**、し、**新しい外部キーを追加**、次の図します。  
  
     ![テーブル デザイナーで外部キーを追加する](../data-tools/media/foreignkey.png "不変")  
  
2.  テキスト ボックスが表示されますが、置換**ToTable**で`Customers`します。  
  
3.  T-SQL ペインで、次の例と一致する最後の行を更新します。  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4.  左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。  
  
5.  **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。  
  
     変更はローカル データベース ファイルに保存されます。  
  
##  <a name="BKMK_Populating"></a> テーブルにデータを設定します。  
  
#### <a name="to-populate-the-tables-with-data"></a>テーブルにデータを読み込むには  
  
1.  **サーバー エクスプ ローラー**または**SQL Server オブジェクト エクスプ ローラー**、サンプル データベースのノードを展開します。  
  
2.  ショートカット メニューを開き、**テーブル**ノードの **更新**の順に展開し、**テーブル**ノード。  
  
3.  Customers テーブルのショートカット メニューを開きを選択します**テーブル データの表示**します。  
  
4.  最低 3 人の Customer (顧客) に任意のデータを追加します。  
  
     顧客 ID には任意の 5 文字を指定できます。この手順では、後で使用するために、少なくとも 1 つを選択します。  
  
5.  Orders テーブルのショートカット メニューを開きを選択します**テーブル データの表示**します。  
  
6.  最低 3 件の注文データを追加します。  
  
    > [!IMPORTANT]
    >  すべての注文 ID および注文数量が整数であり、各顧客 ID が、Customers テーブルの CustomerID 列で指定した値と一致することを確認します。  
  
7.  メニュー バーで選択**ファイル** > **すべて保存**します。  
  
8.  メニュー バーで選択**ファイル** > **ソリューションを閉じる**します。  
  
    > [!NOTE]
    >  ベスト プラクティスとして、データベースをコピーし、他の場所にそのコピーを貼り付ける、またはコピーに異なる名前を付けることによって、作成したデータベースのバックアップを実行します。  
  
## <a name="next-steps"></a>次の手順  
 サンプル データのローカル データベース ファイルをしたのでデータベース タスクについて説明するチュートリアルのいずれかを行うことができます。

