---
title: Visual Studio 2017 の概要
ms.date: 02/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86522beb978dee5722a919c4fa0e3a9030d5f3ad
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="visual-studio-ide-overview"></a>Visual Studio IDE の概要

Visual Studio 統合開発環境 (IDE) は、ほぼすべての種類のコードを表示および編集可能で、Android、iOS、Windows、Web、およびクラウド用のアプリをデバッグ、ビルド、および発行するために使用できるクリエイティブなランチパッドです。 Mac 版と Windows 版が用意されています。 このトピックでは、Visual Studio IDE の機能を紹介します。 ここでは、Visual Studio で行うことができる作業の一部とインストールおよび使用方法、簡単なプロジェクトの作成方法、コードのデバッグと配置についての指針、各種ツール ウィンドウを紹介します。

## <a name="what-can-you-do-with-the-visual-studio-ide"></a>Visual Studio IDE でできること

Android スマートフォン用のアプリを 作成したり、 C++ を使用して最先端のゲームを 作成したり、それ以上のことも可能です。 Visual Studio には Web サイト、ゲーム、デスクトップ アプリ、モバイル アプリ、Office 用のアプリなどの作成をサポートするテンプレートが用意されています。

![Visual Studio のプロジェクト](../ide/media/VSIDE_Tour_Projects_List.png)

ほぼどこからでも入手できるコードをいくつか開いて操作することもできます。 GitHub にお好みのプロジェクトがある場合は、 そのリポジトリを複製して Visual Studio で開くだけでコーディングを開始できます。

### <a name="create-mobile-apps"></a>モバイル アプリの作成

C# や Xamarin (Visual C++) を使用して異なるプラットフォームのネイティブ モバイル アプリを作成したり、Apache Cordova で JavaScript を使用してハイブリッド アプリを作成したりできます。 Unity、Unreal、DirectX、Cocos 用のモバイル ゲームを作成できます。 Visual Studio には Android エミュレーターが搭載されているため、Android アプリの実行してデバッグできます。

Azure App Services を作成して、モバイル アプリにクラウドの機能を活用できます。 Azure App Services を活用すると、アプリのデータをクラウドに保存したり、ユーザーを安全に認証したり、アプリやビジネスのニーズに合わせてリソースを調整したりできます。 詳しくは、「[モバイル アプリ開発](https://www.visualstudio.com/vs/mobile-app-development/)」をご覧ください。

### <a name="create-cloud-apps-for-azure"></a>Azure 用のクラウド アプリの作成

Visual Studio には、Microsoft Azure を使用するクラウド ファーストのアプリケーションを簡単に作成できるツールのスイートが用意されています。 これにより、IDE から直接 Microsoft Azure でアプリケーションとサービスを簡単に構成、ビルド、デバッグ、パッケージ化、およびデプロイできます。 Azure Tools for .NET を入手するには、Visual Studio をインストールするときに **Azure 開発**ワークロードを選択します。 詳しくは、「[Visual Studio Tools for Azure](https://www.visualstudio.com/vs/azure-tools/)」をご覧ください。

次のような接続済みサービスを使用して、アプリに Azure のサービスを活用することができます。

- [Azure モバイル サービス](http://azure.microsoft.com/documentation/services/mobile-services/)

- [Azure ストレージ](http://azure.microsoft.com/documentation/services/storage/)

[HockeyApp](https://www.visualstudio.com/hockey-app/) では、ベータ版の配信、ライブ クラッシュ レポートの収集、実際のユーザーからのフィードバックの取得を行うことができます。 さらに、クラウドに格納されているデータに接続するために、Office 365 REST API を独自のアプリに統合できます。 詳細については、[これらの GitHub サンプル](https://github.com/OfficeDev/?utf8=%E2%9C%93&query=o365)を参照してください。

[Application Insights](https://marketplace.visualstudio.com/items?itemName=VisualStudioOnlineApplicationInsights.application-insights) は、アプリと Web サービスで品質の問題を検出して診断するのに役立ちます。 また、Application Insights は、ユーザー エクスペリエンスを最適化できるように、ユーザーが実際にアプリを使用して行う操作を理解するのに役立ちます。

### <a name="create-apps-for-the-web"></a>Web 用のアプリの作成

現在世界を動かしているのは Web であり、Visual Studio は Web 用のアプリの作成をサポートします。 Web アプリは ASP.NET、Node.js、Python、JavaScript、TypeScript を使用して作成できます。 Visual Studio は、Angular、jQuery、Express などの Web フレームワークを理解します。 ASP.NET Core と .NET Core は、Windows、Mac、Linux の各オペレーティング システムで実行できます。 [ASP.NET Core](http://www.asp.net/core/overview) は、MVC、WebAPI、および SignalR へのメジャー アップデートであり、Windows、Mac、および Linux で実行されます。  ASP.NET Core は、最新のクラウド ベースの Web アプリとサービスをビルドするための効率的で構成可能な .NET スタックを提供するために、まったく新たに設計されました。

詳細については、「[最新の Web ツール](https://www.visualstudio.com/vs/modern-web-tooling/)」をご覧ください。

### <a name="build-cross-platform-apps-and-games"></a>クロス プラットフォーム アプリとゲームをビルドする

Visual Studio を使用して、macOS、Linux、Windows 用のアプリおよびゲームをビルドし、Android、iOS、およびその他のモバイル デバイス用のアプリおよびゲームもビルドします。

- Windows、macOS、および Linux で実行される [.NET Core](/dotnet/core/) アプリをビルドします。

- [Xamarin](https://developer.xamarin.com/guides/cross-platform/windows/visual-studio/) を使用して、iOS、Android、および Windows 向けにモバイル アプリをビルドします。

- 標準的な Web テクノロジである &mdash;HTML、CSS、および JavaScript&mdash; を使用して iOS、Android、および Windows 用のモバイル アプリをビルドするには、[Apache Cordova](/visualstudio/cross-platform/tools-for-cordova/) を使用します。

- [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) を使用して、C# で 2D および 3D ゲームをビルドします。

- [C++ for Cross-Platform Development](../cross-platform/visual-cpp-for-cross-platform-mobile-development.md) を使用することによって、iOS、Android、および Windows デバイス対応のネイティブ C++ アプリをビルドし、iOS、Android、および Windows 用にビルドされたライブラリ内で共通コードを共有します。

- [Android エミュレーター](../cross-platform/visual-studio-emulator-for-android.md)で、Android アプリを展開、テスト、およびデバッグします。

Visual Studio は、他にも数多くのことを実行するのに役立ちます。 完全な一覧については、[www.visualstudio.com](https://www.visualstudio.com/vs/) を参照してください。

## <a name="install-the-visual-studio-ide"></a>Visual Studio IDE のインストール

まず、Visual Studio をダウンロードしてシステムにインストールします。 [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) のページからダウンロードできます。

Visual Studio はかつてないほど軽量になりました。 モジュラー インストーラーでは、*ワークロード* (好みのプログラミング言語やプラットフォームで必要な機能のグループ) を選択してインストールできます。 この方法により、Visual Studio のインストールのフットプリントがかつてないほど小さくなり、インストールと更新に要する時間が短縮されました。 Visual Studio 2017 では、インストール パフォーマンスが強化されただけでなく、IDE の起動時間とソリューションの読み込み時間が短縮されました。

お使いのシステムに Visual Studio をセットアップする方法について詳しくは、「[Visual Studio 2017 のインストール](../install/install-visual-studio.md)」をご覧ください。 [プログラムの作成](#create-a-program)手順に従う場合は、インストール時に必ず、**[.NET Core クロスプラットフォームの開発]** ワークロードを選択します。

![Visual Studio インストーラー](../ide/media/overview-net-core-workload.png)

## <a name="sign-in"></a>サインイン

Visual Studio を初めて起動する際には、Microsoft アカウント、仕事用アカウント、または学校用アカウントを使ってサインインすることもできます。 サインインすると、ウィンドウ レイアウトなどの Visual Studio の設定を複数のデバイス間で同期できます。 また、Azure サブスクリプションや [Visual Studio Team Services](/vsts/) など、必要になる可能性のあるサービスに自動的に接続されます。

## <a name="create-a-program"></a>プログラムの作成

あることを学ぶ方法の 1 つは実際に使ってみることです。 簡単なプログラムを新しく作成してみましょう。

1. Visual Studio を開きます。 メニューで、**[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

  ![メニュー バーで [ファイル]、[新しいプロジェクト] の順に選択します。](../ide/media/VSIDE_Tour_NewProject1.png)

1. **[新しいプロジェクト]** ダイアログ ボックスには複数のプロジェクト テンプレートが表示されます。 **[Visual C#]** で **[.NET Core]** カテゴリを選択し、**[Console App (.NET Core)]\(コンソール アプリ (.NET Core)\)** テンプレートを選択します。 **[名前]** テキスト ボックスに "HelloWorld" と入力します。 **[OK]** ボタンを選択します。

  ![.NET Core アプリ テンプレート](../ide/media/overview-new-project-dialog.png)

  > [!NOTE]
  > **[.NET Core]** カテゴリが表示されない場合は、**[.NET Core クロスプラットフォームの開発]** ワークロードをインストールする必要があります。 これを実行するには、**[新しいプロジェクト]** ダイアログ ボックスの左下側の **[Visual Studio インストーラーを開く]** リンクをクリックします。 **Visual Studio インストーラー**が開いたら、**[.NET Core クロスプラットフォームの開発]** ワークロードまで下にスクロールして選択してから **[変更]** を選択します。

   Visual Studio は、テンプレートを使用してプロジェクトを作成します。 これは、リテラル文字列 "Hello World!" を表示する <xref:System.Console.WriteLine> メソッドを呼び出す単純な "Hello World" アプリケーションです。 コンソール ウィンドウに表示します。

1. まもなく、次のスクリーンショットのような画面が表示されます。

  ![Visual Studio IDE](../ide/media/overview-ide-console-app.png)

   アプリケーションの C# コードは領域の大部分を占めるエディター ウィンドウに表示されます。 コードの構文は、キーワードや型など、コードの種類に応じて自動的に色分けされます。 また、コードの縦の小さな点線は互いに一致する括弧を示し、行番号は後でコードの場所を探すのに役立ちます。 小さな四角で囲まれたマイナス記号を選択するとコードが折りたたまれ、折りたたまれている場合は展開できます。 このコードのアウトライン機能を使用すると、必要のないコードを非表示にして画面を整理できます。

   プロジェクト ファイルは右側の**ソリューション エクスプローラー**と呼ばれるウィンドウに一覧表示されます。

  ![赤色のボックスを持つ Visual Studio IDE](../ide/media/overview-ide-console-app-red-boxes.png)

  他にもメニューやツール ウィンドウが用意されていますが、今は次に進みましょう。

1. アプリを起動します。 そのためには、メニュー バーの **[デバッグ]** メニューから **[デバッグなしで開始]** を選択します。 あるいは、**Ctrl** + **F5 キー**を押します。

  ![[デバッグ]、[デバッグなしで開始] メニューを選択](../ide/media/overview-start-without-debugging.png)

  Visual Studio でアプリがビルドされ、コンソール ウィンドウが開き、メッセージ "Hello World!" が表示されます。 これで実行中のアプリができました。

  ![コンソール ウィンドウ](../ide/media/overview-console-window.png)

1. コンソール ウィンドウを閉じるには、キーボードで任意のキーを押します。

1. 何らかの追加コードをアプリに追加しましょう。 `Console.WriteLine("Hello World!");` という行の前に次の C# コードを追加します。

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   このコードは、"What is your name?" と コンソール ウィンドウで、ユーザーが何らかの文字列を入力して **Enter** キーを押すまで待機します。

1. ここで、`Console.WriteLine("Hello World!");` という行を次のコードに変更します。

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. **[デバッグ]** > **[デバッグなしで開始]** の順に選択するか、**Ctrl** + **F5** キーを押してアプリを再び実行します。

   Visual Studio によってアプリが再度ビルドされ、コンソール ウィンドウが開き、名前を入力するように求められます。

1. コンソール ウィンドウに名前を入力し、**Enter** キーを押します。

   ![コンソール ウィンドウの入力](media/overview-console-input.png)

1. 任意のキーを押して、コンソール ウィンドウを閉じます。

## <a name="debug-test-and-improve-your-code"></a>デバッグとテストによるコードの改善

いつもすべてが完璧にうまく行くとは限りません。 コードを記述する際には、バグの存在やパフォーマンスを確認するために実際に実行してテストする必要があります。 Visual Studio の最新のデバッグ システムを使うと、ローカル プロジェクト、リモート デバイス、またはエミュレーター ([Android デバイス用](../cross-platform/visual-studio-emulator-for-android.md)など) で実行されるコードをデバッグできます。 一度に 1 つのステートメントずつ、コードを実行して必要に応じて変数を検査できます。 指定した条件が True の場合にのみヒットするブレークポイントを設定することができます。 コードの実行中に変数の値などを監視できます。 すべてコード エディター自体で管理できるため、コードを離れる必要はありません。 Visual Studio でのデバッグの詳細については、[デバッガーの機能ツアー](../debugger/debugger-feature-tour.md)に関するページをご覧ください。

テストについては、Visual Studio には単体テスト、IntelliTest、負荷およびパフォーマンス テストなどが用意されています。 テストの詳細については、「[開発者用テスト ツール、シナリオ、および機能](../test/developer-testing-scenarios.md)」を参照してください。 アプリのパフォーマンスを改善する方法の詳細については、「[プロファイリング機能ツアー](../profiling/profiling-feature-tour.md)」をご覧ください。

## <a name="deploy-your-finished-application"></a>完成したアプリケーションを配置する

アプリケーションをユーザーやお客様に配置する用意ができたら、Visual Studio で配置するためのツールが提供されます。Microsoft ストアや SharePoint サイトに配置する場合でも、InstallShield または Windows インストーラー テクノロジを利用する場合でも提供されます。 これはすべて、IDE を使用してアクセスできます。 詳細については、「[アプリケーション、サービス、およびコンポーネントの配置](../deployment/deploying-applications-services-and-components.md)」をご覧ください。

## <a name="quick-tour-of-the-ide"></a>IDE のクイック ツアー

Visual Studio の全体像を視覚的に確認できるように、次のイメージには Visual Studio で開かれたプロジェクトと使用する可能性の高いいくつかの主なツール ウィンドウが示されています。

- [ソリューション エクスプローラー](../ide/solutions-and-projects-in-visual-studio.md)では、コード ファイルを表示、移動、および管理できます。 ソリューション エクスプローラーでは、ファイルをソリューションやプロジェクトにまとめ、コードを整理できます。

- 大部分の時間を費やすことになる [[エディター]](../ide/writing-code-in-the-code-and-text-editor.md) ウィンドウではコードが表示され、ソース コードの編集や UI の設計を行うことができます。

- [[出力]](../ide/reference/output-window.md) ウィンドウには、デバッグ メッセージ、エラー メッセージ、コンパイラの警告、公開状態メッセージなど、Visual Studio の通知が出力されます。 メッセージ ソースごとに独自のタブがあります。

- [チーム エクスプローラー (VSTS)](/vsts/user-guide/work-team-explorer) では、[Git](https://git-scm.com/) や [Team Foundation バージョン管理 (TFVC)](/vsts/tfvc/overview) などのバージョン管理テクノロジを使用して、作業項目を追跡し、コードを他のユーザーと共有できます。

- [クラウド エクスプローラー](/azure/vs-azure-tools-resources-managing-with-cloud-explorer)では、仮想マシン、テーブル、SQL データベースなどの Azure リソースを表示および管理することができます。 特定の操作で Azure Portal が必要な場合、Cloud Explorer でリンクが提供されます。そのリンクから Azure Portal に移動できます。

![Visual Studio IDE](../ide/media/visualstudioide.png)

Visual Studio には他にも次のような一般的な生産性を高める機能が用意されています。

- [クイック起動](../ide/reference/quick-launch-environment-options-dialog-box.md)検索ボックスは、Visual Studio で必要な情報を迅速に見つけるに役立ちます。 探している内容を表す名前を入力するだけで、Visual Studio に結果がリストされ、目的の場所に正確に移動できます。 また、**クイック起動**にはすべてのワークロードまたは個々のコンポーネントに対応する Visual Studio インストーラーを起動するリンクが表示されます。

  ![クイック起動検索ボックス](../ide/media/VSIDE_Tour_QuickLaunch.png)

- [リファクタリング](../ide/refactoring-in-visual-studio.md)。これには、変数の名前をインテリジェントに変更する、選んだコード行を別個の関数に移動する、コードを他の場所に移動する、関数パラメーターを並べ替える、などの操作が含まれます。

 ![リファクタリング](../ide/media/VSIDE_refactor.png)

- **IntelliSense** 。コードに関する型情報をエディターに直接表示したり、場合によっては、ちょっとしたコードを自動的に作成したりする、よく使われる機能セットの包括的な用語です。 エディター内のインラインに基本ドキュメントがあるようなもので、これによって、別個のヘルプ ウィンドウで型情報を検索する手間が省けます。 IntelliSense 機能は言語によって異なります。 詳細については、「[C# の IntelliSense](../ide/visual-csharp-intellisense.md)」、「[Visual C++ の IntelliSense](../ide/visual-cpp-intellisense.md)」、「[JavaScript IntelliSense](../ide/javascript-intellisense.md)」、および [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md) に関するページを参照してください。 次の図は、職場でのいくつかの IntelliSense 機能を示しています。

  ![Visual Studio のメンバーの一覧](../ide/media/vs2017_Intellisense.png)

- **波線**は波打った赤の下線で、コード入力時にエラーや潜在的な問題をリアルタイムに警告します。 これにより、コンパイル時や実行時にエラーが検出されるのを待たずに即時に修正できます。 破線の上に移動すると、エラーに関する追加情報が表示されます。 電球がエラーの修正方法に関する提案とともに左余白に表示される場合もあります。 詳細については、[クイック アクション](../ide/quick-actions.md)に関するページを参照してください。

 ![波線](../ide/media/vs2017_squiggle.png)

- [[呼び出し階層]](../ide/reference/call-hierarchy.md) ウィンドウはテキスト エディターのコンテキスト メニューで開き、キャレット (挿入ポイント) の下のメソッドを呼び出す、またはそのメソッドによって呼び出されるメソッドを表示することができます。

 ![[呼び出し階層] ウィンドウ](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)。コードへの参照および変更、リンクされたバグ、作業項目、コード レビュー、単体テストをすべて、エディターを離れずに検索できます。

 ![CodeLens](../ide/media/codelensoverview.png)

- [ [ピークの定義](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) ] ウィンドウ。現在のコンテキストから移動せずに、メソッドまたは型の定義インラインが表示されます。

 ![ピークの定義](../ide/media/VSIDE_peek_definition.png)

- **[定義に移動]** コンテキスト メニュー オプション。関数またはオブジェクトが定義されている場所に直接移動します。 エディターを右クリックすることで、その他のナビゲーション コマンドも使用できます。

 ![定義へ移動](../ide/media/VSIDE_go_to_definition.png)

## <a name="manage-your-source-code-and-collaborate-with-others"></a>ソース コードの管理および他のユーザーとの共同作業

GitHub などの任意のプロバイダーがホストしている Git リポジトリにあるソース コードを管理できます。 また、[Visual Studio Team Services (VSTS)](/vsts/index) を使用して、プロジェクト全体でコードをバグおよび作業項目と共に管理することもできます。 Visual Studio でチーム エクスプローラーを使用して Git リポジトリを管理する方法の詳細については、[Git および Team Services (VSTS) の概要](/vsts/git/gitquickstart?tabs=visual-studio)に関するページを参照してください。 Visual Studio には、その他の組み込みのソース管理機能もあります。 それらの機能の詳細については、ブログ「[New Git Features in Visual Studio 2017](https://blogs.msdn.microsoft.com/visualstudioalm/2017/03/06/new-git-features-in-visual-studio-2017/)」(Visual Studio 2017 の新しい Git 機能) をご覧ください。

Visual Studio Team Services は、ソフトウェア プロジェクトをホストし、チームでのコラボレーションを有効にするためのクラウド ベースのサービスです。 VSTS は、Git ソース管理システムと Team Foundation ソース管理システムの両方をサポートしています。また、Scrum、CMMI、アジャイル開発方法もサポートしています。 Team Foundation バージョン管理 (TFVC) は、単一の集中サーバー リポジトリを使用して、ファイルを追跡してバージョン管理します。 ローカルの変更は常に集中サーバーにチェックインされます。他の開発者はそこで、最新の変更を取得できます。

Team Foundation Server (TFS) は、Visual Studio のアプリケーション ライフサイクル管理のハブです。 これにより、開発プロセスに関わるすべてのユーザーが 1 つのソリューションを使用して参加できるようになります。 TFS は、異種混合のチームやプロジェクトを管理するのにも役立ちます。

Visual Studio Team Services のアカウントまたは Team Foundation Server がネットワーク上にある場合、Visual Studio の **[チーム エクスプローラー]** ウィンドウから接続することができます。 このウィンドウからソース管理にコードをチェックインしたりソース管理からコードをチェックアウトできます。また、作業項目を管理したり、ビルドを開始したり、チームのルームやワークスペースにアクセスできます。 **チーム エクスプローラー**は、**[クイック起動]** ボックスから、**[ビュー]** > **[チーム エクスプローラー]** の順に選択してメイン メニューから、または **[チーム]** > **[接続の管理]** の順に選択して開くことができます。

次の図は、VSTS でホストされているソリューションの **[チーム エクスプローラー]** ウィンドウを示しています。

![Visual Studio Team Explorer](../ide/media/vs2017_teamexplorer.png)

チームの開発者がバージョン管理にチェックインしたコードをビルドするように、ビルド プロセスを自動化することもできます。 たとえば、1 つまたは複数のプロジェクトを夜間にビルドすることも、コードのチェックインごとにビルドすることもできます。 詳細については、「[Build and Release (VSTS and TFS)](/vsts/build-release/index)」(ビルドとリリース (VSTS と TFS)) を参照してください。

## <a name="connect-to-services-databases-and-cloud-based-resources"></a>サービス、データベース、クラウドベースのリソースへの接続

クラウドは現在のオンラインで繋がった世界では必須であり、Visual Studio はそれを活用する方法を提供します。 たとえば、接続済みサービス機能により、お使いのアプリをサービスに接続できます。 お使いのアプリでそのサービスを使用してデータを Azure ストレージなどに保存できます。

![接続済みサービス](../ide/media/VSIDE_Tour_Connected_Services.png)

**[接続済みサービス]** ページでサービスを選択すると、**接続済みサービス ウィザード**が起動します。このウィザードでは、プロジェクトを構成し、必要な NuGet パッケージをダウンロードして、サービスに対してコーディングを開始できます。

[Cloud Explorer](/azure/vs-azure-tools-resources-managing-with-cloud-explorer) を使用して、Visual Studio 内の Azure ベースのクラウド リソースを表示および管理できます。 Cloud Explorer には、ユーザーがログインしている Azure サブスクリプションで管理されているすべてのアカウントに含まれる Azure リソースが表示されます。 **Cloud Explorer** は、Visual Studio インストーラーで **Azure 開発**ワークロードを選択することで入手できます。

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

**サーバー エクスプローラー**は、ローカル、リモートで、また Azure、Salesforce.com、Office 365、および Web サイトで SQL Server インスタンスとアセットを参照および管理するのに役立ちます。 **サーバー エクスプローラー**を開くには、メイン メニューで **[表示]** > **[サーバー エクスプローラー]** の順に選択します。 サーバー エクスプローラーの使用方法について詳しくは、「[Add new connections](../data-tools/add-new-connections.md)」 (新しい接続の追加) をご覧ください。

[SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt) は、SQL Server、Azure SQL Database、Azure SQL Data Warehouse 用の強力な開発環境です。 データベースを構築、デバッグ、管理、およびリファクターできます。 データベース プロジェクトを操作したり、オンプレミスまたはオフプレミスで接続されたデータベース インスタンスを直接操作したりすることができます。

Visual Studio の **SQL Server オブジェクト エクスプローラー**では、SQL Server Management Studio と同様のデータベース オブジェクトのビューを提供します。 SQL Server オブジェクト エクスプローラーを使用すると、軽いデータベース管理と設計作業を実行できます。これには、SQL Server オブジェクト エクスプローラーのコンテキスト メニューを使用したテーブル データの編集、スキーマの比較、クエリの実行などが含まれます。

![SQL Server オブジェクト エクスプローラー](../ide/media/vs2015_sqlobjectexplorer.png)

## <a name="extend-visual-studio"></a>Visual Studio を拡張する

Visual Studio に必要な機能がない場合は、機能を追加できます。 ワークフローとスタイルに基づいて IDE をカスタマイズしたり、Visual Studio にまだ統合されていない外部ツールのサポートを追加したり、既存の機能を変更して生産性の向上を図ることができます。 Visual Studio 機能拡張ツール (VS SDK) の最新バージョンを検索するには、「 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。

.NET Compiler Platform ("Roslyn") を使って、独自のコード アナライザーとコード ジェネレーターを記述することができます。 必要なものはすべて [Roslyn](https://github.com/dotnet/Roslyn)に揃っています。

Microsoft 開発者や開発コミュニティが作成した Visual Studio の[既存の拡張機能](https://marketplace.visualstudio.com/vs) を検索してください。

Visual Studio の拡張について詳しくは、「[Visual Studio IDE を機能拡張する](https://www.visualstudio.com/vs/extend/)」をご覧ください。

## <a name="learn-more-and-find-out-whats-new"></a>詳細と新機能

Visual Studio を使用したことがない場合は、「[Visual Studio を使用した開発の開始](../ide/get-started-developing-with-visual-studio.md)」を参照するか、[Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033) で利用できる無料の Visual Studio コースを確認してください。 Visual Studio 2017 の新機能については、「[Visual Studio 2017 の新機能](../ide/whats-new-in-visual-studio.md)」をご覧ください。

これで Visual Studio IDE のツアーを終わります。 主な機能について便利なヒントを得るのに役立ててください。

## <a name="see-also"></a>関連項目

* [Visual Studio IDE](https://www.visualstudio.com/vs/)
* [Visual Studio のダウンロード](https://www.visualstudio.com/downloads/)
* [Visual Studio ブログ](https://blogs.msdn.microsoft.com/visualstudio/)
* [Visual Studio フォーラム](https://social.msdn.microsoft.com/Forums/vstudio/home?category=visualstudio%2Cvsarch%2Cvsdbg%2Cvstest%2Cvstfs%2Cvsdata%2Cvsappdev%2Cvisualbasic%2Cvisualcsharp%2Cvisualc)
* [Microsoft Virtual Academy](https://mva.microsoft.com/)