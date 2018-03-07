---
title: "Visual Studio での Xamarin Froms を使用したアプリ作成の基本事項 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2018
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d22b5186-9e03-4e85-afc9-7cbe28522a6d
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- xamarin
ms.openlocfilehash: 71470cd03844c7761afbd07c9d454214f5dc36ca
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2018
---
# <a name="learn-app-building-basics-with-xamarinforms-in-visual-studio"></a>Visual Studio での Xamarin Froms を使用したアプリ作成の基本事項

[Setup and install](../cross-platform/setup-and-install.md) と [Verify your Xamarin environment](../cross-platform/verify-your-xamarin-environment.md)の手順を完了すると、このチュートリアルでは、Xamarin.Forms を使用して基本アプリ (下図) を構築する方法を示します。 Xamarin.Forms を使用して、すべての UI コードを .NET Standard クラス ライブラリにいったん記述します。 そうすると、Xamarin は、iOS、Android、およびユニバーサル Windows プラットフォームのネイティブ UI コントロールを自動的にレンダリングします。 (Shared Project ではなく) この方法が推奨されます。 .NET Standard ライブラリには、すべての対象プラットフォームでサポートされる .NET API のみが含まれ、Xamarin.Forms ではプラットフォーム全体で UI コードを共有できるためです。  
  
![Android、iOS、Windows でのお天気アプリのサンプル](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
作成するには次の作業を行います。  
  
-   [ソリューションの設定](#solution)  
  
-   [共有データ サービス コードの記述](#dataservice)  
  
-   [共有 UI コードの記述の開始](#uicode)  
  
-   [Visual Studio Emulator for Android を使用してアプリをテストします。](#test)  
  
-   [プラットフォーム間で UI をネイティブの外観で終了する](#finish)  
  
> [!TIP]
> このプロジェクトの完全なソース コードは [GitHub の xamarin-forms-samples リポジトリ](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)にあります。  
  
##  <a name="solution"></a> ソリューションの設定  

次の手順では、共有コードの .NET Standard クラス ライブラリと 2 つの追加された NuGet パッケージを含む Xamarin.Forms ソリューションを作成します。  
  
1.  Visual Studio で、新しい**クロスプラットフォーム アプリ (Xamarin.Forms)** ソリューションを作成し、名前を **WeatherApp** とします。 左側にある一覧から **[Visual C#]** と **[クロスプラットフォーム]** を選択して、テンプレートを探します。  
  
     これがない場合は、Xamarin をインストールするか、Visual Studio 2017 の機能を有効にする必要があります。「[セットアップとインストール](../cross-platform/setup-and-install.md)」をご覧ください。  
  
     ![新しい空のアプリ &#40;クロスプラットフォーム Xamarin.Forms アプリ &#41; プロジェクトの作成](../cross-platform/media/crossplat-xamarin-formsguide-2.png "CrossPlat Xamarin FormsGuide 2")

2.  [OK] をクリックした後、オプションをいくつか選択することがあります。 **[空のアプリ]**、**[Xamarin.Forms]**、**[.NET Standard]** を選択します。

     ![クロスプラットフォーム アプリ プロジェクトの新規作成](../cross-platform/media/crossplat-xamarin-formsguide-3.png "CrossPlat Xamarin FormsGuide 3")
  
3.  ソリューションを作成するために [OK] をクリックすると、いくつかの個別のプロジェクトが表示されます。  
  
    -   **WeatherApp**: Xamarin.Forms を使用する共通のビジネス ロジックと UI コードを含む、プラットフォーム間で共有されるコードの記述先である .NET Standard ライブラリ。  
  
    -   **WeatherApp.Android**: ネイティブの Android コードを含むプロジェクト。 これは、既定のスタートアップ プロジェクトとして設定されます。  
  
    -   **WeatherApp.iOS**: ネイティブの iOS コードを含むプロジェクト。  
  
    -   **WeatherApp.UWP**: Windows 10 UWP コードを含むプロジェクト。  
  
    > [!NOTE]
    >  対象としていないプラットフォーム向けのプロジェクトは、自由に削除できます。   
  
     各ネイティブ プロジェクト内では、対応するプラットフォームのネイティブ デザイナーにアクセスでき、必要に応じてプラットフォーム固有の画面と機能を実装できます。  
  
4.  次の方法で、ソリューション内の Xamarin.Forms NuGet パッケージを最新の安定したバージョンにアップグレードします。 新しい Xamarin ソリューションを作成するたびに、これを行うことをお勧めします。  
  
    -   **[ツール] > [NuGet パッケージ マネージャー] > [ソリューションの NuGet パッケージの管理]** の順に選択します。  
  
    -   **[更新]** タブで、**Xamarin.Forms** のパッケージを確認し、ソリューション内のすべてのプロジェクトを確認して更新します。 (注: Xamarin.Android.Support については、すべての更新をオフのままにします。)  
  
    -   **[バージョン]** フィールドを利用可能な **最新の安定した** バージョンに更新します。  
  
    -   **[インストール]**をクリックします。  
  
         ![Xamarin.Forms NuGet パッケージの更新](../cross-platform/media/crossplat-xamarin-formsguide-4.png "CrossPlat Xamarin FormsGuide 4")  
  
5.  気象データ サービスから取得した情報を処理するのに使用する **Newtonsoft.Json** と NuGet パッケージを **WeatherApp** プロジェクトに追加します。  
  
    -   NuGet パッケージ マネージャー (手順 4 で開かれたままのもの) で、**[参照]** タブを選択して **Newtonsoft** を検索します。  
  
    -   **Newtonsoft.Json**を選択します。  
  
    -   **WeatherApp** プロジェクト (パッケージをインストールするのに唯一必要なプロジェクト) をチェックします。  
  
    -   **[バージョン]** フィールドが **最新の安定した** バージョンに設定されていることを確認してください。  
  
    -   **[インストール]**をクリックします。  
  
    ![Newtonsoft.Json NuGet パッケージの検索とインストール](../cross-platform/media/crossplat-xamarin-formsguide-5.png "CrossPlat Xamarin FormsGuide 5")  
  
6.  手順 5 を繰り返して、**Microsoft.Net.Http** パッケージを検索し、インストールします。  
  
7.  ソリューションをビルドし、ビルド エラーがないことを確認します。  
  
##  <a name="dataservice"></a> 共有データ サービス コードの記述  

**WeatherApp** プロジェクトには、すべてのプラットフォームで共有されている .NET Standard ライブラリ用のコードを記述します。 このライブラリは、iOS、Android、Windows 用のプロジェクトによってビルドされたアプリ パッケージに自動的に含まれます。  
  
このサンプルを実行するには、まず [http://openweathermap.org/appid](http://openweathermap.org/appid) で無料の API キーを申し込む必要があります。  
  
次の手順では、.NET Standard ライブラリにコードを追加して、気象サービスからのデータにアクセスし、そのデータを格納します。  
  
1.  **WeatherApp** プロジェクトを右クリックし、**[追加]、[クラス...]** の順に選択します。**[新しい項目の追加]** ダイアログで、ファイルに **Weather.cs**という名前を指定します。 このクラスは、気象データ サービスからのデータを保存するときに使用します。  
  
2.  **Weather.cs** の内容全体を次のコードで置き換えます。  
  
    ```csharp  
    namespace WeatherApp
    {
        public class Weather
        {
            // Because labels bind to these values, set them to an empty string to
            // ensure that the label appears on all platforms by default.
            public string Title { get; set; } = " ";
            public string Temperature { get; set; } = " ";
            public string Wind { get; set; } = " ";
            public string Humidity { get; set; } = " ";
            public string Visibility { get; set; } = " ";
            public string Sunrise { get; set; } = " ";
            public string Sunset { get; set; } = " ";
        }
    }
    ```  
  
3.  **WeatherApp** プロジェクト (**DataService.cs**) に別のクラスを追加します。これは、気象データ サービスからの JSON データを処理するのに使用します。  
  
4.  **DataService.cs** の内容全体を次のコードで置き換えます。  
  
    ```csharp  
    using System.Net.Http;  
    using System.Threading.Tasks;  
    using Newtonsoft.Json;  
    
    namespace WeatherApp  
    {  
        public class DataService  
        {  
            public static async Task<dynamic> getDataFromService(string queryString)  
            {  
                HttpClient client = new HttpClient();  
                var response = await client.GetAsync(queryString);  
  
                dynamic data = null;  
                if (response != null)  
                {  
                    string json = response.Content.ReadAsStringAsync().Result;  
                    data = JsonConvert.DeserializeObject(json);  
                }  
  
                return data;  
            }  
        }  
    }  
    ```  
  
5.  **WeatherApp** プロジェクト (**Core**) に 3 番目のクラスを追加します。ここには共有のビジネス ロジックを配置します。 このコードは、郵便番号を使用してクエリ文字列を生成し、気象データ サービスを呼び出し、**Weather** クラスのインスタンスにデータを取り込みます。  
  
6.  **Core.cs** の内容を次のコードで置き換えます。  
  
    ```csharp  
    using System;  
    using System.Threading.Tasks;  
  
    namespace WeatherApp  
    {  
        public class Core  
        {  
            public static async Task<Weather> GetWeather(string zipCode)  
            {  
                //Sign up for a free API key at http://openweathermap.org/appid  
                string key = "YOUR KEY HERE";  
                string queryString = "http://api.openweathermap.org/data/2.5/weather?zip="  
                    + zipCode + ",us&appid=" + key + "&units=imperial";  
  
                dynamic results = await DataService.getDataFromService(queryString).ConfigureAwait(false);  
  
                if (results["weather"] != null)  
                {  
                    Weather weather = new Weather();  
                    weather.Title = (string)results["name"];                  
                    weather.Temperature = (string)results["main"]["temp"] + " F";  
                    weather.Wind = (string)results["wind"]["speed"] + " mph";                  
                    weather.Humidity = (string)results["main"]["humidity"] + " %";  
                    weather.Visibility = (string)results["weather"][0]["main"];  
  
                    DateTime time = new System.DateTime(1970, 1, 1, 0, 0, 0, 0);  
                    DateTime sunrise = time.AddSeconds((double)results["sys"]["sunrise"]);  
                    DateTime sunset = time.AddSeconds((double)results["sys"]["sunset"]);  
                    weather.Sunrise = sunrise.ToString() + " UTC";  
                    weather.Sunset = sunset.ToString() + " UTC";  
                    return weather;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
        }  
    }  
    ```  
  
7.  **WeatherApp** ライブラリ プロジェクトをビルドし、コードが正しいことを確認します。  
  
##  <a name="uicode"></a> 共有 UI コードの記述の開始  

Xamarin.Forms を使用すると、.NET Standard ライブラリに共有 UI コードを実装できます。 次の手順では、前のセクションで追加した気象データ サービスのコードで返されるデータでテキストを更新するボタンを持つページを、プロジェクトに追加します。  
  
1.  **WeatherApp** プロジェクトを右クリックし、**[追加] > [新しい項目]** の順に選択して、**WeatherPage.cs** という名前の**コンテンツ ページ**を追加します。**[新しい項目の追加]** ダイアログ ボックスで **[コンテンツ ページ]** を選択します。 **[コンテンツ ページ (C#)]** や **[コンテンツ ビュー]** を選択しないように注意してください。 これに **WeatherPage.cs** という名前を付けます。  
  
     ![新しい Xamarin.Forms XAML ページを追加する](../cross-platform/media/crossplat-xamarin-formsguide-6.png "CrossPlat Xamarin FormsGuide 6")  
  
     Xamarin.Forms は XAML ベースのため、この手順では、入れ子にされた分離コード ファイル **WeatherPage.xaml.cs** と共に **WeatherPage.xaml**ファイルを作成します。 これにより、XAML またはコードで UI を生成することができます。 このチュートリアルでは、両方の一部を実行します。  
  
2.  WeatherPage 画面にボタンを追加するには、**WeatherPage.xaml** の内容を以下に置き換えます。  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
           xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
           x:Class="WeatherApp.WeatherPage"
           Title="Sample Weather App">  
      <Button x:Name="getWeatherBtn" 
              Text="Get Weather"
              Clicked="GetWeatherBtn_Clicked" />  
    </ContentPage>  
    ```  
  
     ボタンの名前は **x:Name** 属性を使用して定義する必要があることに注意してください。そうすると、分離コード ファイルでこのボタンを名前で参照することができます。  
  
3.  ボタンの **Clicked** イベントにイベント ハンドラーを追加してボタン テキストを更新するには、**WeatherPage.xaml.cs** の内容を次のコードで置き換えます  (自由に "60601" を別の郵便番号に変更することができます)。  
  
    ```csharp  
    using System;  
    using Xamarin.Forms;  
  
    namespace WeatherApp  
    {  
        public partial class WeatherPage: ContentPage  
        {  
            public WeatherPage()  
            {  
                InitializeComponent();  
  
                //Set the default binding to a default object for now  
                BindingContext = new Weather();  
            }  
  
            private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
            {  
                Weather weather = await Core.GetWeather("60601");  
                getWeatherBtn.Text = weather.Title;  
            }  
        }  
    }  
    ```  
  
4.  アプリの起動時に **WeatherPage** を最初の画面として開くには、 **App.cs** の既定のコンストラクターを次のコードで置き換えます。  
  
    ```csharp  
    public App()  
    {
        InitializeComponent();

        MainPage = new NavigationPage(new WeatherPage());  
    }  
    ```  
  
5.  **WeatherApp** プロジェクトをビルドし、コードが正しいことを確認します。  
  
##  <a name="test"></a> Visual Studio Emulator for Android を使用してアプリをテストします。  

これで、アプリを実行する準備ができました。 アプリが気象サービスからデータを取得していることを確認するには、今回は Android バージョンのみを実行します。 さらに UI 要素を追加した後で、iOS と UWP のバージョンも実行します。   
  
1.  **WeatherApp.Android** プロジェクトをスタートアップ プロジェクトに設定するには、そのプロジェクトを右クリックし、**[スタートアップ プロジェクトに設定]** を選択します。  
  
2.  Visual Studio ツールバーに、**WeatherApp.Android** がターゲット プロジェクトとして一覧表示されます。 デバッグ用の Android エミュレーターの 1 つを選択し、 **F5**キーをクリックします。 Visual Studio Emulator for Android でアプリを実行するための **VisualStudio** Emulator オプションの 1 つを使用することをお勧めします。  
  
     ![Android Emulator のデバッグ ターゲットを選択する](../cross-platform/media/crossplat-xamarin-formsguide-7.png "CrossPlat Xamarin FormsGuide 7")  
  
3.  エミュレーターでアプリが起動されたら、 **[Get Weather]** ボタンをクリックします。 ボタンのテキストが **Chicago** に更新されました。これは、気象サービスから取得されたデータの *Title* プロパティです。  
  
     ![ボタンのタップ前後のお天気アプリ](../cross-platform/media/crossplat-xamarin-formsguide-8.png "CrossPlat Xamarin FormsGuide 8")  
  
##  <a name="finish"></a>UI の外観をすべてのプラットフォームについてネイティブなものにする  

Xamarin.Forms は各プラットフォームのネイティブ UI コントロールをレンダリングして、アプリが自動的にネイティブな外観を持つようにします。 これをさらに見やすくするには、郵便番号用の入力フィールドで UI を終了し、サービスから返された気象データを表示します。  
  
1.  **WeatherPage.xaml** の内容を次のコードで置き換えます。 前述のように **x:Name** 属性を使用して名前が付けられた要素は、コードから参照できます。 Xamarin.Forms では多数の[レイアウト オプション](http://developer.xamarin.com/guides/xamarin-forms/controls/layouts/) (xamarin.com) も提供しています。 ここでは、WeatherPage は [Grid](http://developer.xamarin.com/api/type/Xamarin.Forms.Grid/) (xamarin.com) と [StackLayout](http://developer.xamarin.com/api/type/Xamarin.Forms.StackLayout/) (xamarin.com) を使用しています。  
  
    ```xaml  
    <?xml version="1.0" encoding="utf-8" ?>
    <ContentPage xmlns="http://xamarin.com/schemas/2014/forms"  
                 xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"  
                 x:Class="WeatherApp.WeatherPage"
                 Title="Sample Weather App">

        <ContentPage.Resources>
            <ResourceDictionary>
                <Style x:Key="labelStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Small" />
                    <Setter Property="TextColor" Value="#404040" />
                </Style>
                <Style x:Key="fieldStyle" TargetType="Label">
                    <Setter Property="FontSize" Value="Medium" />
                    <Setter Property="Margin" Value="10,0,0,0" />
                </Style>
            </ResourceDictionary>
        </ContentPage.Resources>

        <StackLayout>
            <Grid BackgroundColor="#545454" Padding="10, 10, 10, 10">
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="Auto" />
                </Grid.RowDefinitions>

                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="Auto" />
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="Auto" />
                </Grid.ColumnDefinitions>
            
                <Label Text="Search by Zip Code" 
                       Grid.Row="0" Grid.Column="0" Grid.ColumnSpan="3"
                       HorizontalOptions="Center"
                       TextColor="White" FontAttributes="Bold" FontSize="Medium" />
            
                <Label x:Name="zipCodeLabel" Text="Zip Code:" 
                       Grid.Row="1" Grid.Column="0"
                       VerticalOptions="Center"
                       Style="{StaticResource labelStyle}"
                       TextColor="#C0C0C0" />
            
                <Entry x:Name="zipCodeEntry"
                       Grid.Row="1" Grid.Column="1"
                       VerticalOptions="Center"
                       Margin="5,0"
                       BackgroundColor="DarkGray"
                       TextColor="White" />
            
                <Button x:Name="getWeatherBtn" Text="Get Weather" 
                        Grid.Row="1" Grid.Column="2"
                        HorizontalOptions="Center"
                        VerticalOptions="Center"
                        BorderWidth="1"
                        BorderColor="White"
                        BackgroundColor="DarkGray"
                        TextColor="White"
                        Clicked="GetWeatherBtn_Clicked" />
            </Grid>

            <ScrollView VerticalOptions="FillAndExpand">
                <StackLayout Padding="10,10,10,10" HorizontalOptions="Start">
                    <Label Text="Location" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Title}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Temperature" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Temperature}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Wind Speed" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Wind}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Humidity" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Humidity}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Visibility" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Visibility}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunrise" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunrise}" Style="{StaticResource fieldStyle}" />
                
                    <Label Text="Time of Sunset" Style="{StaticResource labelStyle}" />
                    <Label Text="{Binding Sunset}" Style="{StaticResource fieldStyle}" />
                </StackLayout>
            </ScrollView>
        </StackLayout>
    </ContentPage>  
     ```  
  
     ここでは示されていませんが、**[OnPlatform]** タグを使用すると、アプリが実行されている現在のプラットフォームに固有のプロパティ値を選択できます (「[Essential XAML Syntax](http://developer.xamarin.com/guides/xamarin-forms/user-interface/xaml-basics/essential_xaml_syntax/)」(xamarin.com) を参照)。 分離コード ファイルで、 [Device.OnPlatform API](http://developer.xamarin.com/guides/xamarin-forms/platform-features/device/) を同じ目的のために使用することができます。  
  
2.  **WeatherPage.xaml.cs**で、 **GetWeatherBtn_Clicked** イベント ハンドラーを次のコードで置き換えます。 このコードは、入力フィールドに郵便番号があることを確認し、その郵便番号のデータを取得し、全ページのバインド コンテキストを結果の **Weather** インスタンスに設定してから、ボタン テキストを "再検索" に設定します。 UI の各ラベルが **Weather** クラスのプロパティにバインドされるため、画面のバインド コンテキストを **Weather** インスタンスに設定すると、それらのラベルが自動的に更新されることに注意してください。  
  
    ```csharp  
    private async void GetWeatherBtn_Clicked(object sender, EventArgs e)  
    {  
        if (!String.IsNullOrEmpty(zipCodeEntry.Text))  
        {  
            Weather weather = await Core.GetWeather(zipCodeEntry.Text);  
            BindingContext = weather;  
            getWeatherBtn.Text = "Search Again";  
        }  
    }  
    ```  
  
3.  適切なプロジェクトを右クリックし、**[スタートアップ プロジェクトに設定]** を選択し、デバイスまたはエミュレーターかシミュレーターのいずれかでアプリを開始して、3 つのすべてのプラットフォーム (Android、iOS、Windows) 上でアプリを実行します。 有効な 5 桁の米国の郵便番号を入力し、**[Get Weather]** ボタンを押すと、その地域の気象データが次のように表示されます。 iOS プロジェクトのネットワーク上で Visual Studio が Mac OS X コンピューターに接続されている必要があります。  
  
     ![Android、iOS、Windows Phone でのお天気アプリのサンプル](../cross-platform/media/crossplat-xamarin-formsguide-1.png "CrossPlat Xamarin FormsGuide 1")  
  
このプロジェクトの完全なソース コードは [GitHub の xamarin-forms-samples リポジトリ](https://github.com/xamarin/xamarin-forms-samples/tree/master/Weather)にあります。