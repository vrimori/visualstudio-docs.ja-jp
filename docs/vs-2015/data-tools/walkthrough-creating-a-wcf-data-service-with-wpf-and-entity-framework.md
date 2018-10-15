---
title: 'チュートリアル: WPF と Entity Framework を使用する WCF Data Service の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6aeb16bb805bc6dda1328b424acbe48b6371437e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197952"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>チュートリアル: WPF と Entity Framework を使用する WCF Data Service の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルは、単純なを作成する方法を示します[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]でホストされる、 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web アプリケーションと Windows フォーム アプリケーションからアクセスします。  
  
 このチュートリアルでは、次の作業を行います。  
  
-   [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] をホストする Web アプリケーションを作成します。  
  
-   Northwind データベースの Customers テーブルを表す[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]を作成します。  
  
-   [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] を作成します。  
  
-   クライアント アプリケーションを作成し、[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] への参照を追加します。  
  
-   サービスへのデータ バインディングを有効にし、ユーザー インターフェイスを生成します。  
  
-   必要に応じて、アプリケーションにフィルター処理機能を追加します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   Northwind サンプル データベース。  
  
     開発用コンピューターにこのデータベースがない場合は、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkID=98088)からダウンロードできます。 手順については、次を参照してください。[サンプル データベースのダウンロード](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5)します。  
  
## <a name="creating-the-service"></a>サービスの作成  
 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] を作成するには、Web プロジェクトを追加し、[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]を作成した後、そのモデルからサービスを作成します。  
  
 最初に、サービスをホストする Web プロジェクトを追加します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Web プロジェクトを作成するには  
  
1.  メニュー バーで、**ファイル**、**新規**、**プロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** と**Web**ノードを選択し、 **ASP します。NET Web アプリケーション**テンプレート。  
  
3.  **名前**テキスト ボックスに、入力 **「northwindweb」と**、選択し、 **OK**ボタン。  
  
4.  **新しい ASP.NET プロジェクト** ダイアログ ボックスで、**テンプレートを選択**一覧で、選択**空**、選択し、 **ok**ボタンをクリックします。  
  
 この手順では、Northwind データベースにある Customers テーブルを表す[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]を作成します。  
  
#### <a name="to-create-the-entity-data-model"></a>Entity Data Model を作成するには  
  
1.  メニュー バーで、**プロジェクト**、**新しい項目の追加**します。  
  
2.  **新しい項目の追加** ダイアログ ボックスで、選択、**データ**ノードを選択し、 **ADO.NET Entity Data Model**項目。  
  
3.  **名前**テキスト ボックスに、入力`NorthwindModel`、選択し、**追加**ボタンをクリックします。  
  
     Entity Data Model ウィザードが表示されます。  
  
4.  Entity Data Model ウィザードでの**モデルのコンテンツの選択**ページで、選択、**データベースの EF デザイナー**項目を選び、 **[次へ]** ボタンをクリックします。  
  
5.  **[データ接続の選択]** ページで、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         - または -  
  
    -   選択、**新しい接続**新しいデータ接続を構成するボタンをクリックします。 詳細については、次を参照してください。[新しい接続を追加](../data-tools/add-new-connections.md)します。  
  
6.  データベースは、パスワードを必要とする場合は、選択、**はい、機密データの接続文字列に含める**オプション ボタンをクリックして、**次**ボタン。  
  
    > [!NOTE]
    >  ダイアログ ボックスが表示される選択**はい**をプロジェクトにファイルを保存します。  
  
7.  **バージョンの選択**ページで、選択、 **Entity Framework 5.0**オプション ボタンをクリックして、 **[次へ]** ボタンをクリックします。  
  
    > [!NOTE]
    >  WCF サービス で Entity Framework 6 の最新バージョンを使用するには、WCF Data Services Entity Framework Provider NuGet パッケージのインストールが必要になります。 参照してください[Services 5.6.0 with Entity Framework 6 + の WCF Data を使用して](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx)します。  
  
8.  **データベース オブジェクトの選択** ページで、展開、**テーブル**ノードを選択、**顧客**チェック ボックスをオンにして、**完了**ボタンをクリックします。  
  
     エンティティ モデル ダイアグラムが表示され、プロジェクトに NorthwindModel.edmx ファイルが追加されます。  
  
 この手順では、データ サービスを作成してテストします。  
  
#### <a name="to-create-the-data-service"></a>データ サービスを作成するには  
  
1.  メニュー バーで、**プロジェクト**、**新しい項目の追加**します。  
  
2.  **新しい項目の追加** ダイアログ ボックスで、選択、 **Web**ノードを選択し、 **WCF Data Service 5.6**項目。  
  
3.  **名前**テキスト ボックスに、入力`NorthwindCustomers`、選択し、**追加**ボタンをクリックします。  
  
     NorthwindCustomers.svc ファイルに表示されます、**コード エディター**します。  
  
4.  **コード エディター**、最初の検索`TODO:`コメントし、次のコードに置き換えます。  
  
     [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
     [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5.  `InitializeService` イベント ハンドラーのコメントを次のコードに置き換えます。  
  
     [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
     [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6.  メニュー バーで、**デバッグ**、**デバッグなしで開始**サービスを実行します。 ブラウザー ウィンドウが開き、そのサービスの XML スキーマが表示されます。  
  
7.  **アドレス**バーで、入力`Customers`NorthwindCustomers.svc の URL の末尾に選択し、 **ENTER**キー。  
  
     Customers テーブル内のデータの XML 表現が表示されます。  
  
    > [!NOTE]
    >  Internet Explorer がデータを誤って RSS フィードとして解釈する場合があります。 RSS フィードを表示するオプションが無効になっていることを確認してください。 詳細については、次を参照してください。[サービス参照のトラブルシューティング](../data-tools/troubleshooting-service-references.md)します。  
  
8.  ブラウザー ウィンドウを閉じます。  
  
 次の手順では、サービスを使用する Windows フォーム クライアント アプリケーションを作成します。  
  
## <a name="creating-the-client-application"></a>クライアント アプリケーションの作成  
 クライアント アプリケーションを作成するには、2 つ目のプロジェクトを追加し、そのプロジェクトにサービス参照を追加します。そして、データ ソースを構成し、サービスから取得したデータを表示するユーザー インターフェイスを作成します。  
  
 最初に、Windows フォーム プロジェクトをソリューションに追加し、スタートアップ プロジェクトに設定します。  
  
#### <a name="to-create-the-client-application"></a>クライアント アプリケーションを作成するには  
  
1.  メニュー バーで、ファイルを選択**追加**、**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、展開、 **Visual Basic**または**Visual c#** ノードを選択し、 **Windows**ノード、を選択し、**Windows フォーム アプリケーション**します。  
  
3.  **[名前]** ボックスに「`NorthwindClient`」と入力して、**[OK]** を選択します。  
  
4.  **ソリューション エクスプ ローラー**、選択、 **NorthwindClient**プロジェクト ノード。  
  
5.  メニュー バーで、**プロジェクト**、**スタートアップ プロジェクトとして設定**します。  
  
 この手順では、Web プロジェクト内の [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] へのサービス参照を追加します。  
  
#### <a name="to-add-a-service-reference"></a>サービス参照を追加するには  
  
1.  メニュー バーで、**プロジェクト**、**サービス参照の追加**します。  
  
2.  **サービス参照の追加** ダイアログ ボックスで、選択、 **Discover**ボタンをクリックします。  
  
     NorthwindCustomers サービスの URL に表示されます、**アドレス**フィールド。  
  
3.  選択、 **OK**サービス参照を追加するボタンをクリックします。  
  
 この手順では、データ ソースを構成して、サービスへのデータ バインディングを有効にします。  
  
#### <a name="to-enable-data-binding-to-the-service"></a>サービスへのデータ バインディングを有効にするには  
  
1.  メニュー バーで、**ビュー**、**その他の Windows**、**データソース**します。  
  
2.  **データ ソース**ウィンドウで、選択、**新しいデータ ソースの追加**ボタンをクリックします。  
  
3.  **データ ソースの種類を選択**のページ、**データ ソース構成ウィザード**、選択**オブジェクト**、選択し、**次**ボタン.  
  
4.  **データ オブジェクトの選択** ページで、展開、 **NorthwindClient**ノードの順に展開し、 **NorthwindClient.ServiceReference1**ノード。  
  
5.  選択**顧客**チェック ボックスをオンにして、**完了**ボタンをクリックします。  
  
 この手順では、サービスから取得したデータを表示するユーザー インターフェイスを作成します。  
  
#### <a name="to-create-the-user-interface"></a>ユーザー インターフェイスを作成するには  
  
1.  **データソース**ウィンドウで、ショートカット メニューを開き、**顧客**ノード選択**コピー**。  
  
2.  **Form1.vb**または**Form1.cs**フォーム デザイナー、ショートカット メニューを開き、選択**貼り付け**します。  
  
     <xref:System.Windows.Forms.DataGridView> コントロール、<xref:System.Windows.Forms.BindingSource> コンポーネント、および <xref:System.Windows.Forms.BindingNavigator> コンポーネントがフォームに追加されます。  
  
3.  選択、 **CustomersDataGridView**コントロール、し、**プロパティ**ウィンドウのセット、**ドッキング**プロパティを**入力**します。  
  
4.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Form1**ノード選択**コードの表示**をコード エディターを開き、次の Imports または Using ステートメントでの追加、ファイルの先頭:  
  
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
  
6.  **ソリューション エクスプ ローラー**NorthwindCustomers.svc ファイルのショートカット メニューを開き、選択**ブラウザーで表示**します。 Internet Explorer が開き、そのサービスの XML スキーマが表示されます。  
  
7.  Internet Explorer のアドレス バーから URL をコピーします。  
  
8.  手順 4. で追加したコードの「`http://localhost:53161/NorthwindCustomers.svc/`」を選択し、コピーした URL に置き換えます。  
  
9. メニュー バーで、**デバッグ**、**デバッグの開始**アプリケーションを実行します。 顧客情報が表示されます。  
  
 この時点で、NorthwindCustomers サービスから取得した顧客の一覧を表示するアプリケーションが作成されました。 このサービスを使用して他のデータも公開する場合は、[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]を変更して、Northwind データベースの他のテーブルを含めます。  
  
 次の省略可能な手順では、サービスによって返されたデータをフィルター処理する方法について説明します。  
  
## <a name="adding-filtering-capabilities"></a>フィルター処理機能の追加  
 この手順では、アプリケーションをカスタマイズして、都市で顧客データをフィルター処理します。  
  
#### <a name="to-add-filtering-by-city"></a>都市によるフィルター処理を追加するには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Form1.vb**または**Form1.cs**ノード選択**開く**します。  
  
2.  追加、<xref:System.Windows.Forms.TextBox>コントロールと<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**をフォームにします。  
  
3.  ショートカット メニューを開き、<xref:System.Windows.Forms.Button>制御、および選択**コードの表示**、し、次のコードを追加、`Button1_Click`イベント ハンドラー。  
  
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
  
5.  メニュー バーで、**デバッグ**、**デバッグの開始**アプリケーションを実行します。  
  
6.  テキスト ボックスで、次のように入力します。**ロンドン**、ボタンを選択するとします。 ロンドンの顧客だけが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [方法: WCF データ サービス参照を追加、更新、または削除する](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)

