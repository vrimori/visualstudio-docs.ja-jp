---
title: "WPF および Entity Framework 6 の単純なデータ アプリケーションを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 394dbf9aba422f8fbf16857d6980a53b353e931a
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2018
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF と Entity Framework 6 の単純なデータ アプリケーションを作成します。

このチュートリアルでは、SQL Server LocalDB、Northwind データベース、Entity Framework 6、および Windows Presentation Foundation での Visual Studio で基本的な「フォーム オーバー データ」アプリケーションを作成する方法を示します。 マスター/詳細ビューでは、基本的なデータ バインドを行う方法を示していて、さらに、カスタム「バインドのナビゲーター」の"Move Next"ボタンを含む"Move Previous、"「先頭に移動する、」"末尾に移動、"「更新」および「削除」です。  
  
 この記事では、Visual Studio でのデータ ツールの使用について説明し、任意の深さの基になるテクノロジについて説明するのには行われません。 これには、XAML、Entity Framework および SQL の基礎知識があることが前提とします。 また、この例にはモデル-ビュー-ビュー モデル (MVVM) アーキテクチャは、WPF アプリケーションの標準は示しません。 ただし、非常にいくつかの変更、独自の MVVM アプリケーションにこのコードをコピーすることができます。  
  
## <a name="install-and-connect-to-northwind"></a>インストールし、Northwind に接続

この例では、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。 処理が必要他の SQL データベースの製品と同様、その製品の ADO.NET データ プロバイダーが Entity Framework をサポートしている場合。  

1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、 **.NET デスクトップ開発**ワークロード、または個々 のコンポーネントとして。

2.  次の手順に従って、Northwind サンプル データベースをインストールします。  

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.  

       クエリ エディター ウィンドウが開きます。  

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。  

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。  

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。  
  
3.  [新しい接続を追加](../data-tools/add-new-connections.md)Northwind のです。  
  
## <a name="configure-the-project"></a>プロジェクトを構成する
  
1.  Visual Studio で、次のように選択します**ファイル**、**新規**、**プロジェクト.。**し、新しい c# WPF アプリケーションを作成します。  
  
2.  次に Entity Framework 6 の NuGet パッケージを追加します。 ソリューション エクスプ ローラーでプロジェクト ノードを選択します。 メイン メニューで、次のように選択します**プロジェクト**、 **NuGet パッケージを管理しています.。**  
  
     ![NuGet パッケージのメニュー項目を管理](../data-tools/media/raddata_vs2015_manage_nuget_packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  NuGet パッケージ マネージャーで、をクリックして、**参照**リンクします。 Entity Framework は、一覧の最上位のパッケージでは可能性があります。 をクリックして**インストール**右側のウィンドウでの指示に従います。 出力ウィンドウがわかるインストールが完了するとします。  
  
     ![Entity Framework の NuGet パッケージ](../data-tools/media/raddata_vs2015_nuget_ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Northwind データベースに基づくモデルを作成するのに Visual Studio を使用できます。  
  
## <a name="create-the-model"></a>モデルを作成する
  
1.  ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし、選択**追加**、**新しい項目の追加.**.[C#] ノードで、左ペインで選択**データ**し、中央のペインで選択**ADO.NET エンティティ データ モデル**です。  
  
     ![Entity Framework モデル新しいプロジェクト項目](../data-tools/media/raddata-ef-new-project-item.png "raddata EF 新しいプロジェクト項目")  

  2.  モデルを呼び出す`Northwind_model`し、[ok] を選択します。 これにより、 **Entity Data Model ウィザード**です。 選択**データベースから EF Designer**  をクリックし、**次**です。  
  
     ![データベースから EF モデル](../data-tools/media/raddata-ef-model-from-database.png "raddata データベースから EF モデル")  
  
3.  次の画面とを選択して、LocalDB Northwind 接続 をクリック**次**です。  
  
4.  ウィザードの次のページで、テーブル、ストアド プロシージャおよび Entity Framework モデルに含めるには、他のデータベース オブジェクトを選択します。 ツリー ビューで [dbo] ノードを展開し、顧客、注文と注文の詳細を選択します。 既定値をオンのままにし、をクリックして**完了**です。  
  
     ![モデルのデータベース オブジェクトの選択](../data-tools/media/raddata-choose-ef-objects.png "raddata EF オブジェクトの選択")  
  
5.  ウィザードでは、Entity Framework モデルを表す c# クラスを生成します。 これらがプレーンな古い c# クラスと新機能では、WPF のユーザー インターフェイスにデータ バインドします。 .Edmx ファイルは、リレーションシップとその他のメタデータとを関連付けるクラスは、データベース内のオブジェクトについて説明します。  .Tt ファイルは、T4 テンプレート コードを生成する、モデルに対して機能し、変更をデータベースに保存されます。 すべてのファイルのソリューション エクスプ ローラーで、Northwind_model ノードの下を確認できます。  

       ![ソリューション エクスプ ローラーの EF モデル ファイル](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata ソリューション エクスプ ローラーの EF モデル ファイル")  
  
     .Edmx ファイルのデザイナー画面では、いくつかのプロパティと、モデル内のリレーションシップを変更することができます。 デザイナーを使用して、このチュートリアルおはしません。  
  
6.  .Tt ファイルでは、汎用と WPF のデータ バインド、ObservableCollections を必要とすると共に使用するのいずれかを調整する必要があります。  ソリューション エクスプ ローラーでは、Northwind_model.tt が見つかるまで Northwind_model ノードを展開します。 (ことを確認する**いない**で、* です。コンテキスト .tt ファイルは、.edmx ファイルのすぐ下)。  
  
    -   2 回の出現を置換<xref:System.Collections.ICollection>で<xref:System.Collections.ObjectModel.ObservableCollection%601>です。  
  
    -   最初の出現箇所を置き換えます<xref:System.Collections.Generic.HashSet%601>で<xref:System.Collections.ObjectModel.ObservableCollection%601>51 'system.ftpserver です。 HashSet の 2 番目に出現を置換されません。  
  
    -   唯一の出現箇所を置き換えます<xref:System.Collections.Generic>('system.ftpserver 431) と<xref:System.Collections.ObjectModel>です。  
  
7.  キーを押して**Ctrl + Shift + B**プロジェクトをビルドします。 ビルドが完了したら、モデルのクラスは、データ ソース ウィザードに表示されます。  
  
今すぐお表示、移動したり、データを変更できるように、このモデルを XAML ページをフックする準備が整いました。  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Databind を XAML ページ モデル

データ バインド コードを記述することが実行するため、Visual Studio で自動的にはるかに簡単です。  
  
1.  メイン メニューから選択**プロジェクト > 新しいデータ ソースの追加**を呼び出すこと、**データ ソース構成ウィザード**です。 選択**オブジェクト**おをデータベースではないモデル クラスをバインドするため。  
  
     ![データ ソース構成ウィザードとオブジェクト ソース](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata オブジェクト ソースとデータ ソース構成ウィザード")  
  
2.  顧客を選択します。  (注文のソースが自動的に生成されます顧客の注文のナビゲーション プロパティからです。)  
  
     ![データ ソースとしてのエンティティ クラスの追加](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata エンティティの追加のデータ ソースとしてクラス")  
  
3.  をクリックして**完了**  
  
4.  コード ビューで MainWindow.xaml に移動します。 この例の目的を非常に単純な XAML を保存しようとしています。 わかりやすいものにメイン ウィンドウのタイトルを変更し、800 x 600 にここでは、高さと幅を大ききます。 常に変更します。 メイン グリッドの詳細については、顧客のその注文を表示するグリッドのいずれか 1 つのナビゲーション ボタンの 1 つの行にこれらの 3 つの行の定義を追加します。  

    ```xaml  
    <Grid.RowDefinitions>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="auto"/>  
            <RowDefinition Height="*"/>  
        </Grid.RowDefinitions>
    ```

5.  デザイナーで表示しているように MainWindow.xaml を開くようになりました。 これにより、Visual Studio ウィンドウの余白にツールボックスの横にある、オプションとして表示するデータ ソース ウィンドウ。 ウィンドウが開き、またはそれ以外の場合キーを押して タブをクリックして**Shift + Alt + D**かを選択して**ビュー &#124;です。その他の Windows &#124;です。データ ソース**です。 独自の個々 のテキスト ボックスに顧客クラス内の各プロパティを表示しようとしています。 最初に顧客のコンボ ボックスの下向き矢印をクリックし、選択**詳細**です。 中間の行に移動すると、デザイナーが認識できるようにデザイン サーフェイスの中央部にノードをドラッグします。  これを紛失した場合は、XAML で後から手動で行を指定できます。 既定では、グリッド要素では、コントロールが垂直方向に配置されますが、この時点でする位置に配置して、フォーム上と同様にします。  たとえば、賢明かもしれませんアドレス上の上部に [名前] ボックスを配置します。 この記事のサンプル アプリケーションは、フィールドの順序を変更し、それら 2 つの列を並べ替えます。  
  
     ![お客様のデータ ソースのバインドを個別のコントロール](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata 顧客のデータ ソース バインドを個別のコントロール")  
  
     コード ビューで表示されます、新しい`Grid`内の要素の行 1 (中央の行) グリッドの親です。 グリッドが、親、`DataContext`属性を参照に追加されている CollectionViewSource、`Windows.Resources`要素。 最初のテキスト ボックスなどのときに、そのデータ コンテキストを指定します。 その名前を"Address"をマップに、`Address`現在プロパティ`Customer`CollectionViewSource 内のオブジェクト。  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  

6.  顧客がウィンドウの上部に表示されている場合は、下にある自分の注文を半分を参照してくださいします。 1 つのグリッド ビュー コントロール内の注文を紹介します。 期待どおりに動作するマスター/詳細形式のデータ バインド、これが、注文クラス プロパティに、Customers、Orders の個別のノードがバインドが重要です。 次の図に注意してください。 デザイナーが 2 行目に配置されるようには、注文のクラスのプロパティ、顧客、フォームの下半分にドラッグします。  
  
     ![グリッドとして注文クラスをドラッグして](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata ドラッグ注文がグリッドとしてクラス")  
  
7.  Visual Studio では、UI コントロールをモデル内のイベントに接続するすべてのバインド コードを生成しました。 一部のデータを表示するのには、モデルを作成するコードを記述します。 最初 MainWindow.xaml.cs に移動し、データ コンテキストの MainWindow クラスにデータ メンバーを追加してみましょう。 うえで生成されたは、このオブジェクトでは、変更と、モデル内のイベントを追跡するコントロールのようなものは機能します。 また、コンス トラクターの初期化ロジックを追加します。 クラスの先頭は、次のようになります。  
  
     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]  
     
     追加、`using`ディレクティブに、負荷の拡張メソッドをスコープに取り込む System.Data.Entity です。  
  
     ```csharp
     using System.Data.Entity;  
     ```  

     スクロール ダウンし、Window_Loaded イベント ハンドラーを見つけるようになりました。 Visual Studio がご利用の米国 CollectionViewSource オブジェクトを追加していることを確認します。 これは、モデルを作成したときに選択した NorthwindEntities オブジェクトを表します。 みましょうメソッド全体が次のように見えるようになりましたように Window_Loaded にコードを追加します。  

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]  

8.  **F5**キーを押します。 CollectionViewSource に取得された最初の顧客の詳細を表示する必要があります。 データ グリッドにその注文も表示されます。 書式設定は、ではの修正をあまり良い外観です。 その他のレコードを表示し、基本的な CRUD 操作を実行する方法も作成します。  

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>ページのデザインを調整し、新しい顧客と注文のグリッドの追加

Visual Studio によって生成される既定の配置には適していませんアプリケーションでは、XAML でいくつかの変更を手動で行うおありますようにします。 新しい顧客や注文を追加するユーザーを有効にするいくつか"forms"を実際にはグリッド) を必要おがあります。 新しい顧客と注文を追加できるようにするには、するために、別の一連のテキスト ボックスにデータ バインドではない必要があります、`CollectionViewSource`です。 ハンドラー メソッドで、Visible プロパティを設定して、ユーザーが特定の時点で表示されるグリッドを管理します。 最後に、各グリッド行に、注文を個々 の注文を削除するユーザーを有効にする [削除] ボタンを追加します。  
  
まず、MainWindow.xaml の Windows.Resources 要素にこれらのスタイルを追加します。  
  
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
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
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
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
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
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
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

Windows フォーム アプリケーションでは、ボタンを持つ BindingNavigator オブジェクトを取得するデータベース内の行を移動すると、基本的な CRUD 操作を実行します。 WPF では、BindingNavigator が提供されませんが、簡単に作成します。 やってを水平方向の StackPanel 内のボタンを持つと分離コードでメソッドにバインドされているコマンドとボタンを関連付けることができましたがします。  
  
コマンドのロジックに 4 つの部分があります: (1)、コマンド、(2)、バインド、(3)、ボタン、および (4)、分離コード内のコマンド ハンドラー。  
  
### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML でのコマンド、バインディング、およびボタンを追加します。
  
1.  まず、MainWindow.xaml ファイル Windows.Resources 要素内のコマンドを追加してみましょう。  
  
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
  
2.  CommandBinding RoutedUICommand イベントを分離コードでメソッドにマップします。 終了タグ Windows.Resources 後に、この踏み込んで言うと要素を追加します。  
  
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
  
3.  今すぐみましょうナビゲーション StackPanel を追加、追加、削除およびボタンを更新します。 まず、Windows.Resources にこのスタイルを追加します。  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     次に、XAML ページの上部に向かって、外側のグリッド要素の RowDefinitions の直後にこのコードを貼り付けます。  
  
    ```xaml  
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
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
  
### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow クラスにコマンド ハンドラーを追加します。  
  
分離コードでは、追加および削除のメソッドを除く最小限です。 ナビゲーションは、メソッド、CollectionViewSource のビューのプロパティを呼び出すことによって実行されます。 DeleteOrderCommandHandler は、注文の連鎖削除を実行する方法を示します。 最初に、関連付けられている Order_Details に削除があります。 UpdateCommandHandler 新しい顧客や注文をコレクションに追加するか、だけで、テキスト ボックスに、ユーザーが加えた変更が既存の顧客や注文を更新します。  
  
これらのハンドラー メソッドを MainWindow.xaml.cs の MainWindow クラスに追加します。 Customers テーブルの CollectionViewSource に別の名前がある場合は、これらの各メソッドの名前を調整する必要があります。  
  
[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]  
  
## <a name="run-the-application"></a>アプリケーションの実行

デバッグを開始するには、**F5** キーを押します。 顧客と注文データのグリッドで、設定の表示し、ナビゲーション ボタンは期待どおりに動作する必要があります。 データを入力した後に、モデルに新しい顧客や注文を追加するには、「コミット」をクリックします。 データを保存せず、新しい顧客または新しい注文フォームからバックアップするには、「キャンセル」をクリックします。 既存の顧客と注文、テキスト ボックス内で直接編集を行うことができ、それらの変更がモデルに自動的に書き込まれます。  
  
## <a name="see-also"></a>関連項目

[.NET 用の Visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md)  
[Entity Framework のドキュメント](/ef/)