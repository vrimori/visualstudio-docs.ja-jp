---
title: 同時実行例外の処理 |Microsoft ドキュメント
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 816d00c4d2c08ba5122b0d9a3f6091937243270a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="handle-a-concurrency-exception"></a>同時実行例外を処理します。
2 人のユーザーが同じデータベースの同じデータを同時に変更しようとすると、同時実行例外 (<xref:System.Data.DBConcurrencyException>) が発生します。 このチュートリアルをキャッチする方法を示しています。 Windows アプリケーションを作成、 <xref:System.Data.DBConcurrencyException>、エラーが発生した行を見つけて、その処理方法の戦略について説明します。  
  
 ここでは次の手順を実行します。  
  
1.  新しい **Windows フォーム アプリケーション プロジェクト**を作成します。  
  
2.  Northwind `Customers` テーブルに基づいて、新しいデータセットを作成します。  
  
3.  データを表示する <xref:System.Windows.Forms.DataGridView> を備えたフォームを作成します。  
  
4.  Northwind データベースの `Customers` テーブルからデータセットにデータを読み込みます。  
  
5.  使用して、**テーブル データの表示**機能**サーバー エクスプ ローラー**にアクセスする、`Customers`テーブルのデータと、レコードを変更します。  
  
6.  別の値に同じレコードを変更、データセットを更新および発生している同時実行エラーが発生すると、データベースに対する変更を作成しようとしてください。  
  
7.  エラーをキャッチし、操作を継続してデータベースを更新するか、または更新をキャンセルするかを判断できるように、レコードの異なるバージョンを表示します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。  
  
1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。  
  
2.  次の手順に従って、Northwind サンプル データベースをインストールします。  

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.  

       クエリ エディター ウィンドウが開きます。  

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。  

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。  

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。  
  
> [!NOTE]
>  アクティブな設定または使用しているエディションによっては、ヘルプに記載されているダイアログ ボックスとメニュー コマンドが表示が異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
## <a name="create-a-new-project"></a>新しいプロジェクトを作成する  
 新しい Windows フォーム アプリケーションを作成してチュートリアルを開始します。  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには  
  
1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.  
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**ConcurrencyWalkthrough**を選択し**OK**です。 
  
     **ConcurrencyWalkthrough**プロジェクトが作成され、追加**ソリューション エクスプ ローラー**、し、デザイナーで新しいフォームが開きます。  
  
## <a name="create-the-northwind-dataset"></a>Northwind データセットを作成します。  
 このセクションでは、という名前のデータセットを作成`NorthwindDataSet`です。  
  
#### <a name="to-create-the-northwinddataset"></a>NorthwindDataSet を作成するには  
  
1.  **データ** メニューの 選択**新しいデータ ソース**です。  
  
     [データ ソース構成ウィザード](../data-tools/media/data-source-configuration-wizard.png)が開きます。  
  
2.  **データ ソースの種類を選択して**画面で、**データベース**です。  
  
3.  利用可能な接続の一覧から、Northwind サンプル データベースへの接続を選択します。 接続が接続の一覧で使用できない場合は、選択**新規接続**  
  
    > [!NOTE]
    >  ローカル データベース ファイルに接続する場合は、選択**いいえ**されたらファイルをプロジェクトに追加したい場合。  
  
4.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**です。  
  
5.  展開して、**テーブル**ノードを選択、`Customers`テーブル。 既定のデータセット名は、`NorthwindDataSet` です。  
  
6.  選択**完了**データセットをプロジェクトに追加します。  
  
## <a name="create-a-data-bound-datagridview-control"></a>データ バインド DataGridView コントロールを作成します。  
 このセクションで作成、<xref:System.Windows.Forms.DataGridView>をドラッグして、**顧客**項目を**データ ソース**ウィンドウから、Windows フォームにします。  
  
#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Customers テーブルにバインドする DataGridView コントロールを作成するには  
  
1.  **データ** メニューの 選択**データ ソースの表示**を開くには、**データ ソース ウィンドウ**します。  
  
2.  **データ ソース**ウィンドウで、展開、 **NorthwindDataSet**ノードをクリックし、**顧客**テーブル。  
  
3.  テーブル ノードの下向きの矢印を選択し、選択**DataGridView**ドロップダウン リストでします。  
  
4.  テーブルをフォームの空の領域にドラッグします。  
  
     A<xref:System.Windows.Forms.DataGridView>という名前のコントロール`CustomersDataGridView`と<xref:System.Windows.Forms.BindingNavigator>という`CustomersBindingNavigator`にバインドされているフォームに追加されます、<xref:System.Windows.Forms.BindingSource>です。これは、有効にするにバインドされている、`Customers`テーブルに、`NorthwindDataSet`です。  
  
## <a name="test-the-form"></a>フォームをテストします。  
 フォームをテストして、ここまでの設定が期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
1.  選択**f5 キーを押して**アプリケーションを実行するには  
  
     フォームに表示される、<xref:System.Windows.Forms.DataGridView>からのデータで塗りつぶされているコントロール、`Customers`テーブル。  
  
2.  **デバッグ**メニューの [**デバッグの停止]**です。  
  
## <a name="handle-concurrency-errors"></a>同時実行エラーを処理します。  
 エラーを処理する方法は、アプリケーションを制御する特定のビジネス ルールによって異なります。 このチュートリアルで、次の戦略を使用して、同時実行エラーを処理する方法の例とします。  
  
 アプリケーションでは、次の 3 つのバージョン レコードのユーザーが表示されます。  
  
-   データベースの現在のレコード  
  
-   元のレコードはデータセットに読み込まれる  
  
-   データセットの提案された変更  
  
ユーザーが提案されたバージョンは、データベースを上書きするか、または更新をキャンセルし、データベースから新しい値でデータセットを更新することです。  
  
#### <a name="to-enable-the-handling-of-concurrency-errors"></a>同時実行エラーを処理できるようにするには  
  
1.  カスタム エラー ハンドラーの作成  
  
2.  ユーザーに対する選択肢の表示  
  
3.  ユーザーの応答の処理  
  
4.  更新の再送、またはデータセット内のデータのリセット  
  
### <a name="add-code-to-handle-the-concurrency-exception"></a>同時実行例外を処理するコードを追加します。  
 更新を実行しようとすると、例外が発生、一般にするは、発生した例外によって提供される情報で操作を行います。  
  
 このセクションでは、データベースを更新しようとするコードを追加します。 いずれかの処理も<xref:System.Data.DBConcurrencyException>生成可能性がある取得、およびその他の例外。  
  
> [!NOTE]
>  このチュートリアルの後半で、`CreateMessage` メソッドと `ProcessDialogResults` メソッドを追加します。  
  
##### <a name="to-add-error-handling-for-the-concurrency-error"></a>同時実行エラー用のエラー処理を追加するには  
  
1.  `Form1_Load` メソッドの下に次のコードを追加します。  
  
     [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
     [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]  
  
2.  次のように `CustomersBindingNavigatorSaveItem_Click` メソッドを `UpdateDatabase` メソッドの呼び出しに置き換えます。  
  
     [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
     [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]  
  
### <a name="display-choices-to-the-user"></a>ユーザーに対する選択肢を表示します。  
 上のコードにより `CreateMessage` プロシージャが呼び出され、ユーザーにエラー情報が表示されます。 このチュートリアルでは、ユーザーに異なるバージョンのレコードを表示するのにメッセージ ボックスを使用します。 これにより、ユーザーの変更によって、レコードを上書きするか、編集をキャンセルするかどうかを選択できます。 ユーザーがメッセージ ボックスのオプションを選択する (ボタンをクリックする) と、`ProcessDialogResult` メソッドに応答が渡されます。  
  
##### <a name="to-create-the-message-to-display-to-the-user"></a>ユーザーに表示するメッセージを作成するには  
  
-   次のコードを追加することによって、メッセージを作成、**コード エディター**です。 このコードは、`UpdateDatabase` メソッドの下に入力します。  
  
     [!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
     [!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]  
  
### <a name="process-the-users-response"></a>ユーザーの応答を処理します。  
 メッセージ ボックスに、ユーザーの応答を処理するコードも必要があります。 オプションは、提案された変更により、データベースの現在のレコードを上書きまたはローカルの変更を破棄して、データベースに現在あるレコードをデータ テーブルを更新するいずれかです。 ユーザーが [はい] を選択した場合、<xref:System.Data.DataTable.Merge%2A>メソッドが呼び出された、 *preserveChanges*引数に設定されて`true`です。 これにより、成功すると、レコードの元のバージョンがデータベース内のレコードと一致するように更新しようとします。  
  
##### <a name="to-process-the-user-input-from-the-message-box"></a>メッセージ ボックスからのユーザーの入力を処理するには  
  
-   前のセクションで追加されたコードの下の次のコードを追加します。  
  
     [!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
     [!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]  
  
## <a name="test-the-form"></a>フォームをテストします。  
 フォームをテストして、期待どおりに動作することを確認します。 同時実行違反をシミュレートするには、NorthwindDataSet にデータを読み込んだ後で、データベースのデータを変更する必要があります。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
1.  選択**f5 キーを押して**アプリケーションを実行します。  
  
2.  フォームが表示されたら、実行を継続したまま Visual Studio IDE に切り替えます。  
  
3.  **ビュー** ] メニューの [選択**サーバー エクスプ ローラー**です。  
  
4.  **サーバー エクスプ ローラー**、アプリケーションを使用して、しの順に展開の接続を展開し、**テーブル**ノード。  
  
5.  右クリックし、**顧客**テーブルをクリックし **テーブル データの表示**です。  
  
6.  最初のレコード (`ALFKI`) 変更`ContactName`に`Maria Anders2`です。  
  
    > [!NOTE]
    >  別の行に移動し、変更をコミットします。  
  
7.  `ConcurrencyWalkthrough` の実行中のフォームに切り替えます。  
  
8.  フォームに最初のレコード (`ALFKI`)、変更`ContactName`に`Maria Anders1`です。  
  
9. 選択、**保存**ボタンをクリックします。  
  
     同時実行エラーが発生し、メッセージ ボックスが表示されます。  
  
10. 選択すると**いいえ**更新をキャンセルし、現在、データベース内にある値でデータセットを更新します。 選択すると**はい**提案された値をデータベースに書き込みます。  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)
