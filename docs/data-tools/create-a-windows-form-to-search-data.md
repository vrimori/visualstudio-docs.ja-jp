---
title: データを検索する Windows フォームを作成します。
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4e04b0e4ef2f77381e305b992c5457bc46dc8261
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="create-a-windows-form-to-search-data"></a>データを検索する Windows フォームを作成します。
一般的なアプリケーションのシナリオでは、選択したデータをフォーム上に表示します。 たとえば、特定の顧客の注文、特定の注文の明細などを表示する場合があります。 このシナリオでは、ユーザーがフォームに情報を入力した後、ユーザーの入力をパラメーターとして使用してクエリが実行されます。つまり、パラメーター クエリに基づいてデータが選択されます。 クエリは、ユーザーが入力した条件を満たすデータのみを返します。 ここでは、特定の都市にいる顧客を返すクエリを作成する方法、およびユーザー インターフェイスを変更して、ユーザーが都市の名前を入力してクエリを実行するボタンを押すことができるようにする方法について説明します。

 パラメーター クエリを使用することにより、データベースが最も得意とする作業 (レコードの迅速なフィルター処理) をデータベースに任せることができるため、アプリケーションの効率が高まります。 これに対し、要求した場合、データベース全体のテーブル、ネットワーク経由で転送するレコードを検索するアプリケーション ロジックを使用、アプリケーションになる低速で効率がよくないです。

 パラメーター化クエリを追加するには、TableAdapter (コントロールのパラメーター値をそのまま使用し、クエリを実行する) を使用する、**検索条件ビルダー**  ダイアログ ボックス。 選択して、ダイアログ ボックスが開き、**クエリの追加**コマンドを**データ**メニュー (または TableAdapter スマート タグ)。

 このチュートリアルでは、以下のタスクを行います。

-   新しい Windows フォーム アプリケーション プロジェクトを作成します。

-   使用してアプリケーションでのデータ ソースの構成の作成と、**データ ソース構成**ウィザード。

-   内の項目のドロップ タイプを設定、**データソース**ウィンドウです。

-   項目をドラッグしてデータを表示するコントロールを作成する、**データソース**ウィンドウからフォームにします。

-   データを表示するコントロールをフォームに追加します。

-   完了、**検索条件ビルダー**  ダイアログ ボックス。

-   フォームにパラメーターを入力し、パラメーター化クエリを実行します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。

## <a name="create-the-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。
 作成するには、まず、 **Windows フォーム アプリケーション**です。 プロジェクトに名前が割り当てられてこの手順で、省略可能なはするが名前を付けますここため、後でプロジェクトを保存します。

#### <a name="to-create-the-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.

2. いずれかを展開**Visual c#** または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**WindowsSearchForm**を選択し**OK**です。

     **WindowsSearchForm**プロジェクトが作成され、追加**ソリューション エクスプ ローラー**です。

## <a name="create-the-data-source"></a>データ ソースを作成します。
この手順を使用してデータベースからのデータ ソースの作成、**データ ソース構成**ウィザード。

#### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成**ウィザード。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **データ接続の選択**ページは、次のいずれか。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   選択**新しい接続**を起動する、**接続接続の追加/変更** ダイアログ ボックス。

5.  データベースは、パスワードを必要とする場合は、機密データを含めるし、をクリックするオプションを選択**次**です。

6.  **接続文字列をアプリケーション構成ファイルに保存** ページで、をクリックして**次**です。

7.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。

8.  選択、**顧客**テーブル、およびをクリックして**完了**です。

     **NorthwindDataSet**をプロジェクトに追加され、**顧客**テーブルに表示されます、**データ ソース**ウィンドウです。

## <a name="create-the-form"></a>フォームを作成します。
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウからフォームにします。

#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには

1.  展開、**顧客**内のノード、**データソース**ウィンドウです。

2.  ドラッグ、**顧客**ノードから、**データ ソース**ウィンドウ、フォームにします。

     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォーム上に表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

## <a name="add-parameterization-search-functionality-to-the-query"></a>クエリにパラメーター化 (検索機能) を追加します。
 使用して元のクエリに WHERE 句を追加することができます、**検索条件ビルダー**  ダイアログ ボックス。

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>パラメーター クエリとコントロールを作成してパラメーターを入力するには

1.  選択、<xref:System.Windows.Forms.DataGridView>コントロールをクリックして**クエリの追加**上、**データ**メニュー。

2.  型`FillByCity`で、**新しいクエリ名**上の領域、**検索条件ビルダー**  ダイアログ ボックス。

3.  追加`WHERE City = @City`でクエリを**クエリ テキスト**領域。

     クエリは次のようになります。

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    >  アクセスおよび OLE DB データ ソースは疑問符 () を使用して ('? ') パラメーターを表すので、WHERE 句は次のとおり:`WHERE City = ?`です。

4.  をクリックして**OK**を閉じる、**検索条件ビルダー**  ダイアログ ボックス。

     A **FillByCityToolStrip**フォームに追加します。

## <a name="testing-the-application"></a>アプリケーションのテスト
 アプリケーションを実行すると、パラメーターを入力として取得できる状態のフォームが開きます。

#### <a name="to-test-the-application"></a>アプリケーションをテストするには

1.  F5 キーを押してアプリケーションを実行します。

2.  型**ロンドン**に、**市区町村**テキスト ボックス、およびクリック**FillByCity**です。

     データ グリッドには、条件を満たす顧客が取得されます。 この例では、データ グリッドのみが表示されますの値を持つ顧客**ロンドン**でその**市区町村**列です。

## <a name="next-steps"></a>次の手順
 アプリケーションの要件に応じて、パラメーター付きのフォームを作成した後に、追加の操作を実行できます。 このチュートリアルで行うことができる拡張には次のものがあります。

-   関連するデータを表示するコントロールを追加します。 詳細については、次を参照してください。[データセットのリレーションシップ](relationships-in-datasets.md)です。

-   データセットを編集し、データベース オブジェクトの追加または削除を行います。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)