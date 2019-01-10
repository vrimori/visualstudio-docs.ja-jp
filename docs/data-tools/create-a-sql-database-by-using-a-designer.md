---
title: データベース ファイルを作成し、テーブル デザイナーを使用して、
description: Visual Studio でテーブル デザイナーを使用して、データベースにテーブルと外部キーを追加する方法を説明するチュートリアル。 グラフィカル インターフェイスを使用してデータを追加する方法も示します。
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 323513c2ce9c27f2c047ac331083bb2e49392f93
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836924"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>データベースを作成し、Visual Studio でのテーブルの追加

Visual Studio を使用して作成し、SQL Server Express LocalDB にローカル データベース ファイルを更新することができます。 TRANSACT-SQL ステートメントを実行することによって、データベースを作成することも、 **SQL Server オブジェクト エクスプ ローラー** Visual Studio でツール ウィンドウです。 このトピックで作成します、 *.mdf*ファイルを開き、テーブル デザイナーを使用してテーブルおよびキーを追加します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了する、省略可能な必要**データ ストレージと処理**ワークロードを Visual Studio でインストールします。 これをインストールするには、開く**Visual Studio インストーラー**を選択し、**ワークロード**タブ。**Web & クラウド**、選択**データ ストレージと処理**します。 選択、**変更**ワークロードを Visual Studio に追加するボタンをクリックします。

## <a name="create-a-project-and-a-local-database-file"></a>プロジェクトとローカル データベース ファイルを作成する

1. **SampleDatabaseWalkthrough** という名前の Windows フォーム プロジェクトを作成します。

2. メニュー バーで選択**プロジェクト** > **新しい項目の追加**します。

3. 項目テンプレートの一覧で、下にスクロールし、選択**サービス ベースのデータベース**します。

     ![[アイテム テンプレート] ダイアログ ボックス](../data-tools/media/raddata-vsitemtemplates.png)

4. データベースの名前**SampleDatabase**を選び、**追加**ボタンをクリックします。

### <a name="add-a-data-source"></a>データ ソースを追加する

1. 場合、**データ ソース**キーを押して開くウィンドウが開いていないことが**Shift**+**Alt**+**D**または選択**ビュー** > **その他の Windows** > **データソース**メニュー バーでします。

1. **データ ソース**ウィンドウで、**新しいデータ ソースの追加**リンク。

   **データ ソース構成ウィザード**が開きます。

1. **データ ソースの種類を選択**ページで、選択**データベース**選び、**次**します。

1. **データベース モデルの選択**ページで、選択**次**(データセット) の既定値を受け入れます。

1. **データ接続の選択**] ページで、[、 **SampleDatabase.mdf**ファイル ボックスの一覧を選び、**次**。

1. **アプリケーション構成ファイルへの接続文字列を保存**ページで、選択**次**します。

1. 1 つ、**データベース オブジェクトの選択** ページで、すべてのオブジェクトにはが含まれていない、データベースを示すメッセージが表示されます。 **[完了]** を選択します。

### <a name="view-properties-of-the-data-connection"></a>データ接続のプロパティを表示

接続文字列を表示することができます、 *SampleDatabase.mdf*データ接続のプロパティ ウィンドウを開いてファイル。

- Visual Studio で、次のように選択します。**ビュー** > **SQL Server オブジェクト エクスプ ローラー**そのウィンドウが開いていない場合。 展開して [プロパティ] ウィンドウを開き、**データ接続**ノードのショートカット メニューを開き、 *SampleDatabase.mdf*を選択し、**プロパティ**します。

- または、選択**ビュー** > **サーバー エクスプ ローラー**、そのウィンドウが開いていない場合。 展開して [プロパティ] ウィンドウを開き、**データ接続**ノード。 ショートカット メニューを開き*SampleDatabase.mdf*、し、**プロパティ**します。

## <a name="create-tables-and-keys-by-using-table-designer"></a>テーブル デザイナーを使用してテーブルおよびキーを作成します。

このセクションでは、2 つのテーブル、テーブルごとに、およびサンプル データのいくつかの行の主キーを作成します。 1 つのテーブル内のレコードが他のテーブル内のレコードに対応させる方法を指定する外部キーを作成することもあります。

### <a name="create-the-customers-table"></a>Customers テーブルを作成します。

1. **サーバー エクスプ ローラー**または**SQL Server オブジェクト エクスプ ローラー**、展開、**データ接続**ノードの順に展開し、 **SampleDatabase.mdf**ノード。

2. ショートカット メニューを開き**テーブル**、し、**新しいテーブルの追加**します。

     **[テーブル デザイナー]** は、作成しているテーブルの 1 つの列を表す、1 つの既定の行のグリッドを開いて表示します。 行をグリッドに追加することによって、テーブルに列を追加します。

3. グリッドで、次のエントリのそれぞれに行を追加します。

    |列名|データの種類|Null を許容|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|false (オフ)|
    |`CompanyName`|`nvarchar(50)`|false (オフ)|
    |`ContactName`|`nvarchar (50)`|true (オン)|
    |`Phone`|`nvarchar (24)`|true (オン)|

4. ショートカット メニューを開き、`CustomerID`行をクリックし **主キーの設定**します。

5. 既定の行のショートカット メニューを開きを選択します**削除**します。

6. スクリプト ペインの最初の行の次のサンプルのように更新して、Customers (顧客) をテーブルと名前を付けます:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    次のように表示されます。

    ![テーブル デザイナー](../data-tools/media/raddata-table-designer.png)

7. 左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。

8. **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。

    変更はローカル データベース ファイルに保存されます。

### <a name="create-the-orders-table"></a>Orders テーブルを作成します。

1. 別のテーブルを追加し、次の表の各エントリの行を追加します。

    |列名|データの種類|Null を許容|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|false (オフ)|
    |`CustomerID`|`nchar(5)`|false (オフ)|
    |`OrderDate`|`datetime`|true (オン)|
    |`OrderQuantity`|`int`|true (オン)|

2. 設定**OrderID** primary key、および、削除、既定の行として。

3. スクリプト ペインの最初の行の次のサンプルのように更新して、Orders (注文) をテーブルと名前を付けます:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4. 左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。

5. **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。

    変更はローカル データベース ファイルに保存されます。

### <a name="create-a-foreign-key"></a>外部キーを作成します。

1. グリッドの右側のコンテキスト ペインでショートカット メニューを開き、**外部キー**、し、**新しい外部キーを追加**、次の図します。

     ![テーブル デザイナーでの外部キーの追加](../data-tools/media/foreignkey.png)

2. 表示されるテキスト ボックスで、**ToTable** を **Customers** に置換します。

3. T-SQL ペインで、次の例と一致する最後の行を更新します。

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. 左上隅にある、**テーブル デザイナー**を選択、 **Update**ボタンをクリックします。

5. **データベース更新のプレビュー**ダイアログ ボックスで、 **Update Database**ボタンをクリックします。

    変更はローカル データベース ファイルに保存されます。

## <a name="populate-the-tables-with-data"></a>テーブルにデータを設定します。

1. **サーバー エクスプ ローラー**または**SQL Server オブジェクト エクスプ ローラー**、サンプル データベースのノードを展開します。

2. ショートカット メニューを開き、**テーブル**ノードの **更新**の順に展開し、**テーブル**ノード。

3. Customers テーブルのショートカット メニューを開きを選択します**テーブル データの表示**します。

4. 任意のデータの一部の顧客を追加します。

    顧客 ID には任意の 5 文字を指定できます。この手順では、後で使用するために、少なくとも 1 つを選択します。

5. Orders テーブルのショートカット メニューを開きを選択します**テーブル データの表示**します。

6. いくつかの注文のデータを追加します。

    > [!IMPORTANT]
    > すべての注文 ID および注文数量が整数であり、各顧客 ID が、Customers テーブルの **CustomerID** 列で指定した値と一致することを確認します。

7. メニュー バーで選択**ファイル** > **すべて保存**します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへのアクセス](accessing-data-in-visual-studio.md)