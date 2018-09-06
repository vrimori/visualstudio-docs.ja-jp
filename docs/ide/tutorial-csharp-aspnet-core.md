---
title: Visual Studio での C# および ASP.NET Core の概要
description: Visual Studio を使用して C# で ASP.NET Core Web アプリを作成する方法について段階的に説明します。
ms.custom: ''
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb1532a76d9bc530146ba5a0f563bcaa9389226c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626709"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>チュートリアル: Visual Studio での C# および ASP.NET Core の概要

Visual Studio を使用する ASP.NET Core での C# 開発に関するこのチュートリアルでは、C# ASP.NET Core Web アプリを作成し、それを変更し、IDE の一部の機能を検討してアプリを実行します。

Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-project"></a>プロジェクトを作成する

まず、ASP.NET Core プロジェクトを作成します。 このプロジェクトの種類には、Web サイトで必要となるすべてのテンプレート ファイルが付属していますので、何も追加する必要はありません。

1. Visual Studio 2017 を開きます。

2. 上部のメニュー バーで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択します。 

3. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[Visual C#]**、**[Web]** の順に展開し、**[.NET Core]** を選択します。 中央のウィンドウで、**[ASP.NET Core Web アプリケーション]** を選択ます。 次に、ファイルに *MyCoreApp* という名前を付け、**[OK]** を選択します。

   ![Visual Studio IDE の [新しいプロジェクト] ダイアログ ボックスに示されている ASP.NET Core Web アプリケーション プロジェクト テンプレート](../ide/media/csharp-aspnet-choose-template-name-mycoreapp-mvc.png)

### <a name="add-a-workload-optional"></a>ワークロードを追加する (省略可能)

**ASP.NET Core Web アプリケーション** プロジェクト テンプレートが表示されない場合は、**ASP.NET と Web 開発**ワークロードを追加して取得できます。 コンピューターにインストールされている Visual Studio 2017 の更新プログラムに応じて、次の 2 つの方法のうちのいずれかでこのワークロードを追加することができます。

#### <a name="option-1-use-the-new-project-dialog-box"></a>オプション 1: [新しいプロジェクト] ダイアログ ボックスを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、**[Visual Studio インストーラーを開く]** リンクを選択します。

   ![[新しいプロジェクト] ダイアログ ボックスで [Visual Studio インストーラーを開く] リンクを選択する](../ide/media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio インストーラーが起動します。 **[ASP.NET と Web 開発]** ワークロードを選択してから **[変更]** を選択します。

   ![Visual Studio インストーラーの [.NET Core クロスプラットフォームの開発] ワークロード](../ide/media/quickstart-aspnet-workload.png)

   (新しいワークロードのインストールを続ける前に、Visual Studio を終了することが必要な場合があります。)

#### <a name="option-2-use-the-tools-menu-bar"></a>オプション 2: [ツール] メニュー バーを使用する

1. **[新しいプロジェクト]** ダイアログ ボックスを取り消します。 次に、上部のメニュー バーで、**[ツール]** > **[ツールと機能を取得]** の順に選択します。

1. Visual Studio インストーラーが起動します。 **[ASP.NET と Web 開発]** ワークロードを選択してから **[変更]** を選択します。

   (新しいワークロードのインストールを続ける前に、Visual Studio を終了することが必要な場合があります。)

### <a name="add-a-project-template"></a>プロジェクト テンプレートを追加する

1. **[新しい ASP.NET Core Web アプリケーション]** ダイアログ ボックスで、**[Web アプリケーション (モデル ビュー コントローラー)]** プロジェクト テンプレートを選択します。

1. 上部のドロップダウン メニューに **[ASP.NET Core 2.0]** が表示されていることを確認します。 次に、**[OK]** を選択します。

   ![[新しい ASP.NET Core Web アプリケーション] ダイアログ ボックス](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>ソリューションについて

このソリューションはモデル ビュー コントローラー (MVC) アーキテクチャ パターンに従います。このパターンでは、アプリが次の 3 つの主要なコンポーネントに分けられます。

* **モデル**には、アプリのデータを表すクラスが含まれます。 モデル クラスでは検証ロジックを使用して、そのデータにビジネス ルールを適用します。 通常、モデル オブジェクトはモデルの状態を取得して、データベースに格納します。
* **ビュー**は、アプリのユーザー インターフェイス (UI) を表示するコンポーネントです。 一般に、この UI ではモデル データが表示されます。
* **コントローラー**には、ブラウザー要求を処理するクラスが含まれます。 モデル データを取得し、応答を返すビュー テンプレートを呼び出します。 MVC アプリでは、ビューに情報のみが表示され、コントローラーがユーザーの入力と操作を処理して応答します。

MVC パターンは、従来のモノリシック アプリよりテストと更新が容易なアプリを作成するのに役立ちます。

## <a name="tour-your-solution"></a>ソリューションのツアーを体験する

 1. プロジェクト テンプレートでは、**MyCoreApp** という名前の単一の ASP.NET Core プロジェクトを使用してソリューションを作成します。 プロジェクト ノードを展開すると、その内容が表示されます。

    ![Visual Studio の ASP.NET ソリューション エクスプローラー](../ide/media/csharp-aspnet-solution-explorer-mycoreapp-mvc.png)

 1. **Controllers** フォルダーから *HomeController.cs* ファイルを開きます。

     ![Visual Studio のソリューション エクスプローラーの HomeController.cs ファイル](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 1. *HomeController.cs* ファイルを表示します。

     ![Visual Studio コード ウィンドウの HomeController.cs](../ide/media/csharp-aspnet-home-controller-code.png)

 1. プロジェクトには **Views** フォルダーもあり、ここには各コントローラーにマップされるサブフォルダーが含まれます。 たとえば、*/Home/About* パスのビュー CSHTML ファイル (HTML を拡張したもの) は、*Views/Home/About.cshtml* にあります。 そのファイルを開きます。

     ![Visual Studio のソリューション エクスプローラーの About.cshtml ファイル](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

    この CSHTML ファイルでは Razor 構文を使用して、標準タグとインライン C# の組み合わせに基づいて HTML をレンダリングします。

     ![Visual Studio コード ウィンドウの About.cshtml](../ide/media/csharp-aspnet-about-cshtml-code.png)

    >[!NOTE]
    > Razor の詳細については、[Razor 構文を使用する C# および ASP.NET の概要](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)に関するページを参照してください。

 1. プロジェクトには、Web サイトのルートである **wwwroot** フォルダーも含まれます。 その内容を表示するには、フォルダーを展開します。

     ![Visual Studio のソリューション エクスプローラーの wwwroot フォルダー](../ide/media/csharp-aspnet-solution-wwwroot.png)

    &mdash;CSS、イメージ、JavaScript ライブラリなど&mdash;の静的サイト コンテンツを、任意のパスに直接配置することができます。

 1. プロジェクトとそのパッケージ、およびアプリケーションを実行時に管理する構成ファイルがいくつかあります。 たとえば、既定のアプリケーション[構成](/aspnet/core/fundamentals/configuration)は *appsettings.json* に格納されます。 しかし、*appsettings.Development.json* を使用して、これらの設定をオーバーライドすることができます。 **appsettings.Development.json** ファイルを表示するには、**appsettings.json** ファイルを展開します。

     ![Visual Studio のソリューション エクスプローラーの構成ファイル](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-debug-and-make-changes"></a>実行、デバッグ、および変更

1. IDE の **[IIS Express]** ボタンを選択して、デバッグ モードでアプリをビルドして実行します  (または、**F5** キーを押すか、メニュー バーから **[デバッグ]、[デバッグの開始]** の順に選択します)。

     ![Visual Studio の [IIS Express] ボタンを選択する](../ide/media/csharp-aspnet-iis-express-button.png)

     > [!NOTE]
     > "**Web サーバー 'IIS Express' に接続できませんでした**" というエラー メッセージが表示された場合は、Visual Studio を閉じて、右クリックまたはコンテキスト メニューから **[管理者として実行]** オプションを使用して Visual Studio を開きます。 その後、アプリケーションをもう一度実行します。

1. Visual Studio でブラウザー ウィンドウが起動します。 **[バージョン情報]** を選択します。

   ![アプリのブラウザー ウィンドウで [バージョン情報] を選択する](../ide/media/csharp-aspnet-browser-page.png)

   たとえば、ブラウザーの **[バージョン情報]** ページには、*HomeController.cs* ファイルに設定されているテキストがレンダリングされます。

   ![[バージョン情報] ページでテキストを表示する](../ide/media/csharp-aspnet-browser-page-about.png)

1. ブラウザー ウィンドウを開いたまま、Visual Studio に戻ります。 *Controllers/HomeController.cs* を開きます (まだ開いていない場合)。

   ![Visual Studio のソリューション エクスプローラーから HomeController.cs ファイルを開く](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. **About** メソッドの最初の行にブレークポイントを設定します。 これを行うには、余白をクリックするか、行にカーソルを設定して **F9** キーを押します。

   この行では、*Views/Home/About.cshtml* の CSHTML ページでレンダリングされる **ViewData** コレクションのデータがいくつか設定されます。

   ![About.cshtml の About メソッドの最初の行にブレークポイントを設定する。  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. ブラウザーに戻り、**[バージョン情報]** ページを更新します。 これにより、Visual Studio のブレークポイントがトリガーされます。

1. Visual Studio で、**ViewData** メンバーにマウスを移動し、そのデータを表示します。

   ![About メソッドの ViewData メンバーを表示して詳細を見る](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. アプリケーションのブレークポイントを、追加する際に使用したものと同じメソッドを使用して削除します。

1. *Views/Home/About.cshtml* を開きます。

   ![ソリューション エクスプローラーで About.cshtml を選択する](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. テキストの **"additional"** を **"changed"** に変更して、ファイルを保存します。

   !["additional" というテキストを "changed" というテキストに変更する](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. ブラウザー ウィンドウに戻り、更新されたテキストを表示します  (変更したテキストが表示されない場合は、ブラウザーを更新してください)。

    ![ブラウザー ウィンドウを更新して、変更したテキストを表示する](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. ツール バーから **[デバッグの停止]** ボタンを選択して、デバッグを停止します  (または、**Shift**+**F5** キーを押すか、メニュー バーから **[デバッグ]** > **[デバッグの停止]** を選択します)。

   ![ツール バーで [デバッグの停止] ボタンを選択する](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="quick-answers-faq"></a>FAQ に対する簡単な回答

以下の簡単な FAQ で、主な概念をいくつか示します。

### <a name="what-is-c"></a>C# とは何ですか?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) は、堅牢でありながら習得しやすいように設計されたタイプ セーフなオブジェクト指向のプログラミング言語です。

### <a name="what-is-aspnet-core"></a>ASP.NET Core とは何ですか?

ASP.NET Core は、Web アプリやサービスなど、インターネットに接続されているアプリケーションを構築するためのオープンソースのクロスプラットフォーム フレームワークです。 ASP.NET Core アプリは .NET Core または .NET Framework で実行できます。 Windows、Mac、Linux 上で、ASP.NET Core アプリ クロスプラットフォームを開発して実行することができます。 ASP.NET Core は [GitHub](https://github.com/aspnet/home) でオープン ソースとして公開されています。

### <a name="what-is-visual-studio"></a>Visual Studio とは何ですか?

Visual Studio は、開発者向け生産性向上ツールの統合開発スイートです。 プログラムやアプリケーションを作成するために使用できるプログラムのようなものと考えてください。

## <a name="next-steps"></a>次の手順

これでこのチュートリアルは完了です。 C#、ASP.NET Core、Visual Studio IDE について少しはご理解いただけたかと思います。 C# と ASP.NET を使用する Web アプリまたは Web サイトの作成方法の詳細については、以下のチュートリアルに進んで確認してください。

> [!div class="nextstepaction"]
> [ASP.NET Core で MVC Web アプリを作成する](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x)
>
> [!div class="nextstepaction"]
> [ASP.NET Core で Razor ページ Web アプリを作成する](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>関連項目

[Visual Studio を使用して Azure App Service に Web アプリを発行する](..//deployment/quickstart-deploy-to-azure.md)