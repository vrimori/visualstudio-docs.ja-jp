---
title: データセットへの WPF コントロールのバインド |Microsoft Docs
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
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 19189e63a3fb3fdfa3016cb2643cc34a193a2a52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893001"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>データセットへの WPF コントロールのバインド
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。 コントロールは、データセットでカプセル化された製品レコードにバインドされます。 また、製品を参照するためのボタンの追加と、製品レコードへの変更の保存も行います。  
  
 このチュートリアルでは、次の作業について説明します。  
  
- WPF アプリケーションと、AdventureWorksLT サンプル データベースのデータから生成されるデータセットを作成する。  
  
- データ テーブルをドラッグしてデータ バインド コントロールのセットを作成、**データソース**WPF デザイナーのウィンドウのウィンドウ。  
  
- 製品レコード間を前後に移動するためのボタンを作成する。  
  
- ユーザーが製品レコードに加えた変更を、データ テーブルおよび基になるデータ ソースに保存するボタンを作成する。  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを実行するには、次のコンポーネントが必要です。  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)します。  
  
  次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。  
  
- データセットおよび TableAdapter。 詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)と[TableAdapter の概要](../data-tools/tableadapter-overview.md)します。  
  
- WPF デザイナーの操作。 詳細については、次を参照してください。 [WPF および Silverlight デザイナーの概要](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)します。  
  
- WPF データ バインディング。 詳しくは、「 [データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)」をご覧ください。  
  
## <a name="create-the-project"></a>プロジェクトの作成  
 新しい WPF プロジェクトを作成します。 このプロジェクトでは、製品レコードを表示します。  
  
#### <a name="to-create-the-project"></a>プロジェクトを作成するには  
  
1.  Visual Studio を起動します。  
  
2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
3.  展開**Visual Basic**または**Visual c#**、し、 **Windows**します。  
  
4.  選択、 **WPF アプリケーション**プロジェクト テンプレート。  
  
5.  **名前**ボックスに「 `AdventureWorksProductsEditor`  をクリック**OK**します。  
  
     Visual Studio によって作成、`AdventureWorksProductsEditor`プロジェクト。  
  
## <a name="create-a-dataset-for-the-application"></a>アプリケーションのデータセットを作成します。  
 アプリケーションのデータ モデルを定義および追加する必要がありますデータ バインド コントロールを作成する前に、**データソース**ウィンドウ。 このチュートリアルでは、データ モデルとして使用するデータセットを作成します。  
  
#### <a name="to-create-a-dataset"></a>データセットを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
     **データソース**ウィンドウが開きます。  
  
2.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。  
  
     **データ ソースの構成**ウィザードが開きます。  
  
3.  **データ ソースの種類を選択**] ページで、[**データベース**、順にクリックします**次**します。  
  
4.  **データベース モデルの選択**] ページで、[**データセット**、順にクリックします**次**します。  
  
5.  **データ接続の選択**ページで、次のオプションのいずれかを選択します。  
  
    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストで使用可能な場合は、それを選択してクリックして**次**します。  
  
    -   をクリックして**新しい接続**、AdventureWorksLT データベースへの接続を作成します。  
  
6.  **アプリケーション構成ファイルへの接続文字列を保存**] ページで、[、**接続を保存、** チェック ボックスをオンにして **[次へ]**。  
  
7.  **データベース オブジェクトの選択** ページで、展開**テーブル**、クリックして、 **Product (SalesLT)** テーブル。  
  
8.  **[完了]** をクリックします。  
  
     Visual Studio プロジェクトに新しい AdventureWorksLTDataSet.xsd ファイルを追加して、対応する追加**AdventureWorksLTDataSet**項目を**データソース**ウィンドウ。 AdventureWorksLTDataSet.xsd ファイルには、`AdventureWorksLTDataSet` という名前の型指定されたデータセットと、`ProductTableAdapter` という名前の TableAdapter が定義されます。 このチュートリアルの後半で、`ProductTableAdapter` を使用してデータセットにデータを読み込み、変更をデータベースに保存します。  
  
9. プロジェクトをビルドします。  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter の既定の fill メソッドを編集します。  
 データセットにデータを読み込むには、`Fill` の `ProductTableAdapter` メソッドを使用します。 既定では、`Fill` メソッドによって、`ProductDataTable` の `AdventureWorksLTDataSet` に Product テーブルのすべてのデータ行が読み込まれます。 このメソッドは、行のサブセットのみを返すように変更できます。 このチュートリアルでは、写真付きの製品の行のみを返すように `Fill` メソッドを変更します。  
  
#### <a name="to-load-product-rows-that-have-photos"></a>写真付きの製品の行を読み込むには  
  
1.  **ソリューション エクスプ ローラー**、AdventureWorksLTDataSet.xsd ファイルをダブルクリックします。  
  
     データセット デザイナーが開きます。  
  
2.  デザイナーで、右クリックし、 **Fill,GetData()** を選択し、**構成**します。  
  
     **TableAdapter 構成**ウィザードが開きます。  
  
3.  **SQL ステートメントの入力**ページで、追加した後は、次の WHERE 句、`SELECT`テキスト ボックス内のステートメント。  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4.  **[完了]** をクリックします。  
  
## <a name="define-the-user-interface"></a>ユーザー インターフェイスを定義します。  
 WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。 これらのボタンを使用して製品レコード間をスクロールしたり、製品レコードへの変更を保存したりできるようにするコードは、このチュートリアルで後で追加します。  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>ウィンドウのユーザー インターフェイスを定義するには  
  
1.  **ソリューション エクスプ ローラー**MainWindow.xaml をダブルクリックします。  
  
     WPF デザイナーでウィンドウが開きます。  
  
2.  デザイナーの [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  プロジェクトをビルドします。  
  
## <a name="createdata-bound-controls"></a>データ バインド コントロール  
 ドラッグして、顧客レコードを表示するコントロールを作成、`Product`テーブルから、**データソース**WPF デザイナーにウィンドウ。  
  
#### <a name="to-create-data-bound-controls"></a>データ バインド コントロールを作成するには  
  
1.  **データ ソース**ウィンドウで、ドロップダウン メニューをクリックして、**製品**ノード**詳細**します。  
  
2.  展開、**製品**ノード。  
  
3.  この例では、いくつかのフィールドは表示されませんので、次のノードの横にあるドロップダウン メニューをクリックして、選択**None**:  
  
    -   ProductCategoryID  
  
    -   ProductModelID  
  
    -   ThumbnailPhotoFileName  
  
    -   rowguid  
  
    -   ModifiedDate  
  
4.  次に、ドロップダウン メニューをクリックして、 **ThumbNailPhoto**ノード**イメージ**します。  
  
    > [!NOTE]
    >  既定では、項目、**データ ソース**画像を表すウィンドウで、既定のコントロールに設定がある**None**します。 これは、画像がデータベース内でバイト配列として格納されているためです。バイト配列には、単純なバイト配列から大規模なアプリケーションの実行可能ファイルまで、あらゆるデータを格納できます。  
  
5.  **データ ソース**ウィンドウで、ドラッグ、**製品**ノード下のボタンを含む行のグリッド行にします。  
  
     Visual Studio でのデータにバインドされているコントロールのセットを定義する XAML の生成、**製品**テーブル。 また、データを読み込むコードも生成されます。 生成された XAML とコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)します。  
  
6.  横に、デザイナーでは、クリックして、テキスト ボックス、**製品 ID**ラベル。  
  
7.  **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティ。  
  
## <a name="navigating-product-records"></a>製品レコード間を移動  
 使用して製品レコード間をスクロールできるようにするコードを追加、 **\<** と**>** ボタン。  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>ユーザーが製品レコード間を移動できるようにするには  
  
1.  デザイナーをダブルクリック、 **<** ウィンドウ サーフェイスのボタンをクリックします。  
  
     Visual Studio の分離コード ファイルを開くし、新たに作成します`backButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
2.  変更、`Window_Loaded`イベント ハンドラーでは、そのため、 `ProductViewSource`、`AdventureWorksLTDataSet`と`AdventureWorksLTDataSetProductTableAdapter`は、メソッドの外部であること、およびフォーム全体にアクセスできます。 これらをフォームにグローバルのみを宣言し、内でそれらを割り当てる、`Window_Loaded`次のようなイベント ハンドラー。  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3.  `backButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4.  デザイナーとダブルクリックに戻り、 **>** ボタンをクリックします。  
  
5.  `nextButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>製品レコードへの Savechanges  
 使用して製品レコードへの変更を保存するようにするコードを追加、**変更を保存**ボタンをクリックします。  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>製品レコードへの変更を保存する機能を追加するには  
  
1.  デザイナーで、ダブルクリック、**変更を保存**ボタンをクリックします。  
  
     Visual Studio の分離コード ファイルを開くし、新たに作成します`saveButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    >  この例では、`Save` の `TableAdapter` メソッドを使用して変更を保存します。 このチュートリアルでは、データ テーブルが 1 つのみ変更されるため、この方法が適しています。 複数のデータ テーブルへの変更を保存する必要がある場合は、Visual Studio によってデータセットと共に生成される `UpdateAll` の `TableAdapterManager` メソッドを使用することもできます。 詳細については、次を参照してください。 [TableAdapterManager の概要](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)します。  
  
## <a name="test-the-application"></a>アプリケーションをテストする  
 アプリケーションをビルドして実行します。 製品レコードを表示および更新できることを確認します。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  **F5**キーを押します。  
  
     アプリケーションがビルドされ、実行されます。 次のことを検証します。  
  
    -   テキスト ボックスに、写真付きの製品の先頭のレコードのデータが表示されること。 この製品は、製品 ID は 713 でと、名前を持つ**Long-sleeve Logo Jersey, S**します。  
  
    -   クリックすることができます、 **>** または**<** 他の製品レコード間を移動するボタン。  
  
2.  製品レコードの 1 つは、変更、**サイズ**値をクリックして**変更を保存**します。  
  
3.  アプリケーションを閉じるし、キーを押してアプリケーションを再起動**F5** Visual Studio でします。  
  
4.  変更した製品レコードに移動し、変更が保持されていることを確認します。  
  
5.  アプリケーションを終了します。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを完了した後、関連する次のタスクを実行できます。  
  
-   使用する方法について説明します、**データソース**WPF のバインドを Visual Studio のウィンドウを他の種類のデータ ソースを制御します。 詳細については、次を参照してください。 [WCF data service にコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)します。  
  
-   使用する方法について説明します、**データソース**Visual Studio で WPF コントロールに関連するデータ (つまり、親子リレーションシップ内のデータ) を表示するウィンドウ。 詳細については、次を参照してください。[チュートリアル: WPF アプリケーションで関連データを表示する](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Visual Studio でのデータに WPF コントロールをバインドします。](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)   
 [WPF と Silverlight のデザイナーの概要](http://msdn.microsoft.com/en-us/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [データ バインディングの概要](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)

