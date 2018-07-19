---
title: 同時実行例外を処理する
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b7895a15dcc7536ee29317a2c02546bf125a6b4a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117200"
---
# <a name="handle-a-concurrency-exception"></a>同時実行例外を処理する
2 人のユーザーが同じデータベースの同じデータを同時に変更しようとすると、同時実行例外 (<xref:System.Data.DBConcurrencyException>) が発生します。 このチュートリアルをキャッチする方法を説明する Windows アプリケーションを作成、<xref:System.Data.DBConcurrencyException>エラーの原因となった行を見つけて、それを処理する方法の戦略について説明します。

 ここでは次の手順を実行します。

1.  新しい **Windows フォーム アプリケーション プロジェクト**を作成します。

2.  Northwind `Customers` テーブルに基づいて、新しいデータセットを作成します。

3.  データを表示する <xref:System.Windows.Forms.DataGridView> を備えたフォームを作成します。

4.  Northwind データベースの `Customers` テーブルからデータセットにデータを読み込みます。

5.  使用して、**テーブル データの表示**機能**サーバー エクスプ ローラー**にアクセスする、`Customers`テーブルのデータと変更レコード。

6.  別の値に同じレコードを変更、データセットを更新および発生している同時実行エラーが発生すると、データベースへの変更の書き込みを試行します。

7.  エラーをキャッチし、続行し、データベースを更新するかどうかを確認するように、レコードの異なるバージョンを表示または更新をキャンセルします。

## <a name="prerequisites"></a>前提条件
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (SQL Server オブジェクト エクスプ ローラーがの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

> [!NOTE]
>  アクティブな設定または使用しているエディションによって、ヘルプの説明から、ダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する
 チュートリアルを開始するには、新しい Windows フォーム アプリケーションを作成します。

#### <a name="to-create-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、 **Windows フォーム アプリ**プロジェクトの種類。

4. プロジェクトに名前を**ConcurrencyWalkthrough**を選び、 **OK**。

     **ConcurrencyWalkthrough**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**、し、デザイナーで新しいフォームが開きます。

## <a name="create-the-northwind-dataset"></a>Northwind データセットを作成します。
 このセクションでという名前のデータセットを作成する`NorthwindDataSet`します。

#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet を作成するには

1.  **データ**] メニューの [選択**新しいデータの追加ソース**します。

     [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)が開きます。

2.  **データ ソースの種類を選択**画面で、**データベース**します。

3.  利用可能な接続の一覧から Northwind サンプル データベースへの接続を選択します。 接続が接続の一覧で使用できない場合は、選択**新しい接続**します。

    > [!NOTE]
    >  ローカル データベース ファイルに接続する場合は、選択**いいえ**されたら、ファイルをプロジェクトに追加したい場合。

4.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**します。

5.  展開、**テーブル**ノード、`Customers`テーブル。 既定のデータセット名は、`NorthwindDataSet` です。

6.  選択**完了**にデータセットをプロジェクトに追加します。

## <a name="create-a-data-bound-datagridview-control"></a>データ バインド DataGridView コントロールを作成します。
 このセクションで作成、<xref:System.Windows.Forms.DataGridView>をドラッグして、**顧客**から項目、**データ ソース**ウィンドウから、Windows フォームにします。

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Customers テーブルにバインドする DataGridView コントロールを作成するには

1.  **データ**] メニューの [選択 **[データ ソースの**を開く、**データ ソース] ウィンドウ**します。

2.  **データソース**ウィンドウで、展開、 **NorthwindDataSet**ノード、および選択し、**顧客**テーブル。

3.  テーブル ノードで、下向きの矢印を選択し、 **DataGridView**ドロップダウン リストでします。

4.  テーブルをフォームの空の領域にドラッグします。

     A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`CustomersDataGridView`と<xref:System.Windows.Forms.BindingNavigator>という`CustomersBindingNavigator`にバインドされているフォームに追加されます、<xref:System.Windows.Forms.BindingSource>します。 これは、さらにバインドされている、`Customers`テーブルに、`NorthwindDataSet`します。

## <a name="test-the-form"></a>フォームをテストします。
 フォームをテストして、ここまでの設定が期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

1.  選択**F5**アプリケーションを実行します。

     フォームが表示されます、<xref:System.Windows.Forms.DataGridView>からのデータが格納されるコントロール、`Customers`テーブル。

2.  **デバッグ**メニューの [**デバッグの停止]** します。

## <a name="handle-concurrency-errors"></a>同時実行エラーの処理
 エラーを処理する方法は、アプリケーションを制御する特定のビジネス ルールに依存します。 このチュートリアルでは、同時実行エラーを処理する方法の例として、次の方法を使用します。

 アプリケーションでは、レコードの 3 つのバージョンと、ユーザーが表示されます。

-   データベースの現在のレコード

-   データセットに読み込まれた元のレコード

-   データセットの変更の提案

ユーザーに提案されたバージョンでは、データベースを上書きするか、または更新をキャンセルし、データベースから新しい値でデータセットを更新できます。

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>同時実行エラーを処理できるようにするには

1.  カスタム エラー ハンドラーの作成

2.  ユーザーに対する選択肢の表示

3.  ユーザーの応答の処理

4.  更新の再送、またはデータセット内のデータのリセット

### <a name="add-code-to-handle-the-concurrency-exception"></a>同時実行例外を処理するコードを追加します。
 更新プログラムを実行しようとすると、例外が発生、一般に、発生した例外によって提供される情報で何か操作します。

 このセクションでは、データベースを更新しようとするコードを追加します。 いずれかの処理も<xref:System.Data.DBConcurrencyException>する可能性がありますが発生すると、その他の例外とします。

> [!NOTE]
>  `CreateMessage`と`ProcessDialogResults`メソッドは、このチュートリアルの後半で追加されます。

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>同時実行エラー用のエラー処理を追加するには

1.  `Form1_Load` メソッドの下に次のコードを追加します。

     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2.  次のように `CustomersBindingNavigatorSaveItem_Click` メソッドを `UpdateDatabase` メソッドの呼び出しに置き換えます。

     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>ユーザーに対する選択肢を表示します。
 上のコードにより `CreateMessage` プロシージャが呼び出され、ユーザーにエラー情報が表示されます。 このチュートリアルでは、ユーザーに異なるバージョンのレコードを表示するのにメッセージ ボックスを使用します。 これにより、ユーザーが変更で、レコードを上書きしたり、編集をキャンセルするかどうかを選択できます。 ユーザーがメッセージ ボックスのオプションを選択する (ボタンをクリックする) と、`ProcessDialogResult` メソッドに応答が渡されます。

##### <a name="to-create-the-message-to-display-to-the-user"></a>ユーザーに表示するメッセージを作成するには

-   次のコードを追加して、メッセージを作成、**コード エディター**します。 このコードは、`UpdateDatabase` メソッドの下に入力します。

     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>ユーザーの応答を処理します。
 メッセージ ボックスに、ユーザーの応答を処理するコードも必要です。 、提案された変更で、データベースの現在のレコードを上書きまたはローカルの変更を破棄し、現在、データベース内にあるレコードをデータ テーブルを更新することもできます。 ユーザーが選択した場合**はい**、<xref:System.Data.DataTable.Merge%2A>メソッドを呼び出すと、 *preserveChanges*引数に設定`true`します。 これにより、レコードの元のバージョンがデータベース内のレコードと一致するように成功すると、ある更新の試行です。

##### <a name="to-process-the-user-input-from-the-message-box"></a>メッセージ ボックスからのユーザーの入力を処理するには

-   前のセクションで追加されたコードの下の次のコードを追加します。

     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>フォームをテストします。
 フォームをテストして、期待どおりに動作することを確認します。 同時実行制御違反をシミュレートするには、NorthwindDataSet にデータを読み込んだ後、データベース内のデータを変更します。

#### <a name="to-test-the-form"></a>フォームをテストするには

1.  選択**F5**アプリケーションを実行します。

2.  フォームが表示されたら、実行を継続したまま Visual Studio IDE に切り替えます。

3.  **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**します。

4.  **サーバー エクスプ ローラー**、接続、アプリケーションを使用して、順に展開を展開、**テーブル**ノード。

5.  右クリックし、**顧客**テーブルし、**テーブル データの表示**します。

6.  最初のレコード (`ALFKI`) 変更`ContactName`に`Maria Anders2`します。

    > [!NOTE]
    >  別の行に移動し、変更をコミットします。

7.  `ConcurrencyWalkthrough` の実行中のフォームに切り替えます。

8.  フォームの最初のレコードで (`ALFKI`)、変更`ContactName`に`Maria Anders1`します。

9. 選択、**保存**ボタンをクリックします。

     同時実行エラーが発生し、メッセージ ボックスが表示されます。

10. 選択**いいえ**更新をキャンセルし、現在、データベース内にある値でデータセットを更新します。 選択**はい**データベースに指定された値を書き込みます。

## <a name="see-also"></a>関連項目

- [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)