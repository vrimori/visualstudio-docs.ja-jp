---
title: リモートの IIS コンピューター上の ASP.NET Core のリモート デバッグ |Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 683e0cae09144777cbb27ef294676cc44dc0a1a1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830834"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Visual Studio 2017 でのリモートの IIS コンピューター上の ASP.NET Core のリモート デバッグ
IIS に配置されている ASP.NET アプリケーションをデバッグするには、インストールし、アプリをデプロイしたコンピューターでリモート ツールを実行して Visual Studio から、実行中のアプリにアタッチします。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

このガイドでは、設定、Visual Studio 2017 の ASP.NET Core を構成して、IIS にデプロイ、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。 ASP.NET 4.5.2 リモート デバッグを参照してください。[リモート IIS コンピューター上の ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)します。 配置して、Azure を使用して IIS 上でデバッグすることができますも。 Azure App Service は、容易に導入し、IIS といずれかを使用してリモート デバッガーの構成済みのインスタンス上でデバッグすることができます、[スナップショット デバッガー](../debugger/debug-live-azure-applications.md)または[サーバー エクスプ ローラーから、デバッガーのアタッチ](../debugger/remote-debugging-azure.md)します。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 8
* Windows Server 2016 および IIS 10

## <a name="requirements"></a>要件

プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での高待機時間またはダイヤルアップ、インターネットなどの低帯域幅接続経由またはインターネット経由でのデバッグは使用しないでと失敗は、ある非常に遅く。 要件の完全な一覧を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)します。

## <a name="app-already-running-in-iis"></a>アプリが IIS で既に実行されているか。

この記事には、Windows server 上の IIS の基本構成の設定および Visual Studio からアプリを展開する方法の手順が含まれています。 ここでは、サーバーにインストールされているアプリが正常に実行できることと、リモート デバッグする準備が整ったらコンポーネントに必要なあるかどうかを確認する手順。

* アプリが IIS で実行されていると、リモート デバッガーをダウンロードし、デバッグを開始に移動したい場合[をダウンロードして Windows Server のリモート ツールをインストール](#BKMK_msvsmon)します。

* アプリが設定されている、展開されると、かどうかを確認するのに役立つこのトピックのすべての手順に従いますデバッグできるように、IIS で正しく実行する場合は。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 のコンピューターで ASP.NET Core アプリケーションを作成します。 

1. 新しい ASP.NET Core アプリケーションを作成します。 (**ファイル > 新規 > プロジェクト**を選択し、 **Visual c# > Web > ASP.NET Core Web アプリケーション**)。

    **ASP.NET Core**テンプレート セクション**Web アプリケーション**します。

2. 確認します**ASP.NET Core 2.0**が選択されているを**Docker サポートを有効にする**は**いない**選択されていることと**認証**に設定されています。**認証なし**します。

3. プロジェクトに名前を**MyASPApp**  をクリック**OK**新しいソリューションを作成します。

4. [About.cshtml.cs] ファイルを開きにブレークポイントを設定、`OnGet`メソッド (以前のテンプレートでの代わりに HomeController.cs を開きでブレークポイントを設定、`About()`メソッド)。

## <a name="bkmk_configureIIS"></a> インストールし、Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(既定では有効です)、Internet explorer セキュリティ強化の構成が有効な場合は、一部の web サーバー コンポーネントをダウンロードするための信頼済みサイトとして、一部のドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**します。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むためのアクセス許可を与える要求を取得する可能性があります。 必須ではありませんが、プロセスを簡略化する次のようにクリックします。 これらのリソースのいくつか**追加**入力を求められたらします。

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server での ASP.NET Core をインストールします。

1. ホスティング システムに [.NET Core Windows Server ホスティング](https://aka.ms/dotnetcore-2-windowshosting) バンドルをインストールします。 このバンドルをインストールすることで、.NET Core ランタイム、.NET Core ライブラリ、ASP.NET Core モジュールがインストールされます。 詳細についての詳細な手順については、次を参照してください。 [IIS への発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)します。

    > [!NOTE]
    > システムにインターネット接続が設定されていない場合は、.NET Core Windows Server ホスティング バンドルをインストールする前に、*[Microsoft Visual C++ 2015 再頒布可能パッケージ](https://www.microsoft.com/download/details.aspx?id=53840)* を入手してインストールしてください。

3. システムを再起動します (または、コマンド プロンプトから **net stop was /y** の後に続けて **net start w3svc** を実行して、システム PATH への変更を適用します)。

## <a name="choose-a-deployment-option"></a>デプロイ オプションを選択します。

IIS にアプリをデプロイする必要があります問題が解決する場合は、これらのオプションを検討してください。

* Visual Studio での設定のインポートを IIS で発行設定ファイルを作成してデプロイします。 一部のシナリオをすばやくアプリをデプロイする方法です。 発行設定ファイルを作成するときに権限 IIS に自動的に設定されます。

* ローカルのフォルダーに発行し、推奨される方法によって、出力を IIS で準備済みのアプリ フォルダーにコピーしてデプロイします。

## <a name="optional-deploy-using-a-publish-settings-file"></a>(省略可能)発行設定ファイルを使用してデプロイします。

このオプションを使用する発行設定ファイルを作成し、Visual Studio にインポートします。

> [!NOTE]
> この展開方法では、Web Deploy を使用します。 Web 配置を手動で構成 Visual Studio で、設定をインポートする代わりにする場合は、ホスティング サーバーの Web デプロイ 3.6 ではなく Web デプロイ 3.6 をインストールできます。 ただし場合 Web Deploy 手動で構成する、する必要があります、サーバー上のアプリ フォルダーが正しい値とアクセス許可で構成されているかどうかを確認する (を参照してください[を構成する ASP.NET Web サイト](#BKMK_deploy_asp_net))。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>インストールし、Windows server ホスティング サーバーの Web 配置の構成

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS に発行設定ファイルを作成する

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートして配置する

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常に配置されたら、自動的に起動されます。 Visual Studio からアプリが起動しない場合は、IIS でアプリを起動します。 ASP.NET Core の場合、**DefaultAppPool** の [アプリケーション プール] フィールドが **[マネージド コードなし]** に設定されていることを確認する必要があります。

1. **設定**ダイアログ ボックスをクリックしてデバッグを有効にする **[次へ]**、選択、**デバッグ**構成を選び、**追加ファイルを削除移行先**下、**ファイル発行**オプション。

    > [!NOTE]
    > デバッグを無効にするリリース構成を選択した場合、 *web.config*ファイルの公開時にします。

1. クリックして**保存**し、アプリを再発行します。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(省略可能)ローカル フォルダーに発行してデプロイします。

このオプションを使用するには、RoboCopy、Powershell を使用して IIS にアプリケーションをコピーするか、ファイルを手動でコピーする場合は、アプリをデプロイします。

### <a name="BKMK_deploy_asp_net"></a> Windows Server コンピューターに ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後でデプロイされます。

2. 開くことがまだ開いていない場合、**インターネット インフォメーション サービス (IIS) マネージャー**します。 (サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして **[インターネット インフォメーション サービス (IIS) マネージャー]** を選択します。)

3. **接続**で左側のウィンドウに移動**サイト**します。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**します。

4. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

5. 設定、**エイリアス**フィールドを**MyASPApp**、アプリケーション プールの既定値を受け入れます (**DefaultAppPool**)、設定、**物理パス**に**C:\Publish**します。

6. **接続**、**アプリケーション プール**します。 開いている**DefaultAppPool**にアプリケーション プールのフィールドを設定および**マネージ コードなし**します。

7. IIS マネージャーで新しいサイトを右クリックし、選択**アクセス許可の編集**、その IUSR、IIS_IUSRS、または、ユーザーが web アプリへのアクセスは読み取りと実行権限を持つ権限を持つユーザー用に構成されたことを確認します。

    これらのアクセス権を持つユーザーのいずれかが表示されない場合は、読み取りと実行権限を持つユーザーとして IUSR を追加する手順を移動します。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>発行して、Visual Studio からローカル フォルダーにパブリッシュすることによって、アプリをデプロイ

発行し、ファイル システムまたはその他のツールを使用してアプリをデプロイすることもできます。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> ダウンロードして、Windows Server のリモート ツールのインストール

このチュートリアルでは、Visual Studio 2017 を使用します。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
## <a name="BKMK_setup"></a> Windows Server のリモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要がある追加のユーザーのアクセス許可を追加または変更した場合、認証モード、リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)します。

サービスとしてリモート デバッガーの実行方法の詳細については、次を参照してください。[リモート デバッガーをサービスとして実行](../debugger/remote-debugging.md#bkmk_configureService)します。

## <a name="BKMK_attach"></a> Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターでは、デバッグしようとしているソリューションを開きます (**MyASPApp**この記事では、すべての手順に従うかどうか)。
2. Visual Studio で、次のようにクリックします。**デバッグ > プロセスにアタッチ**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017 を使用して、以前にアタッチした同じプロセスに再アタッチできる**デバッグ > プロセスに再アタッチしています.**(Shift + Alt + P)。 

3. [修飾子] フィールドを「**\<リモート コンピューター名>:4022**」に設定します。
4. **[最新の情報に更新]** をクリックします。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが表示されない場合は、(ポートが必要です)、リモート コンピューター名ではなく IP アドレスを使用してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

    使用する場合、**検索**、ボタンをクリックする必要があります[UDP ポート 3702 を開く](#bkmk_openports)サーバー。

5. **[すべてのユーザーからのプロセスを表示する]** をオンにします。
6. すばやく検索するプロセス名の最初の文字を入力**dotnet.exe** (for ASP.NET Core)。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. **[アタッチ]** をクリックします。

8. リモート コンピューターの Web サイトを開きます。 ブラウザーで、**http://\<リモート コンピューター名>** に移動します。
    
    ASP.NET の Web ページが表示されるはずです。

9. 実行中の ASP.NET アプリケーションでリンクをクリックして、**について**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

## <a name="bkmk_openports">トラブルシューティング</a>Windows Server で必要なポートを開く

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure VM 上でポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic)します。

必要なポート:

- 80 に必要な IIS 用。
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)の詳細。
- 8172 - (Visual Studio からアプリのデプロイへの Web 配置の省略可能) が必要です。
- UDP 3702 - (省略可能) 検出ポート使用すると、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

1. Windows Server 上のポートを開くを開き、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**します。

2. クリックして**受信の規則 > 新しい規則 > ポート**、順にクリックします**次**。 (UDP 3702、選択**送信の規則**代わりにします)。

3. **特定のローカル ポート**をポート番号を入力し、をクリックして**次**します。

4. クリックして**接続を許可する**、 をクリックして**次**します。

5. ポートを有効にし、をクリックする 1 つまたは複数のネットワークの種類を選択します。**次**します。

    選ぶ種類には、リモート コンピューターが接続しているネットワークが含まれている必要があります。
6. 名を追加 (たとえば、 **IIS**、 **Web Deploy**、または**msvsmon**) の受信の規則をクリックします**完了**。

    [受信の規則] または [送信の規則] の一覧に新しい規則が表示されます。

    詳細について、Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)します。

3. その他の必要なポートの追加の規則を作成します。
