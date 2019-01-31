---
title: 'チュートリアル: WPF と Entity Framework を使用した WCF データ サービスの作成'
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
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 7c69b032e01d98030f75273b4ca48714530ddf38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935165"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>チュートリアル: WPF と Entity Framework を使用した WCF データ サービスの作成
このチュートリアルでは、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Web アプリケーションでホストされる簡単な [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] を作成して、Windows フォーム アプリケーションからアクセスする方法について説明します。

このチュートリアルでしました。

- [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] をホストする Web アプリケーションを作成します。

- 作成、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を表す、 `Customers` Northwind データベースのテーブル。

- [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成します。

- クライアント アプリケーションを作成し、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] への参照を追加します。

- サービスへのデータ バインディングを有効にし、ユーザー インターフェイスを生成します。

- 必要に応じて、アプリケーションにフィルター処理機能を追加します。

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。

2. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (**SQL Server オブジェクト エクスプ ローラー**がの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="creating-the-service"></a>サービスの作成
[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成するには、Web プロジェクトを追加し、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] を作成した後、そのモデルからサービスを作成します。

最初の手順では、サービスをホストする web プロジェクトを追加します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Web プロジェクトを作成するには

1. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

2. **[新しいプロジェクト]** ダイアログ ボックスの **[Visual Basic]** または **[Visual C#]** ノードを展開して、**[Web]** ノードをクリックし、**[ASP.NET Web アプリケーション]** テンプレートをクリックします。

3. **[名前]** ボックスに「**NorthwindWeb**」と入力し、**[OK]** をクリックします。

4. **[新しい ASP.NET プロジェクト]** ダイアログ ボックスの **[テンプレートの選択]** リストで **[なし]** を選択し、**[OK]** ボタンをクリックします。

次の手順で作成、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を表す、 `Customers` Northwind データベースのテーブル。

### <a name="to-create-the-entity-data-model"></a>Entity Data Model を作成するには

1. メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

2. **[新しい項目の追加]** ダイアログ ボックスで **[データ]** ノードを選択し、**[ADO.NET エンティティ データ モデル]** 項目を選択します。

3. **名前**テキスト ボックスに、入力`NorthwindModel`、選択し、**追加**ボタンをクリックします。

     Entity Data Model ウィザードが表示されます。

4. エンティティ データ モデル ウィザードの **[モデルのコンテンツの選択]** ページで、**[データベースから EF デザイナー]** 項目を選択してから **[次へ]** ボタンを選択します。

5. **[データ接続の選択]** ページで、次のいずれかの操作を行います。

    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

         - または -

    -   **[新しい接続]** を選択して、新しいデータ接続を構成します。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。

6. データベースにパスワードが必要な場合は、**[はい、重要情報を接続文字列に含めます。]** を選択し、**[次へ]** をクリックします。

    > [!NOTE]
    > ダイアログ ボックスが表示された場合は、**[はい]** をクリックしてファイルをプロジェクトに保存します。

7. **[バージョンの選択]** ページで **[Entity Framework 5.0]** オプション ボタンを選択し、**[次へ]** をクリックします。

    > [!NOTE]
    > WCF サービスで Entity Framework 6 の最新バージョンを使用するには、WCF Data Services Entity Framework Provider NuGet パッケージのインストールが必要になります。 参照してください[Services 5.6.0 with Entity Framework 6 + の WCF Data を使用して](https://blogs.msdn.microsoft.com/odatateam/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6/)します。

8. **[データベース オブジェクトの選択]** ページで、**[テーブル]** ノードを展開し、**[Customers]** チェック ボックスをオンにして **[完了]** をクリックします。

     エンティティ モデル ダイアグラムが表示されたら、および*NorthwindModel.edmx*ファイルがプロジェクトに追加します。

次の手順では、作成し、データ サービスをテストします。

### <a name="to-create-the-data-service"></a>データ サービスを作成するには

1. メニュー バーで **[プロジェクト]** > **[新しい項目の追加]** の順に選択します。

2. **[新しい項目の追加]** ダイアログ ボックスで **[Web]** ノードを選択し、**[WCF Data Service 5.6]** 項目を選択します。

3. **名前**テキスト ボックスに、入力`NorthwindCustomers`、選択し、**追加**ボタンをクリックします。

     **NorthwindCustomers.svc** ファイルが**コード エディター**に表示されます。

4. **コード エディター**で、最初の `TODO:` コメントを探して、コードを次のコードに置き換えます。

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. `InitializeService` イベント ハンドラーのコメントを次のコードに置き換えます。

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. メニュー バーで、**デバッグ** > **デバッグなしで開始**サービスを実行します。 ブラウザ ウィンドウを開くし、サービスの XML スキーマを表示します。

7. **アドレス**バーで、入力`Customers`の URL の末尾に**NorthwindCustomers.svc**を選択し、 **」と入力**キー。

     内のデータの XML 表現、`Customers`テーブルが表示されます。

    > [!NOTE]
    > Internet Explorer がデータを誤って RSS フィードとして解釈する場合があります。 RSS フィードを表示するオプションが無効になっていることを確認してください。 詳細については、「[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)」を参照してください。

8. ブラウザー ウィンドウを閉じます。

次の手順では、サービスを使用する Windows フォーム クライアント アプリケーションを作成します。

## <a name="creating-the-client-application"></a>クライアント アプリケーションの作成
 クライアント アプリケーションを作成するには、2 つ目のプロジェクトを追加し、そのプロジェクトにサービス参照を追加します。そして、データ ソースを構成し、サービスから取得したデータを表示するユーザー インターフェイスを作成します。

 最初の手順では、Windows フォーム プロジェクトをソリューションに追加し、スタートアップ プロジェクトとして設定します。

### <a name="to-create-the-client-application"></a>クライアント アプリケーションを作成するには

1. メニュー バーで、ファイルを選択**追加** > **新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードを選択して、 **Windows**ノード、を選択し**Windows フォーム アプリケーション**します。

3. **[名前]** ボックスに「`NorthwindClient`」と入力して、**[OK]** を選択します。

4. **ソリューション エクスプローラー**で、**[NorthwindClient]** プロジェクト ノードをクリックします。

5. メニュー バーで、**[プロジェクト]**、**[スタートアップ プロジェクトに設定]** の順に選択します。

次の手順でサービスへの参照を追加する、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] web プロジェクトにします。

### <a name="to-add-a-service-reference"></a>サービス参照を追加するには

1. メニュー バーで、**プロジェクト** > **サービス参照の追加**します。

2. **[サービス参照の追加]** ダイアログ ボックスで、**[探索]** をクリックします。

     NorthwindCustomers サービスの URL が **[アドレス]** フィールドに表示されます。

3. **[OK]** をクリックして、サービス参照を追加します。

次の手順では、サービスへのデータ バインディングを有効にするデータ ソースを構成します。

### <a name="to-enable-data-binding-to-the-service"></a>サービスへのデータ バインディングを有効にするには

1. メニュー バーで、**ビュー** > **その他の Windows** > **データソース**します。

   **[データ ソース]** ウィンドウが開きます。

2. **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックします。

3. **データ ソースの構成ウィザード**の **[データ ソースの種類を選択]** ページで、**[オブジェクト]** をクリックし、**[次へ]** をクリックします。

4. **[データ オブジェクトの選択]** ページで、**NorthwindClient** ノードを展開し、さらに **NorthwindClient.ServiceReference1** ノードを展開します。

5. **[Customer]** チェック ボックスをオンにし、**[完了]** をクリックします。

次の手順では、サービスからデータを表示するユーザー インターフェイスを作成します。

### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには

1. **[データ ソース]** ウィンドウで、**[Customers]** ノードのショートカット メニューを開き、**[コピー]** をクリックします。

2. **[Form1.vb]** または **[Form1.cs]** フォーム デザイナーで、ショートカット メニューを開き、**[貼り付け]** をクリックします。

    <xref:System.Windows.Forms.DataGridView> コントロール、<xref:System.Windows.Forms.BindingSource> コンポーネント、および <xref:System.Windows.Forms.BindingNavigator> コンポーネントがフォームに追加されます。

3. **[CustomersDataGridView]** コントロールを選択してから、**[プロパティ]** ウィンドウで **[Dock]** プロパティを **[Fill]** に設定します。

4. **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Form1**ノード選択**コードの表示**、コード エディターを開き、次を追加する`Imports`または`Using`ファイルの上部にあるステートメント。

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. `Form1_Load` イベント ハンドラーに次のコードを追加します。

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

6. **ソリューション エクスプローラー**で、**NorthwindCustomers.svc** ファイルのショートカット メニューを開き、**[ブラウザーで表示]** をクリックします。 Internet Explorer 開き、サービスの XML スキーマが表示されます。

7. Internet Explorer のアドレス バーから URL をコピーします。

8. 手順 4. で追加したコードの「`http://localhost:53161/NorthwindCustomers.svc/`」を選択し、コピーした URL に置き換えます。

9. メニュー バーで、**デバッグ** > **デバッグの開始**アプリケーションを実行します。 顧客情報が表示されます。

   この時点で、NorthwindCustomers サービスから取得した顧客の一覧を表示するアプリケーションが作成されました。 このサービスを使用して他のデータも公開する場合は、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を変更して、Northwind データベースの他のテーブルを含めます。

次の省略可能な手順では、サービスによって返されるデータをフィルター処理する方法について説明します。

## <a name="adding-filtering-capabilities"></a>フィルター処理機能の追加
 この手順では、顧客の市区町村ごとのデータをフィルター処理するアプリケーションをカスタマイズします。

### <a name="to-add-filtering-by-city"></a>都市によるフィルター処理を追加するには

1. **ソリューション エクスプローラー**で、**[Form1.vb]** または **[Form1.cs]** ノードのショートカット メニューを開き、**[開く]** をクリックします。

2. **[ツールボックス]** から、<xref:System.Windows.Forms.TextBox> コントロールと <xref:System.Windows.Forms.Button> コントロールをフォームに追加します。

3. ショートカット メニューを開き、<xref:System.Windows.Forms.Button>コントロールを選択**コードの表示**、し、次のコードを追加、`Button1_Click`イベント ハンドラー。

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

4. このコードの `http://localhost:53161/NorthwindCustomers.svc` を `Form1_Load` イベント ハンドラーの URL に置き換えます。

5. メニュー バーで、**デバッグ** > **デバッグの開始**アプリケーションを実行します。

6. テキスト ボックスに「**London**」と入力し、ボタンをクリックします。 ロンドンの顧客だけが表示されます。

## <a name="see-also"></a>関連項目

- [Visual Studio での Windows Communication Foundation サービスと WCF データ サービス](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [方法: WCF データ サービス参照を追加、更新、または削除する](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)