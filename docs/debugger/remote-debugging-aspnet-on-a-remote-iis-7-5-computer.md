---
title: リモートの IIS コンピューター上の ASP.NET のリモート デバッグ |Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 1a13488f632e3cf1f244449b2a7a4dbfd7869428
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826509"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>リモートの IIS コンピューター上の ASP.NET のリモート デバッグ
IIS に配置されている ASP.NET アプリケーションをデバッグするには、インストールし、アプリをデプロイしたコンピューターでリモート ツールを実行して Visual Studio から、実行中のアプリにアタッチします。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

このガイドでは、設定、Visual Studio 2017 ASP.NET MVC 4.5.2 アプリケーションを構成して、IIS にデプロイ、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。

> [!NOTE]
> リモートへの ASP.NET Core の代わりにデバッグを参照してください[IIS コンピューター上のリモート デバッグ ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)します。 Azure App Service は、容易に導入し、いずれかを使用して IIS の構成済みのインスタンス上でデバッグすることができます、[スナップショット デバッガー](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 が必要) または[サーバー エクスプ ローラーから、デバッガーのアタッチ](../debugger/remote-debugging-azure.md)。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 8 (Windows Server 2008 R2 の server 手順は異なります)

## <a name="requirements"></a>必要条件

リモート デバッガーは、Windows Server の Windows Server 2008 Service Pack 2 以降でサポートされます。 要件の完全な一覧を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)します。

> [!NOTE]
> プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での高待機時間またはダイヤルアップ、インターネットなどの低帯域幅接続経由またはインターネット経由でのデバッグは使用しないでと失敗は、ある非常に遅く。

## <a name="app-already-running-in-iis"></a>アプリが IIS で既に実行されているか。

この記事には、Windows server 上の IIS の基本構成の設定および Visual Studio からアプリを展開する方法の手順が含まれています。 ここでは、サーバーにインストールされているアプリが正常に実行できることと、リモート デバッグする準備が整ったらコンポーネントに必要なあるかどうかを確認する手順。

* アプリが IIS で実行されていると、リモート デバッガーをダウンロードし、デバッグを開始に移動したい場合[をダウンロードして Windows Server のリモート ツールをインストール](#BKMK_msvsmon)します。

* アプリが設定されている、展開されると、かどうかを確認するのに役立つこのトピックのすべての手順に従いますデバッグできるように、IIS で正しく実行する場合は。

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>ASP.NET 4.5.2 を作成する Visual Studio コンピューターでアプリケーション
  
1. MVC の ASP.NET アプリケーションを新規作成します。 (**ファイル > 新規 > プロジェクト**を選択し、 <strong>Visual C# > Web > ASP.NET Web アプリケーション。**ASP.NET 4.5.2 で</strong>テンプレート セクション**MVC**します。 確認します**Docker サポートを有効にする**が選択されていないことと**認証**に設定されている**認証なし**します。 プロジェクトに名前を**MyASPApp**)。

2. HomeController.cs ファイルを開き、 `About()` メソッドにブレークポイントを設定します。

## <a name="bkmk_configureIIS"></a> インストールし、Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(既定では有効です)、Internet explorer セキュリティ強化の構成が有効な場合は、一部の web サーバー コンポーネントをダウンロードするための信頼済みサイトとして、一部のドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**します。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むためのアクセス許可を与える要求を取得する可能性があります。 必須ではありませんが、プロセスを簡略化する次のようにクリックします。 これらのリソースのいくつか**追加**入力を求められたらします。

## <a name="BKMK_deploy_asp_net"></a> Windows Server での ASP.NET 4.5 をインストールします。

詳細な情報を IIS に ASP.NET をインストールする場合は、「 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

1. サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**します。

1. Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します**Web プラットフォームの新しいコンポーネントの取得**、ASP.NET の検索)。

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. システムの再起動 (実行または**net stop was/y**続けて**net start w3svc**システム パスに変更を適用するコマンド プロンプトから)。

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

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS での発行設定ファイルを作成します。

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートおよび展開

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常がデプロイした後、自動的に開始する必要があります。 Visual Studio からアプリが起動しない場合は、IIS でアプリを起動します。

1. **設定**ダイアログ ボックスをクリックしてデバッグを有効にする **[次へ]**、選択、**デバッグ**構成を選び、**追加ファイルを削除移行先**下、**ファイル発行**オプション。

    > [!NOTE]
    > デバッグを無効にするリリース構成を選択した場合、 *web.config*ファイルの公開時にします。

1. クリックして**保存**し、アプリを再発行します。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(省略可能)ローカル フォルダーに発行してデプロイします。

このオプションを使用するには、RoboCopy、Powershell を使用して IIS にアプリケーションをコピーするか、ファイルを手動でコピーする場合は、アプリをデプロイします。

### <a name="BKMK_deploy_asp_net"></a> Windows Server コンピューターに ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後でデプロイされます。

2. 開くことがまだ開いていない場合、**インターネット インフォメーション サービス (IIS) マネージャー**します。 (サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**で左側のウィンドウに移動**サイト**します。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**します。

5. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

6. 設定、**エイリアス**フィールドを**MyASPApp**、アプリケーション プールの既定値を受け入れます (**DefaultAppPool**)、設定、**物理パス**に**C:\Publish**します。

7. **接続**、**アプリケーション プール**します。 開いている**DefaultAppPool**にアプリケーション プールのフィールドを設定および**ASP.NET v4.0** (ASP.NET 4.5 は、アプリケーション プールのオプションではありません)。

8. サイトでは、IIS マネージャーで選択されて、次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、またはユーザーのアプリケーション プールが読み取りと実行権限を持つ権限を持つユーザー用に構成されたことを確認します。 これらのユーザーの [なし] が存在する場合は、読み取りと実行権限を持つユーザーとして IUSR を追加します。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>発行して、Visual Studio からローカル フォルダーにパブリッシュすることによって、アプリをデプロイ

発行し、ファイル システムまたはその他のツールを使用してアプリをデプロイすることもできます。

1. (ASP.NET 4.5.2)Web.config ファイルが .NET Framework の正しいバージョンを一覧表示されることを確認します。  たとえば、ASP.NET 4.5.2 を対象とする場合は、web.config にこのバージョンが表示されていることを確認すること。
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    たとえば、4.5.2 ではなく ASP.NET 4 をインストールする場合、バージョンは 4.0 をある必要があります。

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

1. Visual Studio コンピューターでは、デバッグしようとしているソリューションを開きます (**MyASPApp**この記事の手順に従っている場合)。
2. Visual Studio で、次のようにクリックします。**デバッグ > プロセスにアタッチ**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017 を使用して、以前にアタッチした同じプロセスに再アタッチできる**デバッグ > プロセスに再アタッチしています.**(Shift + Alt + P)。 

3. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4022**します。
4. クリックして**更新**します。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが表示されない場合は、(ポートが必要です)、リモート コンピューター名ではなく IP アドレスを使用してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

5. **[すべてのユーザーからのプロセスを表示する]** をオンにします。
6. すばやく検索するプロセス名の最初の文字を入力**w3wp.exe** ASP.NET 4.5。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. クリックして**アタッチ**

8. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動します。 **http://\<リモート コンピューター名 >** します。
    
    ASP.NET の Web ページが表示されるはずです。
9. 実行中の ASP.NET アプリケーションでリンクをクリックして、**について**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

## <a name="bkmk_openports"></a> トラブルシューティング: Windows Server で必要なポートを開く

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure VM 上でポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic)します。 

必要なポート:

- 80 に必要な IIS 用。
- 8172 - (Visual Studio からアプリのデプロイへの Web 配置のために必要な省略可能)
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)の詳細。
- UDP 3702 - (省略可能) 検出ポート使用すると、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

1. Windows Server 上のポートを開くを開き、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**します。

2. クリックして**受信の規則 > 新しい規則 > ポート**します。 選択**次へ** **特定のローカル ポート**をポート番号を入力し、をクリックして**次へ**、し**接続を許可する**、次へ をクリックし、名前を追加 (**IIS**、 **Web Deploy**、または**msvsmon**)、受信の規則にします。

    詳細について、Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)します。

3. その他の必要なポートの追加の規則を作成します。