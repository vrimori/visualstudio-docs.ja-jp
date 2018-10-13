---
title: WCF データ サービスへの WPF コントロールのバインド |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdd13647eb485fa20da9c95a1c67ccc3e5f38cc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251837"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>WCF Data Service への WPF コントロールのバインド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。 コントロールは、[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] でカプセル化された顧客レコードにバインドされます。 また、顧客がレコードを表示および更新するために使用できるボタンも追加します。  
  
 このチュートリアルでは、次の作業について説明します。  
  
-   AdventureWorksLT サンプル データベースのデータから生成される Entity Data Model を作成する。  
  
-   作成、[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]を WPF アプリケーションに Entity Data Model でデータを公開します。  
  
-   項目をドラッグしてデータ バインド コントロールのセットを作成する、**データソース**WPF デザイナーにウィンドウ。  
  
-   顧客レコード間を前後に移動するためのボタンを作成する。  
  
-   コントロール内のデータに変更を保存するボタンを作成、[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]と基になるデータ ソース。  
  
     [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
-   [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。  
  
 次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
-   WCF Data Services。 詳細については、次を参照してください。[概要](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)します。  
  
-   [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] のデータ モデル。  
  
-   Entity Data Model および ADO.NET Entity Framework。 詳細については、次を参照してください。 [Entity Framework の概要](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)します。  
  
-   WPF デザイナーの操作。 詳細については、次を参照してください。 [WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)します。  
  
-   WPF データ バインディング。 詳しくは、「 [データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)」をご覧ください。  
  
## <a name="create-the-service-project"></a>サービス プロジェクトを作成します。  
 このチュートリアルでは、まず [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] のプロジェクトを作成します。  
  
#### <a name="to-create-the-service-project"></a>サービス プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  展開**Visual c#** または**Visual Basic**、し、 **Web**します。  
  
4.  **[ASP.NET Web アプリケーション]** プロジェクト テンプレートを選択します。  
  
5.  **名前**ボックスに「 `AdventureWorksService`  をクリック**OK**します。  
  
     Visual Studio によって作成、`AdventureWorksService`プロジェクト。  
  
6.  **ソリューション エクスプ ローラー**を右クリックして**Default.aspx**選択**削除**します。 このファイルは、このチュートリアルでは必要ありません。  
  
## <a name="create-an-entity-data-model-for-the-service"></a>サービスのエンティティ データ モデルを作成します。  
 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] を使用してアプリケーションにデータを公開するには、サービスのデータ モデルを定義する必要があります。 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] 2 種類のデータ モデルをサポートしています。 エンティティのデータ モデル、およびカスタム データ モデルを実装する共通言語ランタイム (CLR) オブジェクトを使用して定義されている、<xref:System.Linq.IQueryable%601>インターフェイス。 このチュートリアルでは、データ モデルとして Entity Data Model を作成します。  
  
#### <a name="to-create-an-entity-data-model"></a>Entity Data Model を作成するには  
  
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
 作成、[!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]を WPF アプリケーションに Entity Data Model でデータを公開します。  
  
#### <a name="to-create-the-service"></a>サービスを作成するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加**します。  
  
2.  インストールされたテンプレートの一覧で**Web**を選び、 **WCF Data Service**プロジェクト アイテム。  
  
3.  **名前**ボックスに「 `AdventureWorksService.svc`、 をクリック**追加**します。  
  
     Visual Studio の追加、`AdventureWorksService.svc`をプロジェクトにします。  
  
## <a name="configure-the-service"></a>サービスの構成  
 作成した Entity Data Model を操作するには、サービスを構成する必要があります。  
  
#### <a name="to-configure-the-service"></a>サービスを構成するには  
  
1.  `AdventureWorks.svc`ファイルのコードで置き換えます、`AdventureWorksService`クラスの次のコードで宣言します。  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     このコードは更新、`AdventureWorksService`クラスから派生するよう、<xref:System.Data.Services.DataService%601>で動作する、`AdventureWorksLTEntities`オブジェクト コンテキスト クラス、エンティティ データ モデル。 また、`InitializeService` メソッドも更新され、`SalesOrderHeader` エンティティへの完全な読み取り/書き込みアクセスがサービスのクライアントに許可されます。  
  
2.  プロジェクトをビルドし、エラーが発生しないことを確認します。  
  
## <a name="create-the-wpf-client-application"></a>WPF クライアント アプリケーションを作成します。  
 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] のデータを表示するには、サービスに基づくデータ ソースを使用して、新しい WPF アプリケーションを作成します。 このチュートリアルの後半で、データ バインド コントロールをアプリケーションに追加します。  
  
#### <a name="to-create-the-wpf-client-application"></a>WPF クライアント アプリケーションを作成するには  
  
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
  
9. **Namespace**ボックスに「`AdventureWorksService`します。  
  
10. **サービス**ボックスで、 **AdventureWorksService.svc**、順にクリックします**OK**します。  
  
     Visual Studio は、サービスの情報をダウンロードし、状態に戻ります、**データ ソースの構成**ウィザード。  
  
11. **サービス参照の追加**] ページで [**完了**します。  
  
     Visual Studio にサービスによって返されるデータを表すノードの追加、**データソース**ウィンドウ。  
  
## <a name="define-the-user-interface-of-the-window"></a>ウィンドウのユーザー インターフェイスを定義します。  
 WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。 これらのボタンを使用して販売レコードを表示および更新できるようにするコードは、このチュートリアルで後で追加します。  
  
#### <a name="to-create-the-window-layout"></a>ウィンドウ レイアウトを作成するには  
  
1.  **ソリューション エクスプ ローラー**MainWindow.xaml をダブルクリックします。  
  
     WPF デザイナーでウィンドウが開きます。  
  
2.  デザイナーの [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。  
  
    ```  
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
 ドラッグして、顧客レコードを表示するコントロールを作成、`SalesOrderHeaders`ノードから、**データソース**をデザイナーにウィンドウ。  
  
#### <a name="to-create-the-data-bound-controls"></a>データ バインディング コントロールを作成するには  
  
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
  
     Visual Studio には、XAML とのデータにバインドされるコントロールのセットを作成するコードが生成される、**製品**テーブル。 生成された XAML とコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
5.  横に、デザイナーでは、クリックして、テキスト ボックス、**顧客 ID**ラベル。  
  
6.  **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティ。  
  
7.  設定、 **IsReadOnly**以下のテキスト ボックスのそれぞれのプロパティ。  
  
    -   **発注書番号**  
  
    -   **販売注文 ID**  
  
    -   **販売注文番号**  
  
## <a name="load-the-data-from-the-service"></a>サービスからデータを読み込む  
 サービスのプロキシ オブジェクトを使用して、サービスからの売上データを読み込みます。 データ ソースに返されるデータを割り当てる、 <xref:System.Windows.Data.CollectionViewSource> WPF ウィンドウ。  
  
#### <a name="to-load-the-data-from-the-service"></a>サービスからデータを読み込むには  
  
1.  作成するため、デザイナーで、`Window_Loaded`イベント ハンドラーを読み取るテキストをダブルクリックします: **MainWindow**します。  
  
2.  イベント ハンドラーを次のコードで置き換えます。 交換することを確認、 *localhost*開発用コンピューター上のローカル ホスト アドレスでこのコードでのアドレス。  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Navigatesales レコード  
 使用して販売レコード間をスクロールできるようにするコードを追加、 **\<** と**>** ボタン。  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>ユーザーが販売レコード間を移動できるようにするには  
  
1.  デザイナーをダブルクリック、 **<** ウィンドウ サーフェイスのボタンをクリックします。  
  
     Visual Studio の分離コード ファイルを開くし、新たに作成します`backButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
2.  生成された `backButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3.  デザイナーに戻り、ダブルクリック、 **>** ボタンをクリックします。  
  
     Visual Studio の分離コード ファイルを開くし、新たに作成します`nextButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
4.  生成された `nextButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>販売レコードへの変更を保存しています  
 ユーザーを表示およびを使用して販売レコードへの変更を保存できるようにするコードを追加、**変更を保存**ボタンをクリックします。  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>販売レコードへの変更を保存する機能を追加するには  
  
1.  デザイナーで、ダブルクリック、**変更の保存**ボタンをクリックします。  
  
     Visual Studio の分離コード ファイルを開くし、新たに作成します`saveButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 アプリケーションをビルドして実行し、顧客レコードを表示および更新できることを確認します。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  **[ビルド]** メニューのをクリックして**ソリューションのビルド**します。 ソリューションがエラーなしでビルドされることを確認します。  
  
2.  キーを押して**Ctrl + F5**します。  
  
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
  
-   使用する方法について説明します、**データソース**Visual Studio で WPF コントロールに関連するデータ (つまり、親子リレーションシップ内のデータ) を表示するウィンドウ。 詳細については、次を参照してください。[チュートリアル: WPF アプリケーションで関連データを表示する](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [データセットへの WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [概要](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Entity Framework の概要](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [WPF と Silverlight のデザイナーの概要](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

