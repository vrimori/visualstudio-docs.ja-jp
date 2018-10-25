---
title: WCF Data Service への WPF コントロールのバインド
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
ms.openlocfilehash: 0f18aaff185e6591d43f10c979c00b654d5608a6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949384"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>WCF Data Service への WPF コントロールのバインド

このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。 コントロールは、WCF Data Service にカプセル化された顧客レコードにバインドされます。 また、顧客がレコードを表示および更新するために使用できるボタンも追加します。

このチュートリアルでは、次の作業について説明します。

- AdventureWorksLT サンプル データベースのデータから生成される Entity Data Model を作成する。

- WCF データ サービスを作成するには、WPF アプリケーションに Entity Data Model でデータが公開します。

- 項目をドラッグしてデータ バインド コントロールのセットを作成する、**データソース**WPF デザイナーにウィンドウ。

- 顧客レコード間を前後に移動するためのボタンを作成する。

- WCF データ サービスを基になるデータ ソース コントロール内のデータに変更を保存するボタンを作成します。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを実行するには、次のコンポーネントが必要です。

-   Visual Studio

-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。

次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。

- WCF Data Services。 詳細については、次を参照してください。[概要](/dotnet/framework/data/wcf/wcf-data-services-overview)します。

- [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] のデータ モデル。

- Entity Data Model および ADO.NET Entity Framework。 詳細については、次を参照してください。 [Entity Framework の概要](/dotnet/framework/data/adonet/ef/overview)します。

- WPF データ バインディング。 詳細については、次を参照してください。[データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)します。

## <a name="create-the-service-project"></a>サービス プロジェクトを作成します。

WCF データ サービスのプロジェクトを作成して、このチュートリアルを開始します。

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

3.  展開**Visual c#** または**Visual Basic**、し、 **Web**します。

4.  **[ASP.NET Web アプリケーション]** プロジェクト テンプレートを選択します。

5.  **名前**ボックスに「 **AdventureWorksService**  をクリック**OK**します。

     Visual Studio によって作成、 **AdventureWorksService**プロジェクト。

6.  **ソリューション エクスプ ローラー**を右クリックして**Default.aspx**選択**削除**します。 このファイルは、このチュートリアルでは必要ありません。

## <a name="create-an-entity-data-model-for-the-service"></a>サービスのエンティティ データ モデルを作成します。

WCF Data Service を使用してアプリケーションにデータを公開するには、サービスのデータ モデルを定義する必要があります。 WCF データ サービスは、2 つの種類のデータ モデルをサポートしています。 エンティティのデータ モデル、およびカスタム データ モデルを実装する共通言語ランタイム (CLR) オブジェクトを使用して定義されている、<xref:System.Linq.IQueryable%601>インターフェイス。 このチュートリアルでは、データ モデルとして Entity Data Model を作成します。

1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

2.  インストールされたテンプレートの一覧で**データ**を選び、 **ADO.NET Entity Data Model**プロジェクト アイテム。

3.  名を変更して`AdventureWorksModel.edmx`、 をクリック**追加**します。

     **Entity Data Model**ウィザードが開きます。

4.  **モデルのコンテンツの選択** ページで **データベースから生成**、 をクリック**次**。

5.  **データ接続の選択**ページで、次のオプションのいずれかを選択します。

    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これを選択します。

    -   をクリックして**新しい接続**、AdventureWorksLT データベースへの接続を作成します。

6.  **データ接続の選択**ことを確認します ページで、**エンティティ接続設定の app.config に保存**オプションが選択されているし、順にクリックします**次**します。

7.  **データベース オブジェクトの選択** ページで、展開**テーブル**、クリックして、 **SalesOrderHeader**テーブル。

8.  **[完了]** をクリックします。

## <a name="create-the-service"></a>サービスを作成します。

WPF アプリケーションに Entity Data Model でデータを公開する WCF Data Service を作成します。

1.  **プロジェクト**メニューの **新しい項目の追加**します。

2.  **インストールされたテンプレート**一覧で、 **Web**を選び、 **WCF Data Service**プロジェクト アイテム。

3.  **名前**ボックスに「 `AdventureWorksService.svc`、 をクリック**追加**します。

     Visual Studio の追加、`AdventureWorksService.svc`をプロジェクトにします。

## <a name="configure-the-service"></a>サービスの構成

作成した Entity Data Model を操作するサービスを構成する必要があります。

1.  `AdventureWorks.svc`ファイルのコードで置き換えます、 **AdventureWorksService**クラスの次のコードで宣言します。

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     このコードは更新、 **AdventureWorksService**クラスから派生するよう、<xref:System.Data.Services.DataService%601>で動作する、`AdventureWorksLTEntities`オブジェクト コンテキスト クラス、エンティティ データ モデル。 また、`InitializeService` メソッドも更新され、`SalesOrderHeader` エンティティへの完全な読み取り/書き込みアクセスがサービスのクライアントに許可されます。

2.  プロジェクトをビルドし、エラーが発生しないことを確認します。

## <a name="create-the-wpf-client-application"></a>WPF クライアント アプリケーションを作成します。

WCF データ サービスからデータを表示するには、サービスに基づいているデータ ソースと新しい WPF アプリケーションを作成します。 このチュートリアルの後半で、データ バインド コントロールをアプリケーションに追加します。

1.  **ソリューション エクスプ ローラー**は、ソリューション ノードを右クリックし、**追加**、選択と**新しいプロジェクト**します。

2.  **新しいプロジェクト**ダイアログ ボックスで、展開**Visual c#** または**Visual Basic**、し、 **Windows**します。

3.  選択、 **WPF アプリケーション**プロジェクト テンプレート。

4.  **名前**ボックスに「 `AdventureWorksSalesEditor`、 をクリック**OK**します。

     Visual Studio の追加、`AdventureWorksSalesEditor`プロジェクトがソリューションにします。

5.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

     **データソース**ウィンドウが開きます。

6.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

     **データ ソースの構成**ウィザードが開きます。

7.  **データ ソースの種類を選択**、ウィザードのページ**サービス**、順にクリックします**次**します。

8.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**Discover**します。

     Visual Studio が使用可能なサービスは、現在のソリューションを検索し、追加`AdventureWorksService.svc`で利用可能なサービスの一覧に、**サービス**ボックス。

9. **Namespace**ボックスに「 **AdventureWorksService**します。

10. **サービス**ボックスで、 **AdventureWorksService.svc**、順にクリックします**OK**します。

     Visual Studio は、サービスの情報をダウンロードし、状態に戻ります、**データ ソースの構成**ウィザード。

11. **サービス参照の追加**] ページで [**完了**します。

     Visual Studio にサービスによって返されるデータを表すノードの追加、**データソース**ウィンドウ。

## <a name="define-the-user-interface"></a>ユーザー インターフェイスを定義します。

WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。 これらのボタンを使用して販売レコードを表示および更新できるようにするコードは、このチュートリアルで後で追加します。

1. **ソリューション エクスプ ローラー**、ダブルクリックして**MainWindow.xaml**します。

    WPF デザイナーでウィンドウが開きます。

2. デザイナーの [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. プロジェクトをビルドします。

## <a name="create-the-data-bound-controls"></a>データ バインド コントロールを作成します。

ドラッグして、顧客レコードを表示するコントロールを作成、`SalesOrderHeaders`ノードから、**データソース**をデザイナーにウィンドウ。

1.  **データ ソース**ウィンドウで、ドロップダウン メニューをクリックして、 **[salesorderheaders]** ノード、および選択**詳細**します。

2.  展開、 **[salesorderheaders]** ノード。

3.  この例では、いくつかのフィールドは表示されませんので、次のノードの横にあるドロップダウン メニューをクリックして、選択**None**:

    -   **CreditCardApprovalCode**

    -   **ModifiedDate**

    -   **OnlineOrderFlag**

    -   **RevisionNumber**

    -   **rowguid**

    この操作は、次の手順において、これらのノードに対応するデータ バインド コントロールが Visual Studio で作成されるのを防ぎます。 このチュートリアルでは、エンドユーザーがこのデータを表示する必要がないことを想定しています。

4.  **データ ソース**ウィンドウで、ドラッグ、 **[salesorderheaders]** ノード下のボタンを含む行のグリッド行にします。

     Visual Studio には、XAML とのデータにバインドされるコントロールのセットを作成するコードが生成される、**製品**テーブル。 生成された XAML とコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)します。

5.  横に、デザイナーでは、クリックして、テキスト ボックス、**顧客 ID**ラベル。

6.  **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティ。

7.  設定、 **IsReadOnly**以下のテキスト ボックスのそれぞれのプロパティ。

    -   **発注書番号**

    -   **販売注文 ID**

    -   **販売注文番号**

## <a name="load-the-data-from-the-service"></a>サービスからデータを読み込む

サービスのプロキシ オブジェクトを使用して、サービスからの売上データを読み込みます。 データ ソースに返されるデータを割り当てる、 <xref:System.Windows.Data.CollectionViewSource> WPF ウィンドウ。

1.  作成するため、デザイナーで、`Window_Loaded`イベント ハンドラーを読み取るテキストをダブルクリックします: **MainWindow**します。

2.  イベント ハンドラーを次のコードで置き換えます。 交換することを確認、 *localhost*開発用コンピューター上のローカル ホスト アドレスでこのコードでのアドレス。

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>販売レコード間を移動します。

使用して販売レコード間をスクロールできるようにするコードを追加、 **\<** と**>** ボタン。

1.  デザイナーをダブルクリック、 **<** ウィンドウ サーフェイスのボタンをクリックします。

     Visual Studio の分離コード ファイルを開くし、新たに作成します`backButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  生成された `backButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3.  デザイナーに戻り、ダブルクリック、 **>** ボタンをクリックします。

     Visual Studio の分離コード ファイルを開くし、新たに作成します`nextButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

4.  生成された `nextButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>販売レコードへの変更を保存します。

ユーザーを表示およびを使用して販売レコードへの変更を保存できるようにするコードを追加、**変更を保存**ボタンをクリックします。

1.  デザイナーで、ダブルクリック、**変更の保存**ボタンをクリックします。

     Visual Studio の分離コード ファイルを開くし、新たに作成します`saveButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>アプリケーションをテストする

ビルドし、表示および顧客レコードを更新できることを確認するアプリケーションを実行します。

1.  **[ビルド]** メニューのをクリックして**ソリューションのビルド**します。 ソリューションがエラーなしでビルドされることを確認します。

2.  キーを押して**Ctrl**+**F5**します。

     Visual Studio の起動時、 **AdventureWorksService**プロジェクトのデバッグを行わず、します。

3.  **ソリューション エクスプ ローラー**を右クリックし、 **AdventureWorksSalesEditor**プロジェクト。

4.  コンテキスト メニューで、[**デバッグ**、] をクリックして**新しいインスタンスを開始**します。

     アプリケーションが実行されます。 次のことを検証します。

    -   販売注文 ID を持つ最初の販売レコードからのデータのさまざまなフィールドを表示するテキスト ボックス**71774**します。

    -   クリックすることができます、 **>** または**<** 他の販売レコード間を移動するボタン。

5.  販売レコードの 1 つは、入力内のテキスト、**コメント**ボックスをクリックして**変更を保存**します。

6.  アプリケーションを終了し、Visual Studio からもう一度アプリケーションを起動します。

7.  変更した販売レコードに移動し、アプリケーションを終了して再起動した後でも変更が保持されていることを確認します。

8.  アプリケーションを終了します。

## <a name="next-steps"></a>次の手順

このチュートリアルを完了した後、関連する次のタスクを実行できます。

-   使用する方法について説明します、**データソース**WPF のバインドを Visual Studio のウィンドウを他の種類のデータ ソースを制御します。 詳細については、次を参照してください。[データセットにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-dataset.md)します。

-   使用する方法について説明します、**データソース**Visual Studio で WPF コントロールに関連するデータ (つまり、親子リレーションシップ内のデータ) を表示するウィンドウ。 詳細については、次を参照してください。[チュートリアル: WPF アプリケーションで関連データの表示](../data-tools/display-related-data-in-wpf-applications.md)します。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [データセットへの WPF コントロールのバインド](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF の概要 (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework の概要 (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [データ バインディングの概要 (.NET Framework)](/dotnet/framework/wpf/data/data-binding-overview)