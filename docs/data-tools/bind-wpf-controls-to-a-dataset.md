---
title: データセットへの WPF コントロールをバインドします。
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bd0aa9ae269da4cfd4ae5ab3dfb45e96052d75fe
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="bind-wpf-controls-to-a-dataset"></a>データセットへの WPF コントロールをバインドします。
このチュートリアルでは、データ バインド コントロールが含まれた WPF アプリケーションを作成します。 コントロールは、データセットでカプセル化された製品レコードにバインドされます。 また、製品を参照するためのボタンの追加と、製品レコードへの変更の保存も行います。

このチュートリアルでは、次の作業について説明します。

- WPF アプリケーションと、AdventureWorksLT サンプル データベースのデータから生成されるデータセットを作成する。

- データ テーブルをドラッグして、データ バインド コントロールのセットを作成する、**データソース**WPF デザイナーでウィンドウをウィンドウです。

- 製品レコード間を前後に移動するためのボタンを作成する。

- ユーザーが製品レコードに加えた変更を、データ テーブルおよび基になるデータ ソースに保存するボタンを作成する。

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルを実行するには、次のコンポーネントが必要です。

-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]

-   AdventureWorksLT サンプル データベースが添付された、SQL Server または SQL Server Express の実行中のインスタンスへのアクセス権。 AdventureWorksLT データベースをダウンロードすることができます、 [CodePlex Web サイト](http://go.microsoft.com/fwlink/?linkid=87843)です。

次の概念に関する知識があると役立ちますが、チュートリアルを実行するうえで必須というわけではありません。

-   データセットおよび TableAdapter。 詳細については、次を参照してください。 [Visual Studio でのデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)と[TableAdapter](../data-tools/create-and-configure-tableadapters.md)です。

-   WPF データ バインディング。 詳しくは、「 [データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)」をご覧ください。

## <a name="create-the-project"></a>プロジェクトの作成
 新しい WPF プロジェクトを作成します。 このプロジェクトでは、製品レコードを表示します。

#### <a name="to-create-the-project"></a>プロジェクトを作成するには

1.  Visual Studio を起動します。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

3.  展開**Visual Basic**または**Visual c#**、し、 **Windows**です。

4.  選択、 **WPF アプリケーション**プロジェクト テンプレート。

5.  **名前**ボックスに、入力`AdventureWorksProductsEditor` をクリック**OK**です。

     Visual Studio によって作成、`AdventureWorksProductsEditor`プロジェクト。

## <a name="create-a-dataset-for-the-application"></a>アプリケーションのデータセットを作成します。
 データ バインド コントロールを作成することができます、前に、アプリケーションのデータ モデルを定義しを追加する必要があります、**データソース**ウィンドウです。 このチュートリアルでは、データ モデルとして使用するデータセットを作成します。

#### <a name="to-create-a-dataset"></a>データセットを作成するには

1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。

     **データソース**ウィンドウが開きます。

2.  **[データ ソース]** ウィンドウで、 **[新しいデータ ソースの追加]** をクリックします。

     **データ ソース構成**ウィザードが開きます。

3.  **データ ソースの種類を選択**] ページで、[**データベース**、順にクリック**次**です。

4.  **データベース モデルの選択**] ページで、[**データセット**、順にクリック**次**です。

5.  **データ接続の選択** ページで、次のオプションのいずれかを選択します。

    -   AdventureWorksLT サンプル データベースへのデータ接続がドロップダウン リストで使用可能な場合は、選択し、をクリックして**次**です。

    -   をクリックして**新しい接続**、AdventureWorksLT データベースへの接続を作成します。

6.  **アプリケーション構成ファイルへの接続文字列を保存**] ページで、[、**接続を保存、**チェック ボックスをクリックして **[次へ]** です。

7.  **データベース オブジェクトの選択** ページで、展開**テーブル**、クリックして、 **Product (SalesLT)** テーブル。

8.  **[完了]** をクリックします。

     Visual Studio が新しく追加`AdventureWorksLTDataSet.xsd`ファイル、プロジェクトを追加、対応する**AdventureWorksLTDataSet**項目を**データソース**ウィンドウ。 `AdventureWorksLTDataSet.xsd`ファイルという名前の型指定されたデータセットを定義する`AdventureWorksLTDataSet`およびという名前の TableAdapter`ProductTableAdapter`です。 このチュートリアルの後半で、`ProductTableAdapter` を使用してデータセットにデータを読み込み、変更をデータベースに保存します。

9. プロジェクトをビルドします。

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter の既定の fill メソッドを編集します。
 データセットにデータを読み込むには、`Fill` の `ProductTableAdapter` メソッドを使用します。 既定では、`Fill` メソッドによって、`ProductDataTable` の `AdventureWorksLTDataSet` に Product テーブルのすべてのデータ行が読み込まれます。 このメソッドは、行のサブセットのみを返すように変更できます。 このチュートリアルでは、写真付きの製品の行のみを返すように `Fill` メソッドを変更します。

#### <a name="to-load-product-rows-that-have-photos"></a>写真付きの製品の行を読み込むには

1.  **ソリューション エクスプ ローラー**をダブルクリックして、`AdventureWorksLTDataSet.xsd`ファイル。

     データセット デザイナーが開きます。

2.  デザイナーを右クリックし、**塗りつぶし、GetData()** を選択し、**構成**です。

     **TableAdapter 構成**ウィザードが開きます。

3.  **SQL ステートメントを入力** ページで、追加した後は、次の WHERE 句、`SELECT`テキスト ボックス内のステートメント。

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4.  **[完了]** をクリックします。

## <a name="define-the-user-interface"></a>ユーザー インターフェイスを定義します。
 WPF デザイナーで XAML を変更して、いくつかのボタンをウィンドウに追加します。 これらのボタンを使用して製品レコード間をスクロールしたり、製品レコードへの変更を保存したりできるようにするコードは、このチュートリアルで後で追加します。

#### <a name="to-define-the-user-interface-of-the-window"></a>ウィンドウのユーザー インターフェイスを定義するには

1.  **ソリューション エクスプ ローラー**MainWindow.xaml をダブルクリックします。

     WPF デザイナーでウィンドウが開きます。

2.  デザイナーの [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] ビューで、`<Grid>` タグの間に次のコードを追加します。

    ```xaml
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3.  プロジェクトをビルドします。

## <a name="create-data-bound-controls"></a>データ バインド コントロールを作成します。
 ドラッグすることで顧客レコードを表示するコントロールを作成、`Product`からテーブル、**データソース**WPF デザイナーにウィンドウです。

#### <a name="to-create-data-bound-controls"></a>データ バインド コントロールを作成するには

1.  **データ ソース**ウィンドウで、ドロップダウン メニューをクリックして、**製品**ノード**詳細**です。

2.  展開して、**製品**ノード。

3.  この例では、いくつかのフィールドは表示されませんので、次のノードの横のドロップダウン メニューをクリックして選択**None**:

    -   ProductCategoryID

    -   ProductModelID

    -   ThumbnailPhotoFileName

    -   rowguid

    -   ModifiedDate

4.  次に、ドロップダウン メニューをクリックして、 **ThumbNailPhoto**ノード**イメージ**です。

    > [!NOTE]
    >  既定では、項目を**データ ソース**画像を表す期間設定、既定のコントロールである**None**です。 これは、画像がデータベース内でバイト配列として格納されているためです。バイト配列には、単純なバイト配列から大規模なアプリケーションの実行可能ファイルまで、あらゆるデータを格納できます。

5.  **データ ソース**ウィンドウで、ドラッグ、**製品**ノード下のボタンが含まれる行のグリッド行にします。

     Visual Studio でのデータにバインドされるコントロールのセットを定義する XAML を生成、**製品**テーブル。 また、データを読み込むコードも生成されます。 生成される XAML およびコードの詳細については、次を参照してください。 [Visual Studio でのデータにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)です。

6.  デザイナーをクリックして、テキスト ボックス の横に、**プロダクト ID**ラベル。

7.  **プロパティ**ウィンドウで、横にあるチェック ボックスを選択、 **IsReadOnly**プロパティです。

## <a name="navigating-product-records"></a>製品レコード間の移動
 使用して製品レコード間をスクロールできるようにするコードを追加、 **\<** と**>** ボタン。

#### <a name="to-enable-users-to-navigate-product-records"></a>ユーザーが製品レコード間を移動できるようにするには

1.  デザイナーをダブルクリックして、 **<** ウィンドウ サーフェイスのボタンをクリックします。

     Visual Studio は、分離コード ファイルを開くし、新たに作成`backButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  変更、 `Window_Loaded` 、イベント ハンドラーのため、 `ProductViewSource`、 `AdventureWorksLTDataSet`、および`AdventureWorksLTDataSetProductTableAdapter`はメソッドの外部およびフォーム全体にアクセスします。 これらをフォームにグローバルのみを宣言し、内で、これらを割り当てる、`Window_Loaded`次のようなイベント ハンドラー。

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3.  `backButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4.  ダブルクリックして、デザイナーに戻り、 **>** ボタンをクリックします。

5.  `nextButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>製品レコードへの変更を保存します。
使用して製品レコードへの変更を保存するようにするコードを追加、**変更を保存**ボタンをクリックします。

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>製品レコードへの変更を保存する機能を追加するには

1.  デザイナーをダブルクリックして、**変更を保存**ボタンをクリックします。

     Visual Studio は、分離コード ファイルを開くし、新たに作成`saveButton_Click`のイベント ハンドラー、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。

2.  `saveButton_Click` イベント ハンドラーに次のコードを追加します。

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    >  この例では、`Save` の `TableAdapter` メソッドを使用して変更を保存します。 このチュートリアルでは、データ テーブルが 1 つのみ変更されるため、この方法が適しています。 複数のデータ テーブルへの変更を保存する必要がある場合は、Visual Studio によってデータセットと共に生成される `UpdateAll` の `TableAdapterManager` メソッドを使用することもできます。 詳細については、次を参照してください。 [Tableadapter](../data-tools/create-and-configure-tableadapters.md)です。

## <a name="test-the-application"></a>アプリケーションをテストする
 アプリケーションをビルドして実行します。 製品レコードを表示および更新できることを確認します。

#### <a name="to-test-the-application"></a>アプリケーションをテストするには

1.  **F5**キーを押します。

     アプリケーションがビルドされ、実行されます。 次のことを検証します。

    -   テキスト ボックスに、写真付きの製品の先頭のレコードのデータが表示されること。 この製品は、製品 ID は 713 でと、名前を持つ**Long-sleeve Logo Jersey, S**です。

    -   クリックすることができます、 **>** または**<** 他の製品レコード間を移動するボタンです。

2.  製品レコードの 1 つは、変更、**サイズ**値に設定して、をクリックして**変更を保存**です。

3.  アプリケーションを閉じるし、キーを押して、アプリケーションを再起動して**f5 キーを押して**Visual Studio でします。

4.  変更した製品レコードに移動し、変更が保持されていることを確認します。

5.  アプリケーションを終了します。

## <a name="next-steps"></a>次の手順
 このチュートリアルを完了した後、関連する次のタスクを実行できます。

-   使用する方法、**データソース**WPF のバインドを Visual Studio のウィンドウを他の種類のデータ ソースを制御します。 詳細については、次を参照してください。 [WCF データ サービスにコントロールをバインドする WPF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)です。

-   使用する方法、**データソース**WPF コントロールに関連するデータ (つまり、親子関係にあるデータ) を表示する Visual Studio のウィンドウ。 詳細については、次を参照してください。[チュートリアル: WPF アプリケーションで関連するデータを表示する](../data-tools/display-related-data-in-wpf-applications.md)です。

## <a name="see-also"></a>関連項目

- [Visual Studio でデータに WPF コントロールをバインドする](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visual Studio のデータセット ツール](../data-tools/dataset-tools-in-visual-studio.md)
- [データ バインディングの概要](/dotnet/framework/wpf/data/data-binding-overview)