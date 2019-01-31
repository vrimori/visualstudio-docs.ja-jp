---
title: ADO.NET を使用した単純なデータ アプリケーションの作成
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 833f4fba621c41a51adca1368c784df313419f97
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945516"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET を使用した単純なデータ アプリケーションの作成

データベースのデータを処理するアプリケーションの作成では、接続文字列の定義、データの挿入、ストアド プロシージャの実行などの基本的なタスクを実行します。 このトピックでは、Visual c# または Visual Basic および ADO.NET を使用して単純な Windows フォームの「フォーム オーバー データ」アプリケーションからデータベースと対話する方法を検出できます。  すべての .NET データ テクノロジ: LINQ to SQL、および Entity Framework のデータセットを含む-最終的にこの記事で示したものとよく似ている手順を実行します。

この記事では、高速の方法で、データベースからデータを取得する簡単な方法を示します。 を、アプリケーションが自明でない方法でデータを変更し、データベースを更新する必要がある場合は、Entity Framework を使用して、基になるデータの変更をユーザー インターフェイス コントロールを自動的に同期へのデータ バインディングを使用してを検討してください。

> [!IMPORTANT]
> コードをシンプルにするため、運用環境で使用する例外処理は含まれていません。

## <a name="prerequisites"></a>必須コンポーネント

アプリケーションの作成には、次が必要です:

-   Visual Studio

-   SQL Server Express LocalDB。 SQL Server Express LocalDB をお持ちでない場合からをインストール、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)します。

このトピックでする Visual Studio IDE の基本的な機能を使い慣れているとできる Windows フォーム アプリケーションを作成と仮定ボタンと、フォームの他のコントロールを配置するプロジェクトにフォーム コントロール、およびコードの単純なイベントのプロパティの設定を追加します。 完了することをお勧め、これらのタスクを慣れていない場合、 [Visual c# および Visual Basic の概要](../ide/quickstart-visual-basic-console.md)トピックでこのチュートリアルを開始する前にします。

## <a name="set-up-the-sample-database"></a>サンプル データベースを設定する

次の手順に従って、サンプル データベースを作成します。

1. Visual Studio で開く、**サーバー エクスプ ローラー**ウィンドウ。

2. 右クリックして**データ接続**選択**新しい SQL Server データベースの作成**です。

3. **サーバー名**テキスト ボックスに、入力 **(localdb) \mssqllocaldb**します。

4. **新しいデータベース名**テキスト ボックスに、入力**Sales**を選択し、 **OK**します。

     空の**Sales**データベースが作成され、サーバー エクスプ ローラーでデータ接続 ノードに追加します。

5. 右クリックし、 **Sales**データ接続と select**新しいクエリ**します。

     クエリ エディター ウィンドウが開きます。

6. コピー、 [Sales Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql)をクリップボードにします。

7. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

     しばらくすると、クエリの実行が完了し、データベース オブジェクトを作成します。 データベースには、2 つのテーブルが含まれています。顧客と注文です。 これらのテーブル データを含まない初期状態で、作成するアプリケーションを実行するときにデータを追加することができます。 データベースには、次の 4 つのシンプルなストアド プロシージャも含まれています。

## <a name="create-the-forms-and-add-controls"></a>フォームを作成してコントロールを追加する

1. Windows フォーム アプリケーションのプロジェクトを作成し、**SimpleDataApp** という名前を付けます。

    Visual Studio は、**Form1** という名前の空の Windows フォームを含めた、いくつかのファイルとプロジェクトを作成します。

2. 2 つの Windows フォームをプロジェクトに追加し、合計 3 つのフォームに次の名前を付けます。

   -   **ナビゲーション**

   -   **NewCustomer**

   -   **FillOrCancel**

3. 各フォームに、次の図に示されるように、テキスト ボックス、ボタン、および他のコントロールを追加します。 各コントロールに、テーブルを示すプロパティを設定します。

   > [!NOTE]
   > グループ ボックス、およびラベル コントロールは明確性を追加しますが、コードでは使用されません。

   **Navigation フォーム**

   ![ナビゲーション ダイアログ ボックス](../data-tools/media/simpleappnav.png)

|Navigation フォームのコントロール|プロパティ|
| - |----------------|
|ボタン|Name = btnGoToAdd|
|ボタン|Name = btnGoToFillOrCancel|
|ボタン|Name = btnExit|

 **NewCustomer フォーム**

 ![新しい顧客を追加して注文を作成する](../data-tools/media/simpleappnewcust.png)

|NewCustomer フォームのコントロール|プロパティ|
| - |----------------|
|TextBox|Name = txtCustomerName|
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|
|ボタン|Name = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|
|ボタン|Name = btnPlaceOrder|
|ボタン|Name = btnAddAnotherAccount|
|ボタン|Name = btnAddFinish|

 **FillOrCancel フォーム**

 ![注文の入力または取り消し](../data-tools/media/simpleappcancelfill.png)

|FillOrCancel フォームのコントロール|プロパティ|
| - |----------------|
|TextBox|Name = txtOrderID|
|ボタン|Name = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|
|ボタン|Name = btnCancelOrder|
|ボタン|Name = btnFillOrder|
|ボタン|Name = btnFinishUpdates|

## <a name="store-the-connection-string"></a>接続文字列を保存する
 アプリケーションがデータベースの接続を開くとき、アプリケーションは接続文字列にアクセスする必要があります。 各フォームで文字列を手動で入力を回避するで文字列を格納、 *App.config*プロジェクトで、ファイルを開き、メソッドは、アプリケーションのすべてのフォームから呼び出されたときに、文字列を返すメソッドを作成します。

 右クリックし、接続文字列を見つけることができます、 **Sales**内のデータ接続**サーバー エクスプ ローラー**を選択して**プロパティ**します。 検索、 **ConnectionString**プロパティを使用して**Ctrl**+**A**、 **Ctrl**+**C**を選択し、文字列をクリップボードにコピーします。

1.  C# を使用している場合**ソリューション エクスプ ローラー**、展開、**プロパティ**ノードのプロジェクトで開くと、 **Settings.settings**ファイル。
    Visual Basic の場合に使用する場合**ソリューション エクスプ ローラー**、] をクリックして **[すべてのファイル**、展開、 **My Project**ノード、および順に開いて、 **Settings.settings**ファイル。

2.  **名前**列、入力`connString`します。

3.  **型**一覧で、 **(接続文字列)** します。

4.  **スコープ**一覧で、**アプリケーション**します。

5.  **値**列で、(任意の外部の引用符)、なし、接続文字列を入力し、変更を保存します。

> [!NOTE]
> 実際のアプリケーションでは文字列を格納する接続」の説明に従って、安全に[接続文字列と構成ファイル](/dotnet/framework/data/adonet/connection-strings-and-configuration-files)します。

##  <a name="write-the-code-for-the-forms"></a>フォームのコードを記述する

このセクションでは、各フォームの動作の簡単な概要を説明します。 フォーム上のボタンがクリックされたときに、基になるロジックを定義するコードも提供します。

### <a name="navigation-form"></a>Navigation フォーム

Navigation フォームはアプリケーションを実行すると開きます。 **[Add an account]** ボタンは NewCustomer フォームを開きます。 **[Fill or cancel orders]** ボタンは FillOrCancel フォームを開きます。 **[Exit]** ボタンは、アプリケーションを閉じます。

#### <a name="make-the-navigation-form-the-startup-form"></a>Navigation フォームをスタートアップ フォームに設定

C# を使用している場合、**ソリューション エクスプローラー**で **Program.cs** を開き、`Application.Run` の行を `Application.Run(new Navigation());` に変更します。

Visual Basic の場合に使用する場合**ソリューション エクスプ ローラー**、オープン、**プロパティ**ウィンドウで、**アプリケーション**、タブを選び**SimpleDataApp.Navigation**で、**スタートアップ フォーム**一覧。

#### <a name="create-auto-generated-event-handlers"></a>自動生成されたイベント ハンドラーを作成します。

Navigation フォームの空のイベント ハンドラー メソッドを作成するには、3 つのボタンをダブルクリックします。 ボタンのクリック イベントを発生させることができるデザイナー コード ファイルに自動生成されたコードを追加も、ボタンをダブルクリックします。

#### <a name="add-code-for-the-navigation-form-logic"></a>ナビゲーションのフォーム ロジックのコードを追加します。

Navigation フォームのコード ページ、完全なメソッド本体を次の 3 つのボタンをクリックしてイベント ハンドラーに次のコードに示すよう。

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>NewCustomer フォーム

顧客名を入力しを選択し、**アカウントの作成**ボタン、NewCustomer フォームは、お客様のアカウントを作成および SQL Server は、新しい顧客の ID としての ID 値を返します。 金額と注文日を指定して選択、し、新しいアカウントの注文を配置できます、 **Place Order**ボタンをクリックします。

#### <a name="create-auto-generated-event-handlers"></a>自動生成されたイベント ハンドラーを作成します。

空のクリックを作成するそれぞれの 4 つのボタンをダブルクリックして、NewCustomer フォームの各ボタンのイベント ハンドラー。 ボタンのクリック イベントを発生させることができるデザイナー コード ファイルに自動生成されたコードを追加も、ボタンをダブルクリックします。

#### <a name="add-code-for-the-newcustomer-form-logic"></a>NewCustomer フォームのロジックのコードを追加します。

NewCustomer フォームのロジックを完了するには、次の手順に従います。

1. 表示、`System.Data.SqlClient`スコープに名前空間を完全にする必要があるないようには、そのメンバーの名前を修飾します。

     ```csharp
     using System.Data.SqlClient;
     ```
     ```vb
     Imports System.Data.SqlClient
     ```

2. クラスに次のコードに示すように、いくつかの変数とヘルパー メソッドを追加します。

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. 次のコードに示すように、メソッド本体を次の 4 つのボタンをクリック イベント ハンドラーを完了します。

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>FillOrCancel フォーム

FillOrCancel フォームは、注文 ID を入力します をクリックすると、注文を返すクエリを実行、 **Find Order**ボタンをクリックします。 戻された行は読み取り専用なデータ グリッドに表示されます。 注文をキャンセル (X) をマークするには、選択した場合、 **Cancel Order**ボタンをクリック、としてマークできます順序満たした (F) を選択した場合、 **Fill Order**ボタンをクリックします。 選択した場合、 **Find Order**更新された行の表示を再度クリックします。

#### <a name="create-auto-generated-event-handlers"></a>自動生成されたイベント ハンドラーを作成します。

空アイテムの作成ボタンをダブルクリックして FillOrCancel フォームに 4 つのボタンのイベント ハンドラーをクリックします。 ボタンのクリック イベントを発生させることができるデザイナー コード ファイルに自動生成されたコードを追加も、ボタンをダブルクリックします。

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>FillOrCancel フォームのロジックのコードを追加します。

FillOrCancel フォームのロジックを完了するには、次の手順に従います。

1. そのメンバーの名前を完全に修飾する必要があるないように、次の 2 つの名前空間をスコープに含めます。

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```
     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. 次のコードに示すように、変数とヘルパー メソッドをクラスに追加します。

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. 次のコードに示すように、メソッド本体を次の 4 つのボタンをクリック イベント ハンドラーを完了します。

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>アプリケーションをテストする

各クリック イベント ハンドラーをコードし、コードの記述を完了した後、**F5** キーを押してアプリケーションのビルドとテストを実行します。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
