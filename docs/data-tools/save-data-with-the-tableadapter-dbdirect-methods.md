---
title: TableAdapter DBDirect メソッドを使用してデータを保存する
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 68842160d3ad7bf7e96d22f58607866c34f9ceb5
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747548"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect メソッドを使用してデータを保存する
このチュートリアルでは、TableAdapter の DBDirect メソッドを使用して、データベースに対して直接 SQL ステートメントを実行する詳細な手順を提供します。 TableAdapter の DBDirect メソッドは、細かいレベル、データベースの更新で制御を提供します。 それらを使用して、個別に呼び出すことによって、特定の SQL ステートメントおよびストアド プロシージャを実行することができます`Insert`、 `Update`、および`Delete`アプリケーションで必要に応じてメソッド (オーバー ロードされたのではなく`Update`更新プログラムを実行するメソッド、INSERT、および DELETE のステートメントすべて 1 つの呼び出しで)。

 このチュートリアルでは、次の作業を行う方法について説明します。

-   新しい**Windows フォーム アプリケーション**です。

-   作成および構成を含むデータセット、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)です。

-   コントロールから項目をドラッグしたときに、フォーム上に作成する場合にオン、**データソース**ウィンドウです。 詳細については、次を参照してください。[セットのデータ ソース ウィンドウからドラッグしたときに作成する制御](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)です。

-   項目をドラッグして、データ バインド フォームを作成、**データソース**ウィンドウからフォームにします。

-   直接データベースにアクセスし、挿入、更新、および削除を実行するメソッドを追加するには.

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成します。
 作成するには、まず、 **Windows フォーム アプリケーション**です。

#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.

2. いずれかを展開**Visual c#** または**Visual Basic**左側のペインでを選択し、 **Windows デスクトップ**です。

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**TableAdapterDbDirectMethodsWalkthrough**を選択し**OK**です。

     **TableAdapterDbDirectMethodsWalkthrough**プロジェクトが作成され、追加**ソリューション エクスプ ローラー**です。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。
 このステップでは、**データ ソース構成ウィザード**に基づいてデータ ソースを作成する、 `Region` Northwind サンプル データベース内のテーブルです。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースの設定の詳細については、次を参照してください。[する方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)です。

#### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1.  **データ**メニューの **データ ソースの表示**です。

2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**です。

3.  **データ ソースの種類を選択**画面で、**データベース**、し、**次**です。

4.  **データ接続の選択**画面で、次のいずれかの操作します。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   選択**新しい接続**を起動する、**接続接続の追加/変更** ダイアログ ボックス。

5.  データベースは、パスワードを必要とする場合は、デリケートなデータを含めるしを選択するオプションを選択**次**です。

6.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**です。

7.  **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。

8.  選択、`Region`テーブルをクリックし **完了**です。

     **NorthwindDataSet**プロジェクトに追加され、`Region`テーブルに表示されます、**データ ソース**ウィンドウです。

## <a name="add-controls-to-the-form-to-display-the-data"></a>データを表示するフォームにコントロールを追加します。
 項目をドラッグして、データ バインド コントロールを作成、**データソース**ウィンドウからフォームにします。

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>データの作成にバインド Windows フォーム コントロール

-   メインのドラッグ**地域**ノードから、**データ ソース**ウィンドウからフォームにします。

     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 `RegionTableAdapter`、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>個々の TableAdapter DbDirect メソッドを呼び出すボタンを追加するには

1.  3 つをドラッグして<xref:System.Windows.Forms.Button>から制御、**ツールボックス**に**Form1** (以下、 **RegionDataGridView**)。

2.  以下の設定を**名前**と**テキスト**各ボタンのプロパティです。

    |name|テキスト|
    |----------|----------|
    |`InsertButton`|**[挿入]**|
    |`UpdateButton`|**更新**|
    |`DeleteButton`|**削除**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>データベースに新しいレコードを挿入するコードを追加するには

1.  選択**InsertButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2.  `InsertButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>データベースのレコードを更新するコードを追加するには

1.  ダブルクリックして、 **UpdateButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2.  `UpdateButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>データベースからレコードを削除するコードを追加するには

1.  選択**DeleteButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2.  `DeleteButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>アプリケーションの実行

#### <a name="to-run-the-application"></a>アプリケーションを実行するには

-   選択**f5 キーを押して**アプリケーションを実行します。

-   選択、**挿入**ボタンをクリックし、新しいレコードをグリッドに表示されることを確認します。

-   選択、**更新**ボタンをクリックし、グリッドで、レコードが更新されることを確認します。

-   選択、**削除**ボタンをクリックし、グリッドからレコードが削除されることを確認します。

## <a name="next-steps"></a>次の手順
 アプリケーションの要件によっては、データ バインド フォームの作成後に実行する可能性があります。 このチュートリアルで行うことができる拡張には次のものがあります。

-   フォームに検索機能を追加します。

-   選択して、データセットにテーブルを追加**構成ウィザードで DataSet を**内から、**データソース**ウィンドウです。 関連するコードをフォームにドラッグすることによって、関連するデータを表示するコントロールを追加できます。 詳細については、次を参照してください。[データセットのリレーションシップ](relationships-in-datasets.md)です。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)