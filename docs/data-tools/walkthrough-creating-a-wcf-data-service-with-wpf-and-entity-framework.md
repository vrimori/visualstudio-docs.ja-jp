---
title: 'チュートリアル: WPF および Entity Framework と WCF データ サービスを作成します。'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1433620303c8bf300645681eeabcd12c4a9c36d7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>チュートリアル: WPF および Entity Framework と WCF データ サービスを作成します。
このチュートリアルは、単純なを作成する方法を示します[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]でホストされている、 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web アプリケーションとして、Windows フォーム アプリケーションからアクセスします。

このチュートリアルでは、次の作業を行います。

-   [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] をホストする Web アプリケーションを作成します。

-   Northwind データベースの Customers テーブルを表す[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を作成します。

-   [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成します。

-   クライアント アプリケーションを作成し、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] への参照を追加します。

-   サービスへのデータ バインディングを有効にし、ユーザー インターフェイスを生成します。

-   必要に応じて、アプリケーションにフィルター処理機能を追加します。

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。

## <a name="creating-the-service"></a>サービスの作成
[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成するには、Web プロジェクトを追加し、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を作成した後、そのモデルからサービスを作成します。

最初に、サービスをホストする Web プロジェクトを追加します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-the-web-project"></a>Web プロジェクトを作成するには

1.  メニュー バーで、次のように選択します。**ファイル**、**新規**、**プロジェクト**です。

2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#**と**Web** 、ノードを選択し、 **ASP です。NET Web アプリケーション**テンプレート。

3.  **名前**テキスト ボックスに、入力**「NorthwindWeb**、を選択し、 **OK**ボタンをクリックします。

4.  **新しい ASP.NET プロジェクト** ダイアログ ボックスで、**テンプレートを選択して**一覧で、選択**空**を選択し、 **ok**ボタンをクリックします。

次の手順では作成、 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Northwind データベースの Customers テーブルを表すです。

#### <a name="to-create-the-entity-data-model"></a>Entity Data Model を作成するには

1.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。

2.  **新しい項目の追加** ダイアログ ボックスで、選択、**データ** ノードを選択し、 **ADO.NET エンティティ データ モデル**項目。

3.  **名前**テキスト ボックスに、入力`NorthwindModel`を選択し、**追加**ボタンをクリックします。

     Entity Data Model ウィザードが表示されます。

4.  エンティティ データ モデル ウィザードで、上、 **モデルのコンテンツ**ページで、選択、**データベースから EF Designer**項目をクリックして、 **次へ**ボタンをクリックします。

5.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   選択、**新しい接続**新しいデータ接続を構成するボタンをクリックします。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)です。

6.  データベースは、パスワードを必要とする場合は、選択、 **はい、接続文字列に機密データを含める**オプション ボタンをクリックして、**次**ボタンをクリックします。

    > [!NOTE]
    >  ダイアログ ボックスが表示されるを選択**はい**をプロジェクトにファイルを保存します。

7.  **、バージョンを選択**ページで、選択、 **Entity Framework 5.0**オプション ボタンをクリックして、**次**ボタンをクリックします。

    > [!NOTE]
    >  WCF サービスで Entity Framework 6 の最新バージョンを使用するためには、WCF Data Services Entity Framework Provider NuGet パッケージをインストールする必要があります。 参照してください[Services 5.6.0 with Entity Framework 6 以降の WCF データを使用して](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx)です。

8.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノードで、選択、**顧客**チェック ボックスをオンにして、**完了**ボタンをクリックします。

     エンティティ モデル ダイアグラムが表示され、プロジェクトに NorthwindModel.edmx ファイルが追加されます。

次の手順では、作成し、データ サービスをテストします。

#### <a name="to-create-the-data-service"></a>データ サービスを作成するには

1.  メニュー バーで、次のように選択します。**プロジェクト**、**新しい項目の追加**です。

2.  **新しい項目の追加** ダイアログ ボックスで、選択、 **Web**  ノードを選択し、 **WCF Data Service 5.6**項目。

3.  **名前**テキスト ボックスに、入力`NorthwindCustomers`を選択し、**追加**ボタンをクリックします。

     NorthwindCustomers.svc ファイルに表示されます、**コード エディター**です。

4.  **コード エディター**、最初の検索`TODO:`コメントおよびコードを次に置き換えます。

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5.  `InitializeService` イベント ハンドラーのコメントを次のコードに置き換えます。

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6.  メニュー バーで、次のように選択します。**デバッグ**、**デバッグなしで開始**サービスを実行します。 ブラウザー ウィンドウが開き、そのサービスの XML スキーマが表示されます。

7.  **アドレス**バーで、入力`Customers`NorthwindCustomers.svc の URL の末尾を選択し、 **ENTER**キー。

     Customers テーブル内のデータの XML 表現が表示されます。

    > [!NOTE]
    >  Internet Explorer がデータを誤って RSS フィードとして解釈する場合があります。 RSS フィードを表示するオプションが無効になっていることを確認してください。 詳細については、次を参照してください。[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)です。

8.  ブラウザー ウィンドウを閉じます。

次の手順では、サービスを使用する Windows フォーム クライアント アプリケーションを作成します。

## <a name="creating-the-client-application"></a>クライアント アプリケーションの作成
 クライアント アプリケーションを作成するには、2 つ目のプロジェクトを追加し、そのプロジェクトにサービス参照を追加します。そして、データ ソースを構成し、サービスから取得したデータを表示するユーザー インターフェイスを作成します。

 最初に、Windows フォーム プロジェクトをソリューションに追加し、スタートアップ プロジェクトに設定します。

#### <a name="to-create-the-client-application"></a>クライアント アプリケーションを作成するには

1.  メニュー バーで、[ファイル] を選択**追加**、**新しいプロジェクト**です。

2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#**ノードを選択し、 **Windows**ノード、をクリックして**Windows フォーム アプリケーション**です。

3.  **[名前]** ボックスに「`NorthwindClient`」と入力して、**[OK]** を選択します。

4.  **ソリューション エクスプ ローラー**、選択、 **NorthwindClient**プロジェクト ノードです。

5.  メニュー バーで、次のように選択します。**プロジェクト**、**スタートアップ プロジェクトとして設定**です。

次の手順へのサービス参照を追加します、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Web プロジェクトです。

#### <a name="to-add-a-service-reference"></a>サービス参照を追加するには

1.  メニュー バーで、次のように選択します。**プロジェクト**、**サービス参照の追加**です。

2.  **サービス参照の追加** ダイアログ ボックスで、選択、 **Discover**ボタンをクリックします。

     NorthwindCustomers サービスの URL に表示されます、**アドレス**フィールドです。

3.  選択、 **OK**サービス参照を追加するボタンをクリックします。

次の手順では、サービスへのデータ バインディングを有効にするデータ ソースを構成します。

#### <a name="to-enable-data-binding-to-the-service"></a>サービスへのデータ バインディングを有効にするには

1.  メニュー バーで、次のように選択します。**ビュー**、**その他のウィンドウ**、**データソース**です。

2.  **データ ソース**ウィンドウで、選択、**新しいデータ ソースの追加**ボタンをクリックします。

3.  **データ ソースの種類を選択**のページ、**データ ソース構成ウィザード**、選択**オブジェクト**を選択し、**次**ボタン.

4.  **データ オブジェクトの選択** ページで、展開、 **NorthwindClient**  ノードの順に展開し、 **NorthwindClient.ServiceReference1**ノード。

5.  選択**顧客**チェック ボックスをオンにして、**完了**ボタンをクリックします。

次の手順では、サービスからデータを表示するユーザー インターフェイスを作成します。

#### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには

1.  **データ ソース**ウィンドウで、ショートカット メニューを開き、**顧客**ノードを選択して**コピー**です。

2.  **Form1.vb**または**Form1.cs**フォーム デザイナーで、ショートカット メニューを開き**貼り付け**です。

     <xref:System.Windows.Forms.DataGridView> コントロール、<xref:System.Windows.Forms.BindingSource> コンポーネント、および <xref:System.Windows.Forms.BindingNavigator> コンポーネントがフォームに追加されます。

3.  選択、 **CustomersDataGridView**コントロール、し、**プロパティ**ウィンドウのセット、**ドッキング**プロパティを**塗りつぶし**です。

4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Form1**ノードを選択し、**コードの表示**をコード エディターを開き、次の Imports または Using でステートメントを追加しますファイルの先頭。

    ```vb
    Imports NorthwindClient.ServiceReference1
    ```

    ```csharp
    using NorthwindClient.ServiceReference1;
    ```

5.  `Form1_Load` イベント ハンドラーに次のコードを追加します。

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
            Dim proxy As New NorthwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))
            Me.CustomersBindingSource.DataSource = proxy.Customers
        End Sub
    ```

    ```csharp
    private void Form1_Load(object sender, EventArgs e)
    {
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));
    this.CustomersBindingSource.DataSource = proxy.Customers;
    }

    ```

6.  **ソリューション エクスプ ローラー**NorthwindCustomers.svc ファイルのショートカット メニューを開き、選択**ブラウザーで表示**です。 Internet Explorer が開き、そのサービスの XML スキーマが表示されます。

7.  Internet Explorer のアドレス バーから URL をコピーします。

8.  手順 4. で追加したコードの「`http://localhost:53161/NorthwindCustomers.svc/`」を選択し、コピーした URL に置き換えます。

9. メニュー バーで、次のように選択します。**デバッグ**、**デバッグの開始**アプリケーションを実行します。 顧客情報が表示されます。

 この時点で、NorthwindCustomers サービスから取得した顧客の一覧を表示するアプリケーションが作成されました。 このサービスを使用して他のデータも公開する場合は、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を変更して、Northwind データベースの他のテーブルを含めます。

次の省略可能な手順では、サービスによって返されたデータをフィルター処理する方法について説明します。

## <a name="adding-filtering-capabilities"></a>フィルター処理機能の追加
 この手順では、アプリケーションをカスタマイズして、都市で顧客データをフィルター処理します。

#### <a name="to-add-filtering-by-city"></a>都市によるフィルター処理を追加するには

1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Form1.vb**または**Form1.cs**ノードを選択し、**開く**です。

2.  追加、<xref:System.Windows.Forms.TextBox>コントロールと<xref:System.Windows.Forms.Button>から制御、**ツールボックス**をフォームにします。

3.  ショートカット メニューを開き、<xref:System.Windows.Forms.Button>制御、および選択**コードの表示**、し、次のコードを追加、`Button1_Click`イベントのハンドラー。

    ```vb
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
            Dim proxy As New northwindEntities _
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))
            Dim city As String = TextBox1.Text

            If city <> "" Then
                Me.CustomersBindingSource.DataSource = From c In _
             proxy.Customers Where c.City = city
            End If

        End Sub
    ```

    ```csharp
    private void Button1_Click(object sender, EventArgs e)
    {
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));
    string city = TextBox1.Text;

    if (!string.IsNullOrEmpty(city)) {
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;
    }

    }
    ```

4.  このコードの `http://localhost:53161/NorthwindCustomers.svc` を `Form1_Load` イベント ハンドラーの URL に置き換えます。

5.  メニュー バーで、次のように選択します。**デバッグ**、**デバッグの開始**アプリケーションを実行します。

6.  テキスト ボックスに入力**ロンドン**、ボタンをクリックしています。 ロンドンの顧客だけが表示されます。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [方法: WCF データ サービス参照を追加、更新、または削除する](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)