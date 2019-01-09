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
ms.workload:
- data-storage
ms.openlocfilehash: 88590c49938ef61344a1092dffb42565a81755d1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920142"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect メソッドを使用してデータを保存する

このチュートリアルでは、TableAdapter の DBDirect メソッドを使用して、データベースに対して直接 SQL ステートメントを実行するための詳細な手順を提供します。 TableAdapter の DBDirect メソッドを使用すると、データベースの更新をきめ細かいレベルで制御できます。 それらを使用するには個別に呼び出すことによって、特定の SQL ステートメントおよびストアド プロシージャを実行する`Insert`、 `Update`、および`Delete`アプリケーションに必要なメソッド (オーバー ロードされたのではなく`Update`更新プログラムを実行するメソッド、INSERT、および 1 回の呼び出しですべての DELETE ステートメント)。

このチュートリアルでは、次の作業を行う方法について説明します。

-   新しい **Windows フォーム アプリケーション**を作成します。

-   作成し、構成を含むデータセット、[データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)します。

-   **[データ ソース]** ウィンドウから項目をドラッグしたときにフォーム上に作成されるコントロールを選択します。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。

-   **[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド フォームを作成します。

-   直接データベースにアクセスし、挿入、更新、および削除を実行するメソッドを追加します。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-a-windows-forms-application"></a>Windows フォーム アプリケーションを作成する

作成するには、まず、 **Windows フォーム アプリケーション**します。

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**TableAdapterDbDirectMethodsWalkthrough**を選び、 **OK**。

     **TableAdapterDbDirectMethodsWalkthrough** プロジェクトが作成されて**ソリューション エクスプローラー**に追加されます。

## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。

この手順では、**データ ソース構成ウィザード**を使用して、Northwind サンプル データベースの `Region` テーブルに基づいてデータ ソースを作成します。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースの設定の詳細については、次を参照してください。[方法。サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)します。

### <a name="to-create-the-data-source"></a>データ ソースを作成するには

1. **データ**メニューの  **データ ソースの**します。

   **[データ ソース]** ウィンドウが開きます。

2. **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成ウィザード**を起動します。

3. **データ ソースの種類を選択**画面で、**データベース**、し、**次**します。

4. **データ接続の選択**画面で、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   **[新しい接続]** を選択して **[接続の追加] または [接続の変更]** ダイアログ ボックスを表示します。

5. データベースにパスワードが必要な場合は、機密データを含めるしを選択するオプションを選択**次**します。

6. **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**します。

7. **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。

8. 選択、`Region`テーブルし、**完了**します。

     プロジェクトに **NorthwindDataSet** が追加され、**[データ ソース]** ウィンドウに `Region` テーブルが表示されます。

## <a name="add-controls-to-the-form-to-display-the-data"></a>データを表示するフォームにコントロールを追加します。

**[データ ソース]** ウィンドウからフォームに項目をドラッグして、データ バインド コントロールを作成します。

Windows フォームにデータ バインド コントロールを作成するには、メインをドラッグ**リージョン**ノードから、**データソース**ウィンドウから、フォームにします。

レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 `RegionTableAdapter`、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。

### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>個々の TableAdapter DbDirect メソッドを呼び出すボタンを追加するには

1. **ツールボックス**から 3 つの <xref:System.Windows.Forms.Button> コントロールを **RegionDataGridView** の下の **Form1** にドラッグします。

2. 各ボタンの **[名前]** および **[テキスト]** プロパティを設定します。

    |name|テキスト|
    |----------|----------|
    |`InsertButton`|**[挿入]**|
    |`UpdateButton`|**更新**|
    |`DeleteButton`|**削除**|

### <a name="to-add-code-to-insert-new-records-into-the-database"></a>データベースに新しいレコードを挿入するコードを追加するには

1. 選択**InsertButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2. `InsertButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#1](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_1.vb)]
     [!code-csharp[VbRaddataSaving#1](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_1.cs)]

### <a name="to-add-code-to-update-records-in-the-database"></a>データベースのレコードを更新するコードを追加するには

1. **[UpdateButton]** をダブルクリックして、クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2. `UpdateButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#2](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_2.vb)]
     [!code-csharp[VbRaddataSaving#2](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_2.cs)]

### <a name="to-add-code-to-delete-records-from-the-database"></a>データベースからレコードを削除するコードを追加するには

1. 選択**DeleteButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。

2. `DeleteButton_Click` イベント ハンドラーを次のコードで置き換えます。

     [!code-vb[VbRaddataSaving#3](../data-tools/codesnippet/VisualBasic/save-data-with-the-tableadapter-dbdirect-methods_3.vb)]
     [!code-csharp[VbRaddataSaving#3](../data-tools/codesnippet/CSharp/save-data-with-the-tableadapter-dbdirect-methods_3.cs)]

## <a name="run-the-application"></a>アプリケーションの実行

-   選択**F5**アプリケーションを実行します。

-   選択、**挿入**ボタンをクリックし、新しいレコードがグリッドに表示されることを確認します。

-   選択、 **Update**ボタンをクリックし、グリッドのレコードが更新されることを確認します。

-   選択、**削除**ボタンをクリックし、グリッドからレコードが削除されることを確認します。

## <a name="next-steps"></a>次の手順

アプリケーションの要件によっては、データ バインド フォームの作成後に実行する場合があります。 このチュートリアルで行うことができる拡張には次のものがあります。

-   フォームに検索機能を追加します。

-   **[データ ソース]** ウィンドウの **[ウィザードで DataSet を構成]** を選択して、データセットにテーブルを追加します。 関連するコードをフォームにドラッグすることによって、関連するデータを表示するコントロールを追加できます。 詳細については、次を参照してください。[データセットのリレーションシップ](relationships-in-datasets.md)します。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)