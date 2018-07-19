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
ms.openlocfilehash: c8d400f8fa46fa10876d1827205671b6d90a3e33
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089439"
---
# <a name="pass-data-between-forms"></a>フォーム間でデータを渡す
このチュートリアルでは、フォーム間でデータを渡す手順について説明します。 顧客と Northwind の orders テーブルを使用して、1 つの形式は、ユーザーが顧客を選択して、2 番目の形式は、選択した顧客の注文を表示します。 このチュートリアルでは、最初のフォームからデータを受信する 2 番目の形式でメソッドを作成する方法を示します。

> [!NOTE]
>  このチュートリアルでは、フォーム間でデータを渡す 1 つの方法についてのみ説明します。 データを受信する 2 つ目のコンス トラクターの作成など、フォームにデータを渡すためには、その他のオプションがあるか、最初のフォームからデータをパブリック プロパティの作成を設定できます。

 このチュートリアルでは、以下のタスクを行います。

-   新しいを作成する**Windows フォーム アプリケーション**プロジェクト。

-   作成と構成を含むデータセット、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

-   項目をドラッグしたときに、フォームに作成するコントロールを選択すると、**データソース**ウィンドウ。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

-   項目をドラッグして、データ バインド コントロールを作成、**データソース**ウィンドウからフォームにします。

-   データを表示するグリッドのある 2 番目のフォームを作成します。

-   特定の顧客の注文をフェッチする TableAdapter クエリを作成します。

-   フォーム間でデータを渡します。

## <a name="prerequisites"></a>前提条件
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 一部として Visual Studio インストーラーでは、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-the-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。

### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**PassingDataBetweenForms**を選び、 **OK**。

     **PassingDataBetweenForms**プロジェクトを作成するとに追加**ソリューション エクスプ ローラー**します。

## <a name="create-the-data-source"></a>データ ソースを作成します。

### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソースの構成**ウィザード。

3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。

4.  **データベース モデルの選択**ことを確認します ページで、**データセット**が指定され、をクリックし、 **次へ**します。

5.  **データ接続の選択** ページで、次のいずれかを実行します。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。

6.  オプションを選択し、をクリックし、データベースには、パスワードが必要ですし、機密データを含めるためのオプションが有効になっている場合は、**次**します。

7.  **接続文字列をアプリケーション構成ファイルに保存**] ページで [**次**します。

8.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノード。

9. 選択、**顧客**と**注文**テーブル、およびクリック**完了**。

     **NorthwindDataSet**がプロジェクトに追加、**顧客**と**注文**に表示されるテーブル、**データ ソース**ウィンドウ。

## <a name="create-the-first-form-form1"></a>最初のフォーム (Form1) を作成します。
 データ バインド グリッドを作成することができます (、<xref:System.Windows.Forms.DataGridView>コントロール)、ドラッグして、**顧客**ノードから、**データ ソース**ウィンドウから、フォームにします。

### <a name="to-create-a-data-bound-grid-on-the-form"></a>フォームにデータ バインド グリッドを作成するには

-   メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウ**Form1**。

     A<xref:System.Windows.Forms.DataGridView>とツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) レコードを移動するために表示されます。 **Form1**します。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

## <a name="create-the-second-form-form2"></a>2 番目のフォーム (Form2) を作成します。

### <a name="to-create-a-second-form-to-pass-the-data-to"></a>データの渡し先となる 2 番目のフォームを作成するには

1.  **[プロジェクト]** メニューの **[Windows フォームの追加]** を選択します。

2.  既定の名前をそのまま**Form2**、 をクリック**追加**します。

3.  メインのドラッグ**注文**ノードから、**データ ソース**ウィンドウ**Form2**。

     A<xref:System.Windows.Forms.DataGridView>とツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) レコードを移動するために表示されます。 **Form2**します。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、CustomersTableAdapter、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

4.  削除、 **OrdersBindingNavigator**コンポーネント トレイから。

     **OrdersBindingNavigator**から消えます**Form2**します。

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Form2 を Form1 で選択した顧客の注文を読み込む TableAdapter クエリを追加します。

### <a name="to-create-a-tableadapter-query"></a>TableAdapter クエリを作成するには

1.  ダブルクリックして、 **NorthwindDataSet.xsd**ファイル**ソリューション エクスプ ローラー**します。

2.  右クリックし、 **OrdersTableAdapter**、選び**クエリの追加**します。

3.  既定のオプションのまま**SQL ステートメントを使用**、 をクリックし、**次**。

4.  既定のオプションのまま**を行を返す SELECT**、順にクリックします**次**します。

5.  返すクエリに WHERE 句を追加`Orders`に基づいて、`CustomerID`します。 クエリは次のようになります。

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    >  データベースに対してパラメーターの構文が正しいことを確認します。 たとえば、Microsoft Access では、WHERE 句は `WHERE CustomerID = ?` のようになります。

6.  **[次へ]** をクリックします。

7.  **DataTableMethod 名前を入力**、型`FillByCustomerID`します。

8.  クリア、 **DataTable を返す**オプションをクリックして**次**します。

9. **[完了]** をクリックします。

## <a name="create-a-method-on-form2-to-pass-data-to"></a>データの渡し先となる Form2 のメソッドを作成します。

### <a name="to-create-a-method-to-pass-data-to"></a>データの渡し先となるメソッドを作成するには

1.  右クリック**Form2**、選択と**コードの表示**を開く**Form2**で、**コード エディター**します。

2.  次のコードを追加**Form2**後、`Form2_Load`メソッド。

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>データを渡して、Form2 を表示する Form1 のメソッドを作成します。

### <a name="to-create-a-method-to-pass-data-to-form2"></a>Form2 にデータを渡すメソッドを作成するには

1.  **Form1**、顧客データ グリッドを右クリックし、クリックして**プロパティ**します。

2.  **プロパティ**ウィンドウで、をクリックして**イベント**します。

3.  ダブルクリックして、 **CellDoubleClick**イベント。

     コード エディターが表示されます。

4.  メソッド定義を次のサンプルのように更新します。

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-application"></a>アプリケーションを実行する

### <a name="to-run-the-application"></a>アプリケーションを実行するには

-   **F5** キーを押してアプリケーションを実行します。

-   顧客レコードをダブルクリックして**Form1**を開く**Form2**その顧客の注文とします。

## <a name="next-steps"></a>次の手順

フォーム間でデータを渡した後に、アプリケーションの要件に応じてさらに操作を追加して実行できます。 このチュートリアルで行うことができる拡張には次のものがあります。

-   データセットを編集し、データベース オブジェクトの追加または削除を行います。 詳細については、[データセットの作成と構成](../data-tools/create-and-configure-datasets-in-visual-studio.md)に関するページを参照してください。

-   データベースにデータを戻して保存する機能を追加します。 詳細については、次を参照してください。[データをデータベースに保存](../data-tools/save-data-back-to-the-database.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)