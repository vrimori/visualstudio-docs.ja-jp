---
title: WPF と Entity Framework 6 で単純なデータ アプリケーションを作成します。
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c39546d48cd8b8bf71594685f944751c1f023750
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117811"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF と Entity Framework 6 で単純なデータ アプリケーションを作成します。

このチュートリアルでは、Visual Studio で基本的な「フォーム オーバー データ」アプリケーションを作成する方法を示します。 アプリでは、SQL Server LocalDB、Northwind データベース、Entity Framework 6、および Windows Presentation Foundation を使用します。 マスター/詳細ビューでは、基本的なデータ バインドを実行する方法を示し、ボタンを使ってカスタム バインドのナビゲーターが**Move Next**、 **Move Previous**、 **を先頭に移動**、**末尾に移動**、 **Update**と**削除**します。

この記事では、Visual Studio での data tools の使用について説明し、任意の深さの基になるテクノロジの説明を試行しません。 これにより、XAML、Entity Framework、および SQL の基礎知識があることを前提としています。 また、この例には、WPF アプリケーションの標準モデル-ビュー-ビューモデル (MVVM) のアーキテクチャは示しません。 ただし、いくつかの変更を MVVM アプリケーションにこのコードをコピーすることができます。

## <a name="install-and-connect-to-northwind"></a>インストールし、Northwind に接続

この例では、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。 その製品の ADO.NET データ プロバイダーは、Entity Framework をサポートする場合、他の SQL データベース製品とでも動作する必要があります。

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、 **.NET デスクトップ開発**ワークロードまたは個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (**SQL Server オブジェクト エクスプ ローラー**がの一部としてインストールされている、**データ ストレージと処理**ワークロードで、 **Visual Studio インストーラー**)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

3.  [新しい接続を追加](../data-tools/add-new-connections.md)Northwind 用です。

## <a name="configure-the-project"></a>プロジェクトを構成する

1.  Visual Studio で、次のように選択します。**ファイル** > **新規** > **プロジェクト**し、新しい c# WPF アプリケーションを作成します。

2.  次に、Entity Framework 6 の NuGet パッケージを追加します。 **ソリューション エクスプ ローラー**、プロジェクト ノードを選択します。 メイン メニューで、次のように選択します。**プロジェクト** > **NuGet パッケージの管理**します。

     ![NuGet パッケージのメニュー項目を管理します。](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  **NuGet パッケージ マネージャー**、 をクリックして、**参照**リンク。 Entity Framework は、一覧の最上位のパッケージでは可能性があります。 クリックして**インストール**右側のウィンドウで、画面の指示に従います。 出力ウィンドウでは、インストールが完了するとします。

     ![Entity Framework NuGet パッケージ](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  今すぐ Visual Studio を使用して、Northwind データベースに基づくモデルを作成することができます。

## <a name="create-the-model"></a>モデルを作成する

1.  ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし **追加** > **新しい項目の**します。 [C#] ノードで、左側のウィンドウで次のように選択します。**データ**中央のペインで選択**ADO.NET Entity Data Model**します。

     ![Entity Framework モデル新しいプロジェクト項目](../data-tools/media/raddata-ef-new-project-item.png)

  2.  モデルを呼び出す`Northwind_model`選択**OK**します。 **Entity Data Model ウィザード**が開きます。 選択**データベースの EF デザイナー**順にクリックします**次**します。

     ![データベースから EF モデル](../data-tools/media/raddata-ef-model-from-database.png)

3.  次の画面で、LocalDB Northwind が選択に接続をクリックします**次**します。

4.  ウィザードの次のページで、テーブル、ストアド プロシージャ、および Entity Framework モデルに含めるには、他のデータベース オブジェクトを選択します。 ツリー ビューの dbo ノードを展開し、選択**顧客**、**注文**、および**Order Details**します。 既定値をオンのままにし、をクリックして**完了**します。

     ![モデルのデータベース オブジェクトを選択します。](../data-tools/media/raddata-choose-ef-objects.png)

5.  ウィザードでは、Entity Framework モデルを表す c# クラスが生成されます。 クラスは、プレーンな古い c# クラスと、私たちは、WPF ユーザー インターフェイスにデータをバインドします。 *.Edmx*ファイルは、リレーションシップおよびその他のクラスをデータベース内のオブジェクトに関連付けられるメタデータについて説明します。 *.Tt*ファイルは対象モデルとし、データベースの変更を保存するコードを生成する T4 テンプレート。 これらすべてのファイルを確認できます**ソリューション エクスプ ローラー** Northwind_model ノードの下。

       ![ソリューション エクスプ ローラーの EF モデル ファイル](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

     デザイナー画面、 *.edmx*ファイルでは、いくつかのプロパティと、モデル内のリレーションシップを変更することができます。 このチュートリアルでは、デザイナーを使用することはできません。

6.  *.Tt*ファイルは、汎用と ObservableCollections を必要とする WPF データ バインドで作業することのいずれかを調整する必要があります。 **ソリューション エクスプ ローラー**、Northwind_model ノードを展開し、見つけます*Northwind_model.tt*します。 (になっていないことを確認、*します。Context.tt*すぐ下に表示されるファイルで、 *.edmx*ファイルです)。

    -   2 つの箇所を置き換えます<xref:System.Collections.ICollection>で<xref:System.Collections.ObjectModel.ObservableCollection%601>します。

    -   最初に見つかった位置の交換<xref:System.Collections.Generic.HashSet%601>で<xref:System.Collections.ObjectModel.ObservableCollection%601>51 の行の付近です。 2 番目に出現する HashSet 置き換えないでください。

    -   唯一の一致を置き換える<xref:System.Collections.Generic>(行 431) の付近で<xref:System.Collections.ObjectModel>します。

7.  キーを押して**Ctrl**+**Shift**+**B**プロジェクトをビルドします。 ビルドが完了したら、モデル クラスは、データ ソース ウィザードに表示されます。

表示、移動、およびデータを変更できるように、XAML ページには、このモデルをフックする準備が整いました。

## <a name="databind-the-model-to-the-xaml-page"></a>XAML ページにモデルをデータ バインド

データ バインド コードを記述することが、その Visual Studio を使用する方が簡単です。

1.  メイン メニューで、次のように選択します。**プロジェクト** > **新しいデータ ソースの追加**を起動、**データ ソース構成ウィザード**します。 選択**オブジェクト**データベースではないモデル クラスにバインドしているためです。

     ![オブジェクトのソースとデータ ソース構成ウィザード](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  選択**顧客**します。 (注文のソースは自動的に生成顧客の注文のナビゲーション プロパティから。)

     ![データ ソースとしてのエンティティ クラスを追加します。](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  **[完了]** をクリックします。

4.  移動します*MainWindow.xaml*コード ビューで。 保持して、XAML 単純なは、この例の目的です。 わかりやすい MainWindow のタイトルを変更し、ここでは、800 600 x の高さと幅を増やします。 常に変更します。 メイン グリッドとナビゲーション ボタンの顧客の詳細については、およびその注文を表示するグリッドの 1 つの行にこれら 3 つの行の定義を追加します。

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  今すぐ開きます*MainWindow.xaml*デザイナーで表示しているようにします。 これにより、**データソース**ウィンドウの横に、Visual Studio ウィンドウの余白のオプションとして表示、**ツールボックス**します。 ウィンドウを開くか、それ以外の場合にキーを押します タブをクリックして**Shift**+**Alt**+**D**選択または**ビュー**  > **他の Windows** > **データソース**します。 独自の個々 のテキスト ボックス内の顧客クラスに各プロパティを表示するでしょう。 最初の矢印をクリックして、**顧客**コンボ ボックス**詳細**します。 次に、中央の行に移動すると、デザイナーが認識できるようには、デザイン画面の中央部にノードをドラッグします。 これを紛失した場合は、XAML で後で手動で行を指定できます。 既定では、グリッド要素では、コントロールが垂直方向に配置されますが、この時点では、する位置に配置して、フォームのようにします。 たとえば、有意義なことに、**名前**アドレス上の上部のテキスト ボックス。 この記事のサンプル アプリケーションでは、フィールドの順序を変更し、それら 2 つの列に並べ替えます。

     ![お客様のデータ ソースのバインドを個別のコントロール](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     コード ビューで確認できます、新しい`Grid`要素 1 の行の (中央の行) の親グリッド。 グリッドが親を`DataContext`属性に追加されている CollectionViewSource を指します、`Windows.Resources`要素。 最初のテキスト ボックスにバインドするときに、そのデータ コンテキストを指定**アドレス**、その名前にマップされて、 `Address` 、現在のプロパティ`Customer`CollectionViewSource 内のオブジェクト。

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  顧客がウィンドウの上部に表示されている場合は、半分の下には、その注文を参照してください。 1 つのグリッド ビュー コントロール内には、注文を表示します。 期待どおりに動作するマスター-詳細データ バインドは、Orders の個別のノードが、Customers クラスに Orders プロパティにバインドすることが重要です。 2 行目で、デザイナーに配置するため、顧客クラスの Orders プロパティをフォームの下半分にドラッグします。

     ![グリッドとして注文クラスをドラッグします。](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio には、モデル内のイベントに UI コントロールを接続するすべてのバインド コードが生成されます。 一部のデータを確認するために必要なは、モデルを設定するコードを記述します。 まずに移動します*MainWindow.xaml.cs*データ コンテキストの MainWindow クラスにデータ メンバーを追加します。 このオブジェクトが生成されたには、変更や、モデル内のイベントを追跡するコントロールのようなものは機能します。 また、コンス トラクターの初期化ロジックを追加します。 このよう、クラスの先頭になります。

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     追加、 `using` Load 拡張メソッドをスコープに取り込む System.Data.Entity のディレクティブ。

     ```csharp
     using System.Data.Entity;
     ```

     ここで、下にスクロールし、検索、`Window_Loaded`イベント ハンドラー。 Visual Studio が CollectionViewSource オブジェクトを追加することに注意してください。 これは、モデルの作成時に選択した NorthwindEntities オブジェクトを表します。 コードを追加してみましょう`Window_Loaded`メソッド全体、このような次のようになりました。

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  **F5**キーを押します。 Collectionviewsource に取得された最初の顧客の詳細を表示する必要があります。 データ グリッドで、注文も確認する必要があります。 書式設定ではありません、を修正しましょう。 その他のレコードを表示して、基本的な CRUD 操作を実行する方法を作成することもできます。

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>ページのデザインを調整し、新しい顧客と注文のグリッドを追加します。

Visual Studio によって生成される既定の配置は、アプリケーションの理想的なはないため、XAML で手動で変更を行ったとします。 新しい顧客または注文を追加するユーザーを有効にするいくつか"forms"(これは、実際にはグリッド) も必要があります。 新しい顧客と注文を追加できるようにするには、するには、別の一連のテキスト ボックスにデータ バインドではない必要があります、`CollectionViewSource`します。 ハンドラー メソッドで、Visible プロパティを設定して、特定の時点でユーザーに表示するグリッドを制御します。 最後に、個別の注文を削除するユーザーを有効にする注文のグリッドの各行に、[削除] ボタンを追加します。

最初に、これらのスタイルを追加、`Windows.Resources`要素*MainWindow.xaml*:

```xaml
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Left"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="23"/>
</Style>
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">
    <Setter Property="HorizontalAlignment" Value="Right"/>
    <Setter Property="VerticalAlignment" Value="Center"/>
    <Setter Property="Margin" Value="3"/>
    <Setter Property="Height" Value="26"/>
    <Setter Property="Width" Value="120"/>
</Style>
```

次に、このマークアップを外部グリッド全体を置き換えます。

```xaml
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">
         <Grid.ColumnDefinitions>
             <ColumnDefinition Width="Auto" MinWidth="233"/>
             <ColumnDefinition Width="Auto" MinWidth="397"/>
         </Grid.ColumnDefinitions>
         <Grid.RowDefinitions>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
             <RowDefinition Height="Auto"/>
         </Grid.RowDefinitions>
         <Label Content="New Order Form" FontWeight="Bold"/>
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
     </Grid>
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">
         <DataGrid.Columns>
             <DataGridTemplateColumn>
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">
                 <DataGridTemplateColumn.CellTemplate>
                     <DataTemplate>
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>
                     </DataTemplate>
                 </DataGridTemplateColumn.CellTemplate>
             </DataGridTemplateColumn>
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>
         </DataGrid.Columns>
     </DataGrid>
 </Grid>
```

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>移動、追加、更新、および削除するボタンを追加します。

Windows フォーム アプリケーションでは、データベース内の行を移動したりする基本的な CRUD 操作を行うのためのボタンを持つ BindingNavigator オブジェクトを取得します。 WPF には、BindingNavigator は示しませんが、簡単に作成できます。 ボタンを水平方向の StackPanel 内で使用する実行し、ボタンの背後にあるコード内のメソッドにバインドされているコマンドを関連付けます。

コマンド ロジックを 4 つの部分があります: (1)、コマンド、(2)、バインド、(3)、ボタン、および分離コードでは、(4)、コマンド ハンドラー。

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML でのコマンド、バインディング、およびボタンを追加します。

1.  コマンドを最初に、追加、 *MainWindow.xaml*ファイル内で、`Windows.Resources`要素。

    ```xaml
    <RoutedUICommand x:Key="FirstCommand" Text="First"/>
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>
    ```

2.  CommandBinding はマップを`RoutedUICommand`分離コード内のメソッドにイベント。 この追加`CommandBindings`要素の後に、`Windows.Resources`終了タグ。

    ```xaml
    <Window.CommandBindings>
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>
    </Window.CommandBindings>
    ```

3.  これで、追加、`StackPanel`ナビゲーションを追加、削除、およびボタンを更新します。 最初に、このスタイルを追加`Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     次に、このコードを貼り付けて直後、`RowDefinitions`外側の`Grid`XAML ページの上部の要素。

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>コマンド ハンドラーを MainWindow クラスに追加します。

分離コードは最小限の追加と削除メソッドは除きます。 ナビゲーションは、メソッド、CollectionViewSource のビューのプロパティを呼び出すことによって実行されます。 `DeleteOrderCommandHandler`注文に対して連鎖削除を実行する方法を示しています。 最初にそれに関連付けられている order_details テーブルを削除するがあります。 `UpdateCommandHandler`だけにテキスト ボックスに、ユーザーが加えた変更で、既存の顧客や注文を更新そうしないと、コレクションに新しい顧客または注文を追加します。

これらのハンドラー メソッドを MainWindow クラスに追加*MainWindow.xaml.cs*します。 CollectionViewSource の Customers テーブル用に別の名前がある場合は、これらの各メソッドの名前を調整する必要があります。

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>アプリケーションの実行

デバッグを開始するには、**F5** キーを押します。 顧客と注文データのグリッドで、設定の表示し、ナビゲーション ボタンは期待どおりに動作する必要があります。 をクリックして**コミット**データを入力した後に、モデルに新しい顧客または注文を追加します。 をクリックして**キャンセル**データを保存せずに新しい顧客または新しい注文書からバックアップします。 既存のお客様と、テキスト ボックスで直接、注文に編集を行うことができ、それらの変更は、モデルに自動的に書き込まれます。

## <a name="see-also"></a>関連項目

- [.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework ドキュメント](/ef/)