---
title: フォーム間でデータを渡す
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4a0d248f59754d3f46e8fab0e0924c36a80b0d89
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305547"
---
# <a name="pass-data-between-forms"></a>フォーム間でデータを渡す

このチュートリアルでは、フォーム間でデータを渡す手順について説明します。 顧客と Northwind の orders テーブルを使用して、1 つの形式は、ユーザーが顧客を選択して、2 番目の形式は、選択した顧客の注文を表示します。 このチュートリアルでは、最初のフォームからデータを受信する 2 番目の形式でメソッドを作成する方法を示します。

> [!NOTE]
> このチュートリアルでは、フォーム間でデータを渡す 1 つの方法についてのみ説明します。 データを受信する 2 つ目のコンス トラクターの作成など、フォームにデータを渡すためには、その他のオプションがあるか、最初のフォームからデータをパブリック プロパティの作成を設定できます。

このチュートリアルでは、以下のタスクを行います。

-   新しい **Windows フォーム アプリケーション** プロジェクトを作成します。

-   作成と構成を含むデータセット、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

-   **[データ ソース]** ウィンドウから項目をドラッグしたときにフォーム上に作成するコントロールを選択します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

-   **[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

-   データを表示するグリッドのある 2 番目のフォームを作成します。

-   特定の顧客の注文をフェッチする TableAdapter クエリを作成します。

-   フォーム間でデータを渡します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 一部として Visual Studio インストーラーでは、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-the-windows-forms-app-project"></a>Windows フォーム アプリ プロジェクトを作成します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**PassingDataBetweenForms**を選び、 **OK**。

     **PassingDataBetweenForms** プロジェクトが作成され、**ソリューション エクスプローラー**に追加されます。

## <a name="create-the-data-source"></a>データ ソースを作成します。

1.  開くには、**データ ソース**ウィンドウで、**データ**] メニューのをクリックして **[データ ソースの**します。

2.  **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成**ウィザードを起動します。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **[データベース モデルの選択]** ページで、**[データセット]** が指定されていることを確認し、**[次へ]** をクリックします。

5.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示します。

6.  データベースにパスワードが必要であり、重要情報を含めるオプションを有効にする場合は、このオプションを選択し、**[次へ]** をクリックします。

7.  **[アプリケーション構成ファイルに接続文字列を保存]** ページで、**[次へ]** をクリックします。

8.  **[データベース オブジェクトの選択]** ページで、**[テーブル]** ノードを展開します。

9. **Customers** テーブルと **Orders** テーブルを選択し、**[完了]** をクリックします。

     プロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウに **Customers** テーブルと **Orders** テーブルが表示されます。

## <a name="create-the-first-form-form1"></a>最初のフォーム (Form1) を作成します。

**[データ ソース]** ウィンドウから **Customers** ノードをフォームにドラッグして、データ バインド グリッド (<xref:System.Windows.Forms.DataGridView> コントロール) を作成します。

### <a name="to-create-a-data-bound-grid-on-the-form"></a>フォームにデータ バインド グリッドを作成するには

-   **[データ ソース]** ウィンドウから **Form1** にメインの **[Customers]** ノードをドラッグします。

     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) が **Form1** 上に表示されます。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource>、<xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。

## <a name="create-the-second-form"></a>2 番目のフォームを作成します。

データを渡すには 2 番目の形式を作成します。

1.  **[プロジェクト]** メニューの **[Windows フォームの追加]** を選択します。

2.  名前を既定の **Form2** のままにして、**[追加]** をクリックします。

3.  **[データ ソース]** ウィンドウから **Form2** にメインの **[Orders]** ノードをドラッグします。

     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) が **Form2** 上に表示されます。 [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、<xref:System.Windows.Forms.BindingSource>、<xref:System.Windows.Forms.BindingNavigator> がコンポーネント トレイに表示されます。

4.  コンポーネント トレイから **OrdersBindingNavigator** を削除します。

     **Form2** から **OrdersBindingNavigator** が消えます。

## <a name="add-a-tableadapter-query"></a>TableAdapter クエリを追加します。

Form2 を Form1 で選択した顧客の注文を読み込むには、TableAdapter クエリを追加します。

1.  **ソリューション エクスプローラー**で、**NorthwindDataSet.xsd** ファイルをダブルクリックします。

2.  **[OrdersTableAdapter]** を右クリックし、**[クエリの追加]** を選択します。

3.  **[SQL ステートメントを使用する]** を既定のオプションのままにして、**[次へ]** をクリックします。

4.  **[複数行を返す SELECT]** を既定のオプションのままにして、**[次へ]** をクリックします。

5.  `CustomerID` に基づいて `Orders` を返すために、クエリに WHERE 句を追加します。 クエリは次のようになります。

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > データベースに対してパラメーターの構文が正しいことを確認します。 たとえば、Microsoft Access では、WHERE 句は `WHERE CustomerID = ?` のようになります。

6.  **[次へ]** をクリックします。

7.  **DataTableMethod 名前を入力**、型`FillByCustomerID`します。

8.  **[DataTable を返す]** オプションをオフにして、**[次へ]** をクリックします。

9. **[完了]** をクリックします。

## <a name="create-a-method-on-form2-to-pass-data-to"></a>データの渡し先となる Form2 のメソッドを作成します。

1.  **Form2** を右クリックし、**[コードの表示]** を選択して**コード エディター**で **Form2** を開きます。

2.  **Form2** の `Form2_Load` メソッドの後に次のコードを追加します。

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>データを渡して、Form2 を表示する Form1 のメソッドを作成します。

1.  **Form1** の Customer データ グリッドを右クリックし、**[プロパティ]** をクリックします。

2.  **[プロパティ]** ウィンドウで、**[イベント]** をクリックします。

3.  **CellDoubleClick** イベントをダブルクリックします。

     コード エディターが表示されます。

4.  メソッド定義を次のサンプルのように更新します。

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>アプリを実行する

-   **F5** キーを押してアプリケーションを実行します。

-   **Form1** で顧客レコードをダブルクリックして、その顧客の注文を表示する **Form2** を開きます。

## <a name="next-steps"></a>次の手順

フォーム間でデータを渡した後に、アプリケーションの要件に応じてさらに操作を追加して実行できます。 このチュートリアルで行うことができる拡張には次のものがあります。

-   データセットを編集し、データベース オブジェクトの追加または削除を行います。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。

-   データベースにデータを戻して保存する機能を追加します。 詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)