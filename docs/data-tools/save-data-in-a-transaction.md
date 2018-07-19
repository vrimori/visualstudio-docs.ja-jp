---
title: 'チュートリアル: トランザクションにデータを保存する'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2829e1dffa0975a1970b8727f9baf79febf9b32c
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174888"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>チュートリアル: トランザクションにデータを保存する
このチュートリアルを使用して、トランザクションでデータを保存する方法について説明、<xref:System.Transactions>名前空間。 このチュートリアルでは、Windows フォーム アプリケーションを作成します。 Northwind サンプル データベース内のデータセットを 2 つのテーブルを作成するのにデータ ソース構成ウィザードを使用します。 Windows フォームにデータ バインド コントロールと BindingNavigator の保存 ボタンを TransactionScope 内部でデータベースを更新するためにコードを変更するを追加します。

## <a name="prerequisites"></a>前提条件
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 一部として Visual Studio インストーラーでは、SQL Server Express LocalDB をインストールすることができます、 **.NET デスクトップ開発**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。
 作成するには、まず、 **Windows フォーム アプリケーション**します。

#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**SavingDataInATransactionWalkthrough**を選び、 **OK**。

     **SavingDataInATransactionWalkthrough**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。

## <a name="create-a-database-data-source"></a>データベースのデータ ソースを作成します。
 このステップでは、**データ ソース構成ウィザード**に基づいてデータ ソースを作成する、`Customers`と`Orders`Northwind サンプル データベース内のテーブル。

#### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **データ**メニューの  **データ ソースの**します。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。

3.  **データ ソースの種類を選択**画面で、**データベース**、し、**次**します。

4.  **データ接続の選択**画面は、次のいずれか。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックスし、Northwind データベースへの接続を作成します。

5.  データベースにパスワードが必要な場合は、機密データを含めるしを選択するオプションを選択**次**します。

6.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**します。

7.  **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。

8.  選択、`Customers`と`Orders`テーブル、および選択**完了**します。

     **NorthwindDataSet**プロジェクトに追加されて、`Customers`と`Orders`に表示されるテーブル、**データ ソース**ウィンドウ。

## <a name="add-controls-to-the-form"></a>コントロールをフォームに追加します。
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウから、フォームにします。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows フォーム上のコントロールのバインドをデータを作成するには

-   **データソース**ウィンドウで、展開、**顧客**ノード。

-   メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウ**Form1**。

     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 `CustomersTableAdapter`、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

-   関連するドラッグ**注文**ノード (main ではない**注文**が関連する子テーブル ノードの下、 **Fax**列) 下のフォームに、 **CustomersDataGridView**します。

     <xref:System.Windows.Forms.DataGridView> がフォームに表示されます。 `OrdersTableAdapter`と<xref:System.Windows.Forms.BindingSource>コンポーネント トレイに表示されます。

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions アセンブリへの参照を追加します。
 トランザクションは、<xref:System.Transactions> 名前空間を使用します。 System.Transactions アセンブリへのプロジェクト参照は既定で追加されないため、手動で追加する必要があります。

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions の DLL ファイルへの参照を追加するには

1.  **プロジェクト**メニューの **参照の追加**します。

2.  選択**System.Transactions** (上、 **.NET** ] タブ)、し、[ **[ok]** します。

     参照を**System.Transactions**プロジェクトに追加されます。

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator の SaveItem ボタンのコードを変更します。
 既定でコードを追加、フォーム上にドロップされた最初のテーブルの`click`のボタンでは、保存のイベント、<xref:System.Windows.Forms.BindingNavigator>します。 追加テーブルを更新する場合は、手動でコードを追加する必要があります。 このチュートリアルでは、リファクタリング、既存のコードをファイルから保存ボタンの click イベント ハンドラー。 また、行が追加または削除する必要があるかどうかに基づいて、特定の更新機能を提供するメソッドを作成します。

#### <a name="to-modify-the-auto-generated-save-code"></a>自動生成された保存コードを変更するには

1.  選択、**保存**のボタンでは、 **CustomersBindingNavigator** (フロッピー ディスクのアイコンのボタン)。

2.  `CustomersBindingNavigatorSaveItem_Click` メソッドを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

関連するデータへの変更を解決する順序は次のとおりです。

-   子レコードを削除します。 (この場合、レコードを削除、`Orders`テーブルです)。

-   親レコードを削除します。 (この場合、レコードを削除、`Customers`テーブルです)。

-   親レコードを挿入します。 (この場合は、内のレコードを挿入、`Customers`テーブルです)。

-   子レコードを挿入します。 (この場合は、内のレコードを挿入、`Orders`テーブルです)。

#### <a name="to-delete-existing-orders"></a>既存の注文を削除するには

-   次の追加`DeleteOrders`メソッドを**Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

#### <a name="to-delete-existing-customers"></a>既存の顧客を削除するには

-   次の追加`DeleteCustomers`メソッドを**Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

#### <a name="to-add-new-customers"></a>新規顧客を追加するには

-   次の追加`AddNewCustomers`メソッドを**Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

#### <a name="to-add-new-orders"></a>新規注文を追加するには

-   次の追加`AddNewOrders`メソッドを**Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>アプリケーションの実行

#### <a name="to-run-the-application"></a>アプリケーションを実行するには

-   選択**F5**アプリケーションを実行します。

## <a name="see-also"></a>関連項目

- [方法: トランザクションを使用してデータを保存](../data-tools/save-data-by-using-a-transaction.md)
- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)