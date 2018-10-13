---
title: WPF と Entity Framework 6 で単純なデータ アプリケーションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 716e58acaddd1891f2e0d605265cb53bae4ad8d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299183"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF と Entity Framework 6 で単純なデータ アプリケーションを作成します。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルでは、SQL Server LocalDB、Northwind データベース、Entity Framework 6、および Windows Presentation Foundation と Visual Studio で基本的な「フォーム オーバー データ」のアプリケーションを作成する方法を示します。 マスター/詳細ビューでは、基本的なデータ バインドを行う方法を示していて、カスタム「バインド ナビゲーター」を「次に移動」ボタンを含む"Move Previous、"「を先頭へ移動」""への移動、終了があります「更新」および「削除します」。  
  
 この記事では、Visual Studio での data tools の使用について説明し、任意の深さの基になるテクノロジの説明を試行しません。 これにより、XAML、Entity Framework、および SQL の基礎知識があることを前提としています。 また、この例には MVVM アーキテクチャは、WPF アプリケーションの標準は示しません。 ただし、非常にいくつかの変更を MVVM アプリケーションに、このコードをコピーできます。  
  
## <a name="install-and-connect-to-northwind"></a>インストールし、Northwind に接続  
 この例では、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。 機能の他の SQL データベース製品でもその製品の ADO.NET データ プロバイダーは、Entity Framework をサポートしている場合。  
  
1.  SQL Server 2014 LocalDB Express 32 ビットからをインストールしていない場合、 [SQL Server のエディションのダウンロード ページ](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)します。  
  
2.  次の手順は、ここで、Northwind サンプル データベースをインストール:[サンプル データベースの SQL Server のインストール](../data-tools/install-sql-server-sample-databases.md)します。  
  
3.  [新しい接続を追加](../data-tools/add-new-connections.md)Northwind 用です。  
  
## <a name="configure-the-project"></a>プロジェクトを構成する  
  
1.  Visual Studio で、次のように選択します。**ファイル&#124;新しいプロジェクト**し、新しい c# WPF アプリケーションを作成します。  
  
2.  次に Entity Framework 6 の NuGet パッケージを追加します。 ソリューション エクスプ ローラーでプロジェクト ノードを選択します。 メイン メニューで、次のように選択します**プロジェクト&#124;NuGet パッケージの管理.。**  
  
     ![NuGet パッケージのメニュー項目を管理](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  NuGet パッケージ マネージャーで、クリックして、**参照**リンク。 Entity Framework は、一覧の最上位のパッケージでは可能性があります。 クリックして**インストール**右側のウィンドウで、画面の指示に従います。 出力ウィンドウがわかりますインストールが完了するとします。  
  
     ![Entity Framework NuGet パッケージ](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  今すぐ Visual Studio を使用して、Northwind データベースに基づくモデルを作成することができましています。  
  
## <a name="create-the-model"></a>モデルを作成する  
  
1.  ソリューション エクスプ ローラーでプロジェクト ノードを右クリックし、選択**追加&#124;新しい項目の**します。 [C#] ノードで、左側のウィンドウで次のように選択します。**データ**中央のペインで選択**ADO.NET Entity Data Model**します。  
  
     ![Entity Framework モデル新しいプロジェクト項目](../data-tools/media/raddata-ef-new-project-item.png "raddata EF の新しいプロジェクト項目")  
  
2.  モデルを呼び出す`Northwind_model`し、[ok] を選択します。 すると、 **Entity Data Model ウィザード**します。 選択**データベースの EF デザイナー**順にクリックします**次**します。  
  
     ![データベースから EF モデル](../data-tools/media/raddata-ef-model-from-database.png "raddata データベースから EF モデル")  
  
3.  次の画面で、LocalDB Northwind が選択に接続をクリックします**次**します。  
  
4.  ウィザードの次のページで、テーブル、ストアド プロシージャ、および Entity Framework モデルに含めるには、他のデータベース オブジェクトを選択します。 ツリー ビューで [dbo] ノードを展開し、顧客、注文および注文の詳細を選択します。 既定値をオンのままにし、をクリックして**完了**します。  
  
     ![モデルのデータベース オブジェクトの選択](../data-tools/media/raddata-choose-ef-objects.png "raddata EF オブジェクトの選択")  
  
5.  ウィザードでは、Entity Framework モデルを表す c# クラスが生成されます。 これらは、プレーンな古い c# クラスとは知りませんが、WPF ユーザー インターフェイスにデータをバインドします。 .Edmx ファイルには、リレーションシップおよびその他のクラスをデータベース内のオブジェクトに関連付けられるメタデータについて説明します。  .Tt ファイルは、モデルに対して機能し、変更、データベースに保存するコードを生成する T4 テンプレートです。 これらすべてのファイルでは、ソリューション エクスプ ローラー Northwind_model ノードの下を確認できます。  
  
     ![ソリューション エクスプ ローラーの EF モデル ファイル](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata ソリューション エクスプ ローラーの EF モデル ファイル")  
  
     .Edmx ファイルのデザイナー画面では、いくつかのプロパティと、モデル内のリレーションシップを変更することができます。 このチュートリアルでは、デザイナーを使用することはできません。  
  
6.  .Tt ファイルでは、汎用と ObservableCollections を必要とする WPF データ バインドで作業することのいずれかを調整する必要があります。  ソリューション エクスプ ローラーでは、Northwind_model.tt が見つかるまで Northwind_model ノードを展開します。 (必ず、**されません**で、*。コンテキスト .tt ファイルは、.edmx ファイルのすぐ下)。  
  
    -   2 つの箇所を置き換えます<xref:System.Collections.ICollection>で<xref:System.Collections.ObjectModel.ObservableCollection%601>します。  
  
    -   最初に見つかった位置の交換<xref:System.Collections.Generic.HashSet%601>で<xref:System.Collections.ObjectModel.ObservableCollection%601>51 の行の付近です。 2 番目に出現する HashSet は置き換えられません  
  
    -   唯一の一致を置き換える<xref:System.Collections.Generic>(約 334 行目) と<xref:System.Collections.ObjectModel>します。  
  
7.  キーを押して**Ctrl + Shift + B**プロジェクトをビルドします。 ビルドが完了したら、モデル クラスは、データ ソース ウィザードに表示されます。  
  
 これで表示、移動してデータを変更できる XAML ページには、このモデルをフックする準備が整いました。  
  
## <a name="databind-the-model-to-the-xaml-page"></a>XAML ページにモデルをデータ バインド  
 データ バインド コードを記述することが、その Visual Studio を使用する方が簡単です。  
  
1.  メイン メニューで、次のように選択します。**プロジェクト&#124;新しいデータ ソースの追加**を起動、**データ ソース構成ウィザード**します。 選択**オブジェクト**データベースではないモデル クラスにバインドしているためです。  
  
     ![オブジェクトのソースとデータ ソース構成ウィザード](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata オブジェクト ソースとデータ ソース構成ウィザード")  
  
2.  顧客を選択します。  (注文のソースが自動的に生成されます顧客の注文のナビゲーション プロパティから。)  
  
     ![データ ソースとしてのエンティティ クラスの追加](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata エンティティの追加は、データ ソースとしてクラス")  
  
3.  クリックして**完了**  
  
4.  コード ビューで MainWindow.xaml に移動します。 この例の目的を非常に単純な XAML を保持するでしょう。 わかりやすい MainWindow のタイトルを変更し、ここでは、800 600 x の高さと幅を増やします。 常に変更します。 メイン グリッドのナビゲーション ボタンは、顧客の詳細は、その注文を表示するグリッドのいずれか 1 つの 1 つの行にこれら 3 つの行の定義を追加します。  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  ここで、デザイナーで表示しているように、MainWindow.xaml を開きます。 これは、結果、データ ソース ウィンドウで、ツールボックスの横にある Visual Studio ウィンドウの余白のオプションとして表示します。 ウィンドウを開くか、それ以外の場合にキーを押します タブをクリックして**Shift + Alt + D**選択または**ビュー&#124;その他の Windows&#124;データ ソース**します。 独自の個々 のテキスト ボックス内の顧客クラスに各プロパティを表示するでしょう。 最初の顧客のコンボ ボックスの矢印をクリックし、選択**詳細**します。 中央の行に移動すると、デザイナーが認識できるようには、デザイン画面の中央部にノードをドラッグします。  これを紛失した場合は、XAML で後で手動で行を指定できます。 既定では、グリッド要素では、コントロールが垂直方向に配置されますが、この時点でする位置に配置して、フォームのようにします。  たとえば、有意義なことアドレス上の上部に [名前] ボックスを配置します。 この記事のサンプル アプリケーションでは、フィールドの順序を変更し、それら 2 つの列に並べ替えます。  
  
     ![個々 のコントロールを顧客のデータ ソース バインド](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata お客様のデータ ソース バインドを個別のコントロール")  
  
     コード ビューで確認できます、新しい`Grid`要素 1 の行の (中央の行) の親グリッド。 グリッドが親を`DataContext`属性に追加された CollectionViewSource を指します、`Windows.Resources`要素。 その名前を"Address"バインドは最初のテキスト ボックスに、たとえば、するときに、そのデータ コンテキストを指定にマップされて、`Address`プロパティ、現在の`Customer`CollectionViewSource 内のオブジェクト。  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  下には、その注文を半分見たい、顧客がウィンドウの上部に表示されている場合。 1 つのグリッド ビュー コントロール内の注文を紹介します。 期待どおりに動作するマスター-詳細データ バインドが Orders の個別のノードが、Customers クラスに Orders プロパティにバインドします重要です。 次の図に注意してください。 2 行目で、デザイナーに配置するため、顧客クラスの Orders プロパティをフォームの下半分にドラッグします。  
  
     ![グリッドとして注文クラスをドラッグして](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata ドラッグの注文をグリッドとしてクラス")  
  
7.  Visual Studio には、モデル内のイベントに UI コントロールを接続するすべてのバインド コードが生成されます。 一部のデータを表示するには、実行する必要がありますすべては、モデルを設定するコードを作成します。 最初 MainWindow.xaml.cs に移動し、データ コンテキストの MainWindow クラスにデータ メンバーを追加してみましょう。 このオブジェクトは、私たちが生成されたらには、変更や、モデル内のイベントを追跡するコントロールのようなものは機能します。 ここで私たちは、新しい顧客または新しい注文を追加する後で使用する 2 つのメンバーを追加します。 コンス トラクターの初期化ロジックも追加します。 このよう、クラスの先頭になります。  
  
    ```csharp  
    public partial class MainWindow : Window  
       {  
           public Customer newCustomer { get; set; }  
           public Order newOrder { get; set; }  
  
           NorthwindEntities context = new NorthwindEntities();  
           CollectionViewSource custViewSource;  
           CollectionViewSource ordViewSource;  
  
           public MainWindow()  
           {  
               InitializeComponent();  
               newCustomer = new Customer();  
               newOrder = new Order();  
               custViewSource = ((CollectionViewSource)  
                   (FindResource("customerViewSource")));  
               ordViewSource = ((CollectionViewSource)  
                   (FindResource("customerOrdersViewSource")));  
               DataContext = this;  
           }  
    ```  
  
     追加、 `using` Load 拡張メソッドをスコープに取り込む System.Data.Entity のディレクティブ。  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     今すぐ下にスクロールし、Window_Loaded イベント ハンドラーを検索します。 Visual Studio が私たちにとって、CollectionViewSource オブジェクトを追加することに注意してください。 これは、モデルを作成したときに選択した NorthwindEntities オブジェクトを表します。 みましょうメソッド全体は次のようになりますように Window_loaded にコードを追加します。  
  
    ```csharp  
    private void Window_Loaded(object sender, RoutedEventArgs e)  
        {  
            // Load is an extension method on IQueryable,    
            // defined in the System.Data.Entity namespace.   
            // This method enumerates the results of the query,    
            // similar to ToList but without creating a list.   
            // When used with Linq to Entities this method    
            // creates entity objects and adds them to the context.   
            context.Customers.Load();  
  
            // After the data is loaded call the DbSet<T>.Local property    
            // to use the DbSet<T> as a binding source.   
            custViewSource.Source = context.Customers.Local;  
        }  
    ```  
  
8.  **F5**キーを押します。 データ グリッドで、注文、CollectionViewSource に取得された最初の顧客の詳細を表示する必要があります。 書式設定ではありません、を修正しましょう。 他のレコードを表示する方法を作成し、基本的な CRUD 操作を実行します。  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>ページのデザインを調整し、新しい顧客と注文のグリッドを追加します。  
 Visual Studio によって生成される既定の配置は、XAML でいくつかの変更を手動で行うことはアプリケーションでは、適していません。 新しい顧客または新しい注文を追加するユーザーを有効にするいくつか"forms"(これは、実際にはグリッド) も必要になります。    新しい顧客と注文を追加できるようにするには、するには、別の一連のテキスト ボックスにデータ バインドではない必要があります、`CollectionViewSource`します。 ハンドラー メソッドで、Visible プロパティを設定して、特定の時点でユーザーに表示するグリッドを制御します。  
  
 最後に、個別の注文を削除するユーザーを有効にする注文のグリッド内の行ごとに Delete ボタンを追加します。  
  
 まず、Windows.Resources にこれらのスタイルを追加します。  
  
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
<Grid >  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>  
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
     </StackPanel>  
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
 Windows フォーム アプリケーションでは、データベース内の行を移動したりする基本的な CRUD 操作を行うのためのボタンを持つ BindingNavigator オブジェクトを取得します。 WPF には、BindingNavigator は示しませんが、簡単に作成できます。 ページのグリッドの一番下の行で水平方向の StackPanel 内のボタンを持つよいですし、ボタンの背後にあるコード内のメソッドにバインドされているコマンドに関連付けられたします。  
  
 コマンド ロジックを 4 つの部分があります: (1)、コマンド、(2)、バインド、(3)、ボタン、および分離コードでは、(4)、コマンド ハンドラー。  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML でのコマンド、バインディング、およびボタンを追加します。  
  
1.  まず、Windows.Resources 要素内で、MainWindow.XAML ファイルで、コマンドを追加してみましょう。  
  
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
  
2.  CommandBinding は、分離コード内のメソッドに特徴的な RoutedUICommand イベントをマップします。 終了タグ Windows.Resources 後に、この CommandBindings 要素を追加します。  
  
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
  
3.  今すぐみましょう、ナビゲーションを使用した、StackPanel の追加、追加、削除およびボタンを更新します。 まず、Windows.Resources にこのスタイルを追加します。  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     今すぐ XAML ページの上部で、外側の Grid 要素に各 Rowdefinition の直後にこのコードを貼り付けます。  
  
    ```xaml  
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>コマンド ハンドラーを MainWindow クラスに追加します。  
  
1.  分離コードは最小限の追加と削除メソッドは除きます。 CollectionViewSource のビューのプロパティでメソッドを呼び出すことによって、ナビゲーションが実行されることに注意してください。 DeleteOrderCommandHandler では、注文の連鎖削除を実行する方法を示します。 最初にそれに関連付けられている order_details テーブルを削除するがあります。 UpdateCommandHandler。 だけテキスト ボックスで行った変更任意で、既存のオブジェクトを更新そう、コレクションに新しい顧客を追加します。  
  
2.  これらの各メソッドの名前を調整する必要があります。、CollectionViewSource の Customers テーブル用に別の名前を MainWindow.xaml.cs の MainWindow クラスにこれらのハンドラー メソッドを追加します。  
  
    ```csharp  
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToLast();  
    }  
  
    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToPrevious();  
    }  
  
    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToNext();  
    }  
  
    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToFirst();  
    }  
  
    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // If existing window is visible, then delete the customer and all their orders.  
        // In a real application, you should add warnings and allow a user to cancel the operation.  
        var cur = custViewSource.View.CurrentItem as Customer;  
  
        var cust = (from c in context.Customers  
                    where c.CustomerID == cur.CustomerID  
                    select c).FirstOrDefault();  
  
        if (cust != null)  
        {  
            foreach (var ord in cust.Orders.ToList())  
            {  
                Delete_Order(ord);  
            }  
            context.Customers.Remove(cust);  
        }  
        context.SaveChanges();  
        custViewSource.View.Refresh();  
    }  
  
    // Commit changes from the new customer form, the new order form,  
    // or edits made to the existing customer form.  
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        if (newCustomerGrid.IsVisible)  
        {  
            // Create a new object because the old one  
            // is being tracked by EF now.  
            newCustomer = new Customer();   
            newCustomer.Address = add_addressTextBox.Text;  
            newCustomer.City = add_cityTextBox.Text;  
            newCustomer.CompanyName = add_companyNameTextBox.Text;  
            newCustomer.ContactName = add_contactNameTextBox.Text;  
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;  
            newCustomer.Country = add_countryTextBox.Text;  
            newCustomer.CustomerID = add_customerIDTextBox.Text;  
            newCustomer.Fax = add_faxTextBox.Text;  
            newCustomer.Phone = add_phoneTextBox.Text;  
            newCustomer.PostalCode = add_postalCodeTextBox.Text;  
            newCustomer.Region = add_regionTextBox.Text;  
  
            // Perform very basic validation  
            if (newCustomer.CustomerID.Length == 5)  
            {  
                // Insert the new customer at correct position:  
                int len = context.Customers.Local.Count();  
                int pos = len;  
                for (int i = 0; i < len; ++i)  
                {  
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)  
                    {  
                        pos = i;  
                        break;  
                    }  
                }  
                context.Customers.Local.Insert(pos, newCustomer);  
                custViewSource.View.Refresh();  
                custViewSource.View.MoveCurrentTo(newCustomer);  
            }  
            else  
            {  
                MessageBox.Show("CustomerID must have 5 characters.");  
            }  
  
            newCustomerGrid.Visibility = Visibility.Collapsed;  
            existingCustomerGrid.Visibility = Visibility.Visible;  
        }  
        else if (newOrderGrid.IsVisible)  
        {  
            // Order ID is auto-generated so we don't set it here.  
            // For CustomerID, address, etc we use the values from current customer.  
            // User can modify these in the datagrid after the order is entered.  
  
            newOrder.OrderDate = add_orderDatePicker.SelectedDate;  
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;  
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;  
            try  
            {  
                // Exercise for the reader if you are using Northwind:  
                // Add the Northwind Shippers table to the model.  
                // Acceptable ShipperID values are 1, 2, or 3.  
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"  
                    || add_ShipViaTextBox.Text == "3")  
                {  
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);  
                }  
                else  
                {  
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");  
                    return;  
                }  
            }  
            catch  
            {  
                MessageBox.Show("Ship Via must be convertible to int");  
                return;  
            }  
            try  
            {  
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);  
            }  
            catch  
            {  
                MessageBox.Show("Freight must be convertible to decimal.");  
                return;  
            }  
  
            // Add the order into the EF model  
            context.Orders.Add(newOrder);  
            ordViewSource.View.Refresh();  
        }  
  
        // Save the changes, either for a new customer, a new order  
        // or an edit in an existing customer or order  
        context.SaveChanges();  
    }  
  
    // Sets up the form so that user can enter data. Data is later  
    // saved when user clicks Commit.  
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Visible;  
  
        // Clear all the text boxes before adding a new customer.  
        foreach (var child in newCustomerGrid.Children)  
        {  
            var tb = child as TextBox;  
            if (tb != null)  
            {  
                tb.Text = "";  
            }  
        }  
    }  
  
    private void NewOrder_click(object sender, RoutedEventArgs e)  
    {  
        var cust = custViewSource.View.CurrentItem as Customer;  
        if (cust == null)  
        {  
            MessageBox.Show("No customer selected.");  
            return;  
        }  
  
        newOrder.CustomerID = cust.CustomerID;  
  
        // Get address and other mostly constant fields from   
        // an existing order, if one exists  
        var coll = custViewSource.Source as IEnumerable<Customer>;  
        var lastOrder = (from c in coll  
                         from ord in c.Orders  
                         select ord).LastOrDefault();  
        if (lastOrder != null)  
        {  
            newOrder.ShipAddress = lastOrder.ShipAddress;  
            newOrder.ShipCity = lastOrder.ShipCity;  
            newOrder.ShipCountry = lastOrder.ShipCountry;  
            newOrder.ShipName = lastOrder.ShipName;  
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;  
            newOrder.ShipRegion = lastOrder.ShipRegion;  
        }  
  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.UpdateLayout();  
        newOrderGrid.Visibility = Visibility.Visible;  
    }  
  
    // Cancels any input into the new customer form  
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        add_addressTextBox.Text = "";  
        add_cityTextBox.Text = "";  
        add_companyNameTextBox.Text = "";  
        add_contactNameTextBox.Text = "";  
        add_contactTitleTextBox.Text = "";  
        add_countryTextBox.Text = "";  
        add_customerIDTextBox.Text = "";  
        add_faxTextBox.Text = "";  
        add_phoneTextBox.Text = "";  
        add_postalCodeTextBox.Text = "";  
        add_regionTextBox.Text = "";  
  
        existingCustomerGrid.Visibility = Visibility.Visible;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
    }  
  
    private void Delete_Order(Order order)  
    {  
        // Find the order in the EF model.  
        var ord = (from o in context.Orders.Local  
                   where o.OrderID == order.OrderID  
                   select o).FirstOrDefault();  
  
        // Delete all the order_details that have  
        // this Order as a foreign key  
        foreach (var detail in ord.Order_Details.ToList())  
        {  
            context.Order_Details.Remove(detail);  
        }  
  
        // Now it's safe to delete the order.  
        context.Orders.Remove(ord);  
        context.SaveChanges();  
  
        // Update the data grid.  
        ordViewSource.View.Refresh();  
    }  
  
    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // Get the Order in the row in which the Delete button was clicked.  
        Order obj = e.Parameter as Order;  
        Delete_Order(obj);  
    }  
    ```  
  
3.  **F5**キーを押します。 データが表示され、ナビゲーション ボタンは期待どおりに動作する必要があります。 データを入力した後に、モデルに新しい顧客または注文を追加するには、「コミット」をクリックします。  保存せずに新しい顧客や新しい注文フォームからバックアップするには、"Cancel"をクリックします。 既存の顧客と注文、テキスト ボックス内で直接編集を行うことができ、それらの変更をモデルに自動的に書き込まれます。  
  
## <a name="see-also"></a>関連項目  
 [.NET 用の visual Studio データ ツール](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework ドキュメント](https://msdn.microsoft.com/data/ee712907.aspx)

