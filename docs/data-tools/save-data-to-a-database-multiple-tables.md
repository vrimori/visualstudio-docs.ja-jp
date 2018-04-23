---
title: データベース (複数のテーブル) にデータを保存します。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5cb987da516c295ea1b3a5b203a1739a70705ae8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="save-data-to-a-database-multiple-tables"></a>データベース (複数のテーブル) にデータを保存します。
アプリケーション開発における最も一般的なシナリオの 1 つに、Windows アプリケーションのフォームにデータを表示して編集し、更新したデータをデータベースに返送する操作があります。 このチュートリアルでは、2 つの関連するテーブルのデータを表示するフォームを作成し、レコードを編集して変更内容をデータベースに保存する方法を示します。 この例では、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルを使用します。

 アプリケーション内のデータをデータベースに保存するには、TableAdapter の `Update` メソッドを呼び出します。 テーブルをドラッグすると、**データソース**ウィンドウからフォーム、データを保存するために必要なコードには自動的に追加します。フォームに追加される他のテーブルでは、このコードを手動で追加が必要です。 ここでは、複数のテーブルから更新を保存するコードを追加する手順を示します。

> [!NOTE]
>  アクティブな設定または使用しているエディションによっては、ヘルプに記載されているダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

 このチュートリアルでは、以下のタスクを行います。

-   新たに作成する**Windows フォーム アプリケーション**プロジェクト。

-   使用してアプリケーションでのデータ ソースの構成の作成と、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)です。

-   内の項目のコントロールの設定、[データ ソース ウィンドウ](add-new-data-sources.md)します。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。

-   項目をドラッグしてデータ バインド コントロールの作成、**データソース**ウィンドウからフォームにします。

-   データセット内の各テーブル内のいくつかのレコードを変更します。

-   データセット内の更新されたデータをデータベースに返送するコードを変更します。

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
 作成するには、まず、 **Windows フォーム アプリケーション**です。 この手順では省略可能なは、プロジェクトに名前を割り当てるが名前を付けますが、後で、プロジェクトを保存するため。

#### <a name="to-create-the-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.

2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**UpdateMultipleTablesWalkthrough**を選択し**OK**です。

     **UpdateMultipleTablesWalkthrough**プロジェクトが作成され、追加**ソリューション エクスプ ローラー**です。

## <a name="create-the-data-source"></a>データ ソースを作成します。
 この手順を使用して、Northwind データベースからデータ ソースを作成、**データ ソース構成ウィザード**です。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースの設定の詳細については、次を参照してください。[する方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)です。

#### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **データ**メニューの **データ ソースの表示**です。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**です。

3.  **データ ソースの種類を選択**画面で、**データベース**、し、**次**です。

4.  **データ接続の選択**画面は、次のいずれか。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   選択**新しい接続**を開くには、**接続接続の追加/変更** ダイアログ ボックス。

5.  データベースは、パスワードを必要とする場合は、デリケートなデータを含めるしを選択するオプションを選択**次**です。

6.  **接続文字列をアプリケーション構成ファイルに保存** **次へ**です。

7.  **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。

8.  選択、**顧客**と**注文**テーブル、および選択**完了**です。

     **NorthwindDataSet**をプロジェクトに追加された、テーブルに表示されると、**データ ソース**ウィンドウです。

## <a name="set-the-controls-to-be-created"></a>作成するコントロールを設定します。
 このチュートリアルでは、内のデータ、`Customers`テーブルは、**詳細**レイアウトの個々 のコントロールにデータが表示されます。 データ、`Orders`テーブルは、**グリッド**レイアウトで表示される、<xref:System.Windows.Forms.DataGridView>コントロール。

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>[データ ソース] ウィンドウの項目にドロップ タイプを設定するには

1.  **データソース**ウィンドウで、展開、**顧客**ノード。

2.  **顧客**ノードで、選択**詳細**のコントロールを変更するコントロール リストから、**顧客**テーブルを個別のコントロールです。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。

## <a name="create-the-data-bound-form"></a>データ バインド フォームを作成します。
 項目をドラッグして、データ バインド コントロールを作成することができます、**データソース**ウィンドウからフォームにします。

#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには

1.  メインをドラッグして**顧客**ノードから、**データ ソース**ウィンドウ**Form1**です。

     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 `CustomersTableAdapter`、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

2.  関連するドラッグ**Orders**からノード、**データ ソース** ウィンドウ**Form1**です。

    > [!NOTE]
    >  関連する**Orders**ノードが下にある、 **Fax**列の子ノードです、**顧客**ノード。

     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 `OrdersTableAdapter`と<xref:System.Windows.Forms.BindingSource>コンポーネント トレイに表示されます。

## <a name="add-code-to-update-the-database"></a>データベースを更新するコードを追加します。
 データベースを更新するには呼び出すことによって、`Update`のメソッド、**顧客**と**注文**Tableadapter。 既定では、イベント ハンドラーを**保存**のボタン、<xref:System.Windows.Forms.BindingNavigator>データベースへの更新を送信するフォームのコードに追加されます。 この手順では、正しい順序で更新を送信するコードを変更します。これにより、参照整合性エラーが発生する可能性がなくなります。 また、Update 呼び出しを try-catch ブロックにラップして、エラー処理も実装します。 アプリケーションの要件に適合するようにコードを変更できます。

> [!NOTE]
>  わかりやすくするため、このチュートリアルでは、トランザクションは使用されません。ただし、2 つを更新する、または以上の関連テーブル、トランザクション内のすべての更新ロジックを含めます。 トランザクションは、すべての変更がコミットされるまで、データベースに対するすべての関連する変更が成功したことを保証するプロセスです。 詳細については、次を参照してください。[トランザクションと同時実行](/dotnet/framework/data/adonet/transactions-and-concurrency)です。

#### <a name="to-add-update-logic-to-the-application"></a>アプリケーションに更新ロジックを追加するには

1.  選択、**保存**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>です。コード エディターが開き、`bindingNavigatorSaveItem_Click`イベント ハンドラー。

2.  イベント ハンドラーのコードを、関連する TableAdapter の `Update` メソッドを呼び出すコードに置き換えます。 次のコードは、最初に、各 <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState.Deleted>、<xref:System.Data.DataRowState.Added>、および <xref:System.Data.DataRowState.Modified>) の更新済み情報を保持する 3 つの一時的なデータ テーブルを作成します。 更新プログラムは、正しい順序で実行されます。 コードは、次のようになります。

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>アプリケーションをテストする

#### <a name="to-test-the-application"></a>アプリケーションをテストするには

1.  選択**f5 キーを押して**です。

2.  各テーブルの 1 つ以上のレコードのデータを変更します。

3.  選択、**保存**ボタンをクリックします。

4.  データベースの値をチェックし、変更が保存されたことを確認します。


## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)