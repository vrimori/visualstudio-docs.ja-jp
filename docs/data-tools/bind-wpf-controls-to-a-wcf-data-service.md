---
title: WCF data service への WPF コントロールをバインドします。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8152a02df8f335a92024134dde89b45d2f3e115a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>WCF data service への WPF コントロールをバインドします。

このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。 コントロールは、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] でカプセル化された顧客レコードにバインドされます。 また、顧客がレコードを表示および更新するために使用できるボタンも追加します。

このチュートリアルでは、次の作業について説明します。

- AdventureWorksLT サンプル データベースのデータから生成される Entity Data Model を作成する。

- 作成する、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] WPF アプリケーションに Entity Data Model のデータを公開します。

- 項目をドラッグして、データ バインド コントロールのセットを作成する、**データソース**WPF デザイナーにウィンドウです。

- 顧客レコード間を前後に移動するためのボタンを作成する。

- コントロール内のデータに変更を保存するボタンを作成する、[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)]と基になるデータ ソース。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルを実行するには、次のコンポーネントが必要です。

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)です。

次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。

-   WCF Data Services。 詳細については、次を参照してください。[概要](/dotnet/framework/data/wcf/wcf-data-services-overview)です。

-   [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] のデータ モデル。

-   Entity Data Model および ADO.NET Entity Framework。 詳細については、次を参照してください。 [Entity Framework の概要](/dotnet/framework/data/adonet/ef/overview)です。

-   WPF データ バインディング。 詳しくは、「 [データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)」をご覧ください。

## <a name="create-the-service-project"></a>サービス プロジェクトを作成します。
このチュートリアルでは、まず [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] のプロジェクトを作成します。

### <a name="to-create-the-service-project"></a>サービス プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

3.  展開**Visual c#** または**Visual Basic**、し、 **Web**です。

4.  **[ASP.NET Web アプリケーション]** プロジェクト テンプレートを選択します。

5.  **名前**ボックスに、入力`AdventureWorksService` をクリック**OK**です。

     Visual Studio によって作成、`AdventureWorksService`プロジェクト。

6.  **ソリューション エクスプ ローラー**を右クリックして**Default.aspx**選択**削除**です。 このファイルは、このチュートリアルでは必要ありません。

## <a name="create-an-entity-data-model-for-the-service"></a>サービスの Entity Data Model を作成します。
[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] を使用してアプリケーションにデータを公開するには、サービスのデータ モデルを定義する必要があります。 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] 2 種類のデータ モデルをサポートしています。 エンティティ データ モデル、およびカスタム データ モデルを実装する共通言語ランタイム (CLR) オブジェクトを使用して定義されている、<xref:System.Linq.IQueryable%601>インターフェイスです。 このチュートリアルでは、データ モデルとして Entity Data Model を作成します。

### <a name="to-create-an-entity-data-model"></a>Entity Data Model を作成するには

1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

2.  インストールされたテンプレートの一覧で**データ**、クリックして、 **ADO.NET エンティティ データ モデル**プロジェクト項目です。

3.  名前を変更`AdventureWorksModel.edmx`、 をクリック**追加**です。

     **Entity Data Model**ウィザードが開きます。

4.  **モデルのコンテンツ** ページで、をクリックして**データベースから生成**、 をクリック**次**です。

5.  **データ接続の選択** ページで、次のオプションのいずれかを選択します。

    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これを選択します。

    -   をクリックして**新しい接続**、AdventureWorksLT データベースへの接続を作成します。

6.  **データ接続の選択** ページで、ことを確認して、**エンティティ接続設定を付けて App.Config に保存**オプションを選択して、をクリックして**次**です。

7.  **データベース オブジェクトの選択** ページで、展開**テーブル**、クリックして、 **SalesOrderHeader**テーブル。

8.  **[完了]** をクリックします。

## <a name="create-the-service"></a>サービスを作成します。
作成、 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] WPF アプリケーションに Entity Data Model でデータを公開します。

### <a name="to-create-the-service"></a>サービスを作成するには

1.  **プロジェクト**メニューの **新しい項目の追加**です。

2.  インストールされたテンプレートの一覧で**Web**、クリックして、 **WCF データ サービス**プロジェクト項目です。

3.  **名前**ボックスに、入力`AdventureWorksService.svc`、 をクリック**追加**です。

     Visual Studio は追加、`AdventureWorksService.svc`をプロジェクトにします。

## <a name="configure-the-service"></a>サービスの構成
作成した Entity Data Model を操作するには、サービスを構成する必要があります。

### <a name="to-configure-the-service"></a>サービスを構成するには

1.  `AdventureWorks.svc`ファイルのコードは、置換、`AdventureWorksService`クラスの次のコードで宣言します。

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     このコードを更新、`AdventureWorksService`クラスから派生するよう、<xref:System.Data.Services.DataService%601>で動作する、`AdventureWorksLTEntities`エンティティ データ モデルのコンテキスト クラスのオブジェクトします。 また、`InitializeService` メソッドも更新され、`SalesOrderHeader` エンティティへの完全な読み取り/書き込みアクセスがサービスのクライアントに許可されます。

2.  プロジェクトをビルドし、エラーが発生しないことを確認します。

## <a name="create-the-wpf-client-application"></a>WPF クライアント アプリケーションを作成します。
[!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] のデータを表示するには、サービスに基づくデータ ソースを使用して、新しい WPF アプリケーションを作成します。 このチュートリアルの後半で、データ バインド コントロールをアプリケーションに追加します。

### <a name="to-create-the-wpf-client-application"></a>WPF クライアント アプリケーションを作成するには

1.  **ソリューション エクスプ ローラー**ソリューション ノードを右クリックしをクリックして**追加**を選択して**新しいプロジェクト**です。

2.  **新しいプロジェクト**ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**、し、 **Windows**です。

3.  選択、 **WPF アプリケーション**プロジェクト テンプレート。

4.  **名前**ボックスに、入力`AdventureWorksSalesEditor`、 をクリック**OK**です。

     Visual Studio は追加、`AdventureWorksSalesEditor`プロジェクトがソリューションにします。

5.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

     **データソース**ウィンドウが開きます。

6.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

     **データ ソース構成**ウィザードが開きます。

7.  **データ ソースの種類を選択**、ウィザードのページ**サービス**、順にクリック**次**です。

8.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**Discover**です。

     Visual Studio が使用可能なサービスは、現在のソリューションを検索し、追加`AdventureWorksService.svc`で使用可能なサービスの一覧に、 **Services**ボックス。

9. **Namespace**ボックスに、入力`AdventureWorksService`です。

10. **Services**ボックスで、をクリックして**AdventureWorksService.svc**、クリックして **[ok]** です。

     Visual Studio サービス情報をダウンロードし、その、**データ ソース構成**ウィザード。

11. **サービス参照の追加**] ページで [**完了**です。

     Visual Studio は、サービスによって返されるデータを表すノードを追加、**データソース**ウィンドウです。

## <a name="define-the-user-interface-of-the-window"></a>ウィンドウのユーザー インターフェイスを定義します。
WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。 これらのボタンを使用して販売レコードを表示および更新できるようにするコードは、このチュートリアルで後で追加します。

### <a name="to-create-the-window-layout"></a>ウィンドウ レイアウトを作成するには

1.  **ソリューション エクスプ ローラー**をダブルクリックして**MainWindow.xaml**です。

     WPF デザイナーでウィンドウが開きます。

2.  デザイナーの [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  プロジェクトをビルドします。

## <a name="create-the-data-bound-controls"></a>データ バインド コントロールを作成します。
ドラッグすることで顧客レコードを表示するコントロールを作成、`SalesOrderHeaders`ノードから、**データ ソース**をデザイナーにウィンドウです。

### <a name="to-create-the-data-bound-controls"></a>データ バインディング コントロールを作成するには

1.  **データ ソース**ウィンドウで、ドロップダウン メニューをクリックして、 **[salesorderheaders]** ノード、および選択**詳細**です。

2.  展開して、 **SalesOrderHeaders**ノード。

3.  この例では、いくつかのフィールドは表示されませんので、次のノードの横のドロップダウン メニューをクリックして選択**None**:

    -   **CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **rowguid**

    この操作は、次の手順において、これらのノードに対応するデータ バインド コントロールが Visual Studio で作成されるのを防ぎます。 このチュートリアルでは、エンドユーザーがこのデータを表示する必要がないことを想定しています。

4.  **データ ソース**ウィンドウで、ドラッグ、 **[salesorderheaders]** ノード下のボタンが含まれる行のグリッド行にします。

     Visual Studio XAML とのデータにバインドされるコントロールのセットを作成するコードを生成、**製品**テーブル。 生成される XAML およびコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

5.  デザイナーをクリックして、テキスト ボックス の横に、**顧客 ID**ラベル。

6.  **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティです。

7.  設定、 **IsReadOnly**の次のテキスト ボックスのプロパティ。

    -   **注文書番号**

    -   **販売注文 ID**

    -   **販売注文番号**

## <a name="load-the-data-from-the-service"></a>サービスからデータを読み込む
サービス プロキシ オブジェクトを使用して、サービスからの売上データを読み込みます。 データ ソースに返されるデータを割り当てる、 <xref:System.Windows.Data.CollectionViewSource> WPF ウィンドウにします。

### <a name="to-load-the-data-from-the-service"></a>サービスからデータを読み込むには

1.  作成する、デザイナーで、 `Window_Loaded` 、イベント ハンドラーを読み取り、テキストをダブルクリックして: **MainWindow**です。

2.  イベント ハンドラーを次のコードで置き換えます。 交換することを確認してください、 *localhost*開発用コンピューター上のローカル ホスト アドレスでこのコード内のアドレス。

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>販売レコード間を移動します。
使用して販売レコード間をスクロールできるようにするコードを追加、 **\<** と**>** ボタン。

### <a name="to-enable-users-to-navigate-sales-records"></a>ユーザーが販売レコード間を移動できるようにするには

1.  デザイナーをダブルクリックして、 **<** ウィンドウ サーフェイスのボタンをクリックします。

     Visual Studio は、分離コード ファイルを開くし、新たに作成`backButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  生成された `backButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  デザイナーに戻り、ダブルクリック、 **>** ボタンをクリックします。

     Visual Studio は、分離コード ファイルを開くし、新たに作成`nextButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

4.  生成された `nextButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="saving-changes-to-sales-records"></a>販売レコードに変更を保存
ユーザーを表示し、使用して販売レコードへの変更を保存、できるようにするコードを追加、**変更を保存**ボタンをクリックします。

### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>販売レコードへの変更を保存する機能を追加するには

1.  デザイナーをダブルクリックして、 **Save Changes**ボタンをクリックします。

     Visual Studio は、分離コード ファイルを開くし、新たに作成`saveButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="testing-the-application"></a>アプリケーションのテスト
アプリケーションをビルドして実行し、顧客レコードを表示および更新できることを確認します。

### <a name="to-test-the-application"></a>アプリケーションをテストするには

1.  **[ビルド]** メニューのをクリックして**ソリューションのビルド**です。 ソリューションがエラーなしでビルドされることを確認します。

2.  キーを押して**ctrl キーを押しながら f5 キーを押して**です。

     Visual Studio を起動、 **AdventureWorksService**プロジェクトのデバッグを行わず、します。

3.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksSalesEditor**プロジェクト。

4.  コンテキスト メニューで、**デバッグ**をクリックして**新しいインスタンスを開始**です。

     アプリケーションが実行されます。 次のことを検証します。

    -   データの販売注文 ID を持つ最初の販売レコードからフィールドが表示されるテキスト ボックス**71774**です。

    -   クリックすることができます、 **>** または**<** 他の販売レコード間を移動するボタンです。

5.  販売レコードの 1 つは、入力内のテキスト、**コメント**ボックスをクリックして**変更を保存**です。

6.  アプリケーションを終了し、Visual Studio からもう一度アプリケーションを起動します。

7.  変更した販売レコードに移動し、アプリケーションを終了して再起動した後でも変更が保持されていることを確認します。

8.  アプリケーションを終了します。

## <a name="next-steps"></a>次の手順

このチュートリアルを完了した後、関連する次のタスクを実行できます。

-   使用する方法、**データソース**WPF のバインドを Visual Studio のウィンドウを他の種類のデータ ソースを制御します。 詳細については、次を参照してください。[データセットにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-dataset.md)です。

-   使用する方法、**データソース**WPF コントロールに関連するデータ (つまり、親子関係にあるデータ) を表示する Visual Studio のウィンドウ。 詳細については、次を参照してください。[チュートリアル: WPF アプリケーションで関連するデータを表示する](../data-tools/display-related-data-in-wpf-applications.md)です。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF の概要 (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework の概要 (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [データ バインディングの概要 (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)