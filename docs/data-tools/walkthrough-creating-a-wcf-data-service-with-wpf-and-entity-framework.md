---
title: "Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "data services in Visual Studio"
  - "WCF Data Services, Visual Studio"
  - "ADO.NET Data Services, Visual Studio"
  - "WCF data services in Visual Studio"
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 24
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio
このチュートリアルでは、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] Web アプリケーションでホストされる簡単な [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] を作成して、Windows フォーム アプリケーションからアクセスする方法について説明します。  
  
 このチュートリアルでは、次の作業を行います。  
  
-   [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] をホストする Web アプリケーションを作成します。  
  
-   Northwind データベースの Customers テーブルを表す[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を作成します。  
  
-   [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成します。  
  
-   クライアント アプリケーションを作成し、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] への参照を追加します。  
  
-   サービスへのデータ バインディングを有効にし、ユーザー インターフェイスを生成します。  
  
-   必要に応じて、アプリケーションにフィルター処理機能を追加します。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Northwind サンプル データベース。  
  
     開発用コンピューターにこのデータベースがない場合は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088)からダウンロードします。  手順については、「[Downloading Sample Databases](../Topic/Downloading%20Sample%20Databases.md)」を参照してください。  
  
## サービスの作成  
 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を作成するには、Web プロジェクトを追加し、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を作成した後、そのモデルからサービスを作成します。  
  
 最初に、サービスをホストする Web プロジェクトを追加します。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Web プロジェクトを作成するには  
  
1.  メニュー バーで **\[ファイル\]**、**\[新規\]**、**\[プロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[Visual Basic\]** または **\[Visual C\#\]** ノードを展開して、**\[Web\]** ノードをクリックし、**\[ASP.NET Web アプリケーション\]** テンプレートをクリックします。  
  
3.  **\[名前\]** ボックスに「NorthwindWeb」と入力し、**\[OK\]** をクリックします。  
  
4.  **\[新しい ASP.NET プロジェクト\]** ダイアログ ボックスの **\[テンプレートの選択\]** リストで **\[なし\]** を選択し、**\[OK\]** ボタンをクリックします。  
  
 この手順では、Northwind データベースにある Customers テーブルを表す[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を作成します。  
  
#### Entity Data Model を作成するには  
  
1.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[データ\]** ノードを選択し、**\[ADO.NET エンティティ データ モデル\]** 項目を選択します。  
  
3.  **\[名前\]** ボックスに「`NorthwindModel`」と入力し、**\[追加\]** ボタンをクリックします。  
  
     Entity Data Model ウィザードが表示されます。  
  
4.  エンティティ データ モデル ウィザードの **\[モデルのコンテンツの選択\]** ページで、**\[データベースからの EF デザイナー \(EF Designer from database\)\]** 項目を選択してから **\[次へ\]** ボタンを選択します。  
  
5.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         または  
  
    -   **\[新しい接続\]** を選択して、新しいデータ接続を構成します。  詳細については、「[方法: SQL Server データベースへの接続を作成する](http://msdn.microsoft.com/ja-jp/360c340d-e5a6-4a7e-a569-e95d500be43d)」を参照してください。  
  
6.  データベースにパスワードが必要な場合は、**\[はい、重要情報を接続文字列に含めます。\]** を選択し、**\[次へ\]** をクリックします。  
  
    > [!NOTE]
    >  ダイアログ ボックスが表示された場合は、**\[はい\]** をクリックしてファイルをプロジェクトに保存します。  
  
7.  **\[バージョンの選択\]** ページで **\[Entity Framework 5.0\]** オプション ボタンを選択し、**\[次へ\]** をクリックします。  
  
    > [!NOTE]
    >  WCF サービス で Entity Framework 6 の最新バージョンを使用するには、WCF Data Services Entity Framework Provider NuGet パッケージのインストールが必要になります。  「[Using WCF Data Services 5.6.0 with Entity Framework 6\+](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx)」を参照してください。  
  
8.  **\[データベース オブジェクトの選択\]** ページで、**\[テーブル\]** ノードを展開し、**\[Customers\]** チェック ボックスをオンにして **\[完了\]** をクリックします。  
  
     エンティティ モデル ダイアグラムが表示され、プロジェクトに NorthwindModel.edmx ファイルが追加されます。  
  
 この手順では、データ サービスを作成してテストします。  
  
#### データ サービスを作成するには  
  
1.  メニュー バーで **\[プロジェクト\]**、**\[新しい項目の追加\]** の順に選択します。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで **\[Web\]** ノードを選択し、**\[WCF Data Service 5.6\]** 項目を選択します。  
  
3.  **\[名前\]** ボックスに「`NorthwindCustomers`」と入力し、**\[追加\]** をクリックします。  
  
     NorthwindCustomers.svc ファイルが**コード エディター**に表示されます。  
  
4.  **コード エディター**で、最初の `TODO:` コメントを探して、コードを次のコードに置き換えます。  
  
     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-cs[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]  
  
5.  `InitializeService` イベント ハンドラーのコメントを次のコードに置き換えます。  
  
     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-cs[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]  
  
6.  メニュー バーで **\[デバッグ\]**、**\[デバッグなしで開始\]** の順にクリックして、プロジェクトを実行します。  ブラウザー ウィンドウが開き、そのサービスの XML スキーマが表示されます。  
  
7.  **\[アドレス\]** バーの NorthwindCustomers.svc の URL の末尾に「`Customers`」と入力し、Enter キーを押します。  
  
     Customers テーブル内のデータの XML 表現が表示されます。  
  
    > [!NOTE]
    >  Internet Explorer がデータを誤って RSS フィードとして解釈する場合があります。  RSS フィードを表示するオプションが無効になっていることを確認してください。  詳細については、「[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)」を参照してください。  
  
8.  ブラウザー ウィンドウを閉じます。  
  
 次の手順では、サービスを使用する Windows フォーム クライアント アプリケーションを作成します。  
  
## クライアント アプリケーションの作成  
 クライアント アプリケーションを作成するには、2 つ目のプロジェクトを追加し、そのプロジェクトにサービス参照を追加します。そして、データ ソースを構成し、サービスから取得したデータを表示するユーザー インターフェイスを作成します。  
  
 最初に、Windows フォーム プロジェクトをソリューションに追加し、スタートアップ プロジェクトに設定します。  
  
#### クライアント アプリケーションを作成するには  
  
1.  メニュー バーで \[ファイル\]、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[Visual Basic\]** ノードまたは **\[Visual C\#\]** ノードを展開し、**\[Windows\]** をクリックして **\[Windows フォーム アプリケーション\]** をクリックします。  
  
3.  **\[名前\]** ボックスに「`NorthwindClient`」と入力し、**\[OK\]** をクリックします。  
  
4.  **ソリューション エクスプローラー**で、**\[NorthwindClient\]** プロジェクト ノードをクリックします。  
  
5.  メニュー バーで、**\[プロジェクト\]**、**\[スタートアップ プロジェクトに設定\]** の順に選択します。  
  
 この手順では、Web プロジェクト内の [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] へのサービス参照を追加します。  
  
#### サービス参照を追加するには  
  
1.  メニュー バーで、**\[プロジェクト\]**、**\[サービス参照の追加\]** の順に選択します。  
  
2.  **\[サービス参照の追加\]** ダイアログ ボックスで、**\[探索\]** をクリックします。  
  
     NorthwindCustomers サービスの URL が **"アドレス"** フィールドに表示されます。  
  
3.  **\[OK\]** をクリックして、サービス参照を追加します。  
  
 この手順では、データ ソースを構成して、サービスへのデータ バインディングを有効にします。  
  
#### サービスへのデータ バインディングを有効にするには  
  
1.  メニュー バーの **\[表示\]** をクリックし、**\[その他のウィンドウ\]**、**\[データ ソース\]** の順にクリックします。  
  
2.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックします。  
  
3.  **データ ソースの構成**ウィザードの **\[データ ソースの種類を選択\]** ページで、**\[オブジェクト\]** をクリックし、**\[次へ\]** をクリックします。  
  
4.  **\[データ オブジェクトの選択\]** ページで、**NorthwindClient** ノードを展開し、さらに **NorthwindClient.ServiceReference1** ノードを展開します。  
  
5.  **\[Customer\]** チェック ボックスをオンにし、**\[完了\]** をクリックします。  
  
 この手順では、サービスから取得したデータを表示するユーザー インターフェイスを作成します。  
  
#### ユーザー インターフェイスを作成するには  
  
1.  **\[データ ソース\]** ウィンドウで、**\[Customers\]** ノードのショートカット メニューを開き、**\[コピー\]** をクリックします。  
  
2.  **\[Form1.vb\]** または **\[Form1.cs\]** フォーム デザイナーで、ショートカット メニューを開き、**\[貼り付け\]** をクリックします。  
  
     <xref:System.Windows.Forms.DataGridView> コントロール、<xref:System.Windows.Forms.BindingSource> コンポーネント、および <xref:System.Windows.Forms.BindingNavigator> コンポーネントがフォームに追加されます。  
  
3.  **\[CustomersDataGridView\]** コントロールを選択してから、**\[プロパティ\]** ウィンドウで **\[Dock\]** プロパティを **\[Fill\]** に設定します。  
  
4.  **ソリューション エクスプローラー**で、**\[Form1\]** ノードのショートカット メニューを開き、**\[コードの表示\]** を選択してコード エディターを開き、次の Imports または Using ステートメントをファイルの先頭に追加します。  
  
    ```vb  
    Imports NorthwindClient.ServiceReference1  
    ```  
  
    ```c#  
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
  
    ```c#  
    private void Form1_Load(object sender, EventArgs e)  
    {  
    NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
    this.CustomersBindingSource.DataSource = proxy.Customers;  
    }  
  
    ```  
  
6.  **ソリューション エクスプローラー**で、NorthwindCustomers.svc ファイルのショートカット メニューを開き、**\[ブラウザーで表示\]** をクリックします。  Internet Explorer が開き、そのサービスの XML スキーマが表示されます。  
  
7.  Internet Explorer のアドレス バーから URL をコピーします。  
  
8.  手順 4. で追加したコードの「`http://localhost:53161/NorthwindCustomers.svc/`」を選択し、コピーした URL に置き換えます。  
  
9. メニュー バーで、**\[デバッグ\]**、**\[デバッグ開始\]** の順に選択してアプリケーションを実行します。  顧客情報が表示されます。  
  
 この時点で、NorthwindCustomers サービスから取得した顧客の一覧を表示するアプリケーションが作成されました。  このサービスを使用して他のデータも公開する場合は、[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]を変更して、Northwind データベースの他のテーブルを含めます。  
  
 次の省略可能な手順では、サービスによって返されたデータをフィルター処理する方法について説明します。  
  
## フィルター処理機能の追加  
 この手順では、アプリケーションをカスタマイズして、都市で顧客データをフィルター処理します。  
  
#### 都市によるフィルター処理を追加するには  
  
1.  **ソリューション エクスプローラー**で、**\[Form1.vb\]** または **\[Form1.cs\]** ノードのショートカット メニューを開き、**\[開く\]** をクリックします。  
  
2.  <xref:System.Windows.Forms.TextBox>\[ツールボックス\] から、<xref:System.Windows.Forms.Button> コントロールと  **コントロールをフォームに追加します。**  
  
3.  <xref:System.Windows.Forms.Button> コントロールのショートカット メニューを開き、**\[コードの表示\]** をクリックして、`Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
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
  
    ```c#  
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
  
5.  メニュー バーで、**\[デバッグ\]**、**\[デバッグ開始\]** の順に選択してアプリケーションを実行します。  
  
6.  テキスト ボックスに「London」と入力し、ボタンをクリックします。  ロンドンの顧客だけが表示されます。  
  
## 参照  
 [How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)