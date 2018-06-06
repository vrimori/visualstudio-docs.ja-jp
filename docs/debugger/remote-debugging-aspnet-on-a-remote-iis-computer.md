---
title: リモート デバッグの IIS のリモート コンピューター上の ASP.NET Core |Microsoft ドキュメント
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 607f4bb2bcce3d8895a4a07df8d70c866e7a6aab
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746931"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Visual Studio 2017 の IIS のリモート コンピューターでリモート デバッグの ASP.NET Core
IIS に配置されている ASP.NET アプリケーションをデバッグするには、インストールし、アプリが展開されているコンピューターでリモート ツールを実行して Visual Studio から、実行中のアプリにアタッチし、します。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

このガイドでは、設定、Visual Studio 2017 ASP.NET Core を構成して、IIS に展開、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。 ASP.NET 4.5.2 リモート デバッグを参照してください。[リモート IIS コンピューター上の ASP.NET のデバッグ](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)です。 配置して、Azure を使用して IIS 上でデバッグすることもできます。 Azure App Service を簡単に展開でき、IIS といずれかを使用してリモート デバッガーの構成済みのインスタンス上でのデバッグ、[スナップショット デバッガー](../debugger/debug-live-azure-applications.md)または[サーバー エクスプ ローラーから、デバッガーのアタッチ](../debugger/remote-debugging-azure.md)です。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 および IIS 8
* Windows Server 2016 および IIS 10

## <a name="requirements"></a>必要条件

プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での待機時間の長いまたはダイヤルアップ、インターネットなどの低帯域幅接続またはインターネット経由でのデバッグはお勧めしませんが失敗することも非常に遅くします。 要件の一覧については、次を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)です。

## <a name="app-already-running-in-iis"></a>アプリが既に IIS で実行されていますか。

この記事には、Windows server 上の IIS の基本的な構成設定、および Visual Studio からアプリの展開のステップが含まれます。 ここでは、サーバーがインストールされているアプリが正常に実行できることと、リモート デバッグする準備ができたらコンポーネントを必要なことを確認する手順。

* IIS で、アプリが実行されていて、リモート デバッガーをダウンロードし、デバッグを開始に移動したい[ダウンロードして、Windows Server のリモート ツールをインストール](#BKMK_msvsmon)です。

* アプリがセットアップされている、展開するかどうかを確認するのに役立つこのトピックのすべての手順に従いますをデバッグすることができるように、IIS で正しく実行する場合。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 コンピューター上の ASP.NET Core アプリケーションを作成します。 

1. 新しい ASP.NET Core アプリケーションを作成します。 (**ファイル > 新規 > プロジェクト**選択してから、 **Visual c# > Web > ASP.NET Core Web アプリケーション**)。

    **ASP.NET Core**テンプレート セクションで、 **Web アプリケーション**です。

2. 確認して**ASP.NET Core 2.0**が選択されているを**Docker のサポートを有効にする**は**いない**選択されていることと**認証**に設定されています。**認証なし**です。

3. プロジェクトの名前**MyASPApp**  をクリック**OK**新しいソリューションを作成します。

4. About.cshtml.cs ファイルを開きにブレークポイントを設定、`OnGet`メソッド (既存のテンプレートで HomeController.cs 代わりに開きにブレークポイントを設定、`About()`メソッド)。

## <a name="bkmk_configureIIS"></a> インストールして Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(これは既定で有効)、Internet explorer セキュリティ強化の構成が有効な場合は、いくつかの web サーバー コンポーネントをダウンロードするために信頼済みサイトとしていくつかのドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**です。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むための権限を許可する要求を取得することがあります。 これらのリソースの一部は必要ありません、クリックしてプロセスを簡易化、**追加**されたらです。

## <a name="install-aspnet-core-on-windows-server"></a>Windows Server での ASP.NET Core をインストールします。

1. インストール、 [.NET コア Windows Server をホストしている](https://aka.ms/dotnetcore-2-windowshosting)ホスト システムにバンドルできます。 バンドルは、.NET Core ランタイム、.NET Core ライブラリ、および ASP.NET Core モジュールをインストールします。 複数の詳細な手順については、次を参照してください。[を IIS に発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)です。

    > [!NOTE]
    > システム持っていない場合、インターネット接続を入手してインストール、 *[Microsoft Visual C 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* .NET コア Windows Server をホストしているバンドルをインストールする前にします。

3. システムを再起動 (実行または**net stop が/y**続く**net 開始 w3svc**システム パスへの変更を取得するコマンド プロンプトから)。

## <a name="choose-a-deployment-option"></a>展開オプションを選択します

アプリを展開する、IIS にする必要がある場合は、これらのオプションを考慮してください。

* IIS で、発行設定ファイルを作成して、Visual Studio での設定をインポートして展開します。 シナリオによっては、これは、アプリの配置に高速な方法です。 発行設定ファイルを作成するときに権限 IIS で自動的に設定されます。

* ローカル フォルダーに発行し、IIS で準備済みのアプリのフォルダーに優先の方法で出力をコピーして展開します。

## <a name="optional-deploy-using-a-publish-settings-file"></a>(省略可能)発行設定ファイルを使用した展開します。

このオプションを使用する、発行設定ファイルを作成し、Visual Studio にインポートします。

> [!NOTE]
> この展開方法は、Web Deploy を使用します。 Web 配置を手動で構成 Visual Studio で、設定をインポートする代わりにする場合をホストしているサーバーの Web 展開 3.6 ではなく Web 展開 3.6 をインストールできます。 ただし、Web Deploy を手動で構成する場合、必要がありますに正しい値および権限を持つサーバー上のアプリ フォルダーが構成されていることを確認してください (を参照してください[を構成する ASP.NET Web サイト](#BKMK_deploy_asp_net))。

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>インストールして Windows Server 上のホスト サーバーの Web 配置を構成します。

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS に発行設定ファイルを作成します。

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定のインポートおよび展開

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常に配置した後、自動的に開始する必要があります。 Visual Studio からアプリが起動しない場合は、IIS でアプリを起動します。 ASP.NET core アプリケーション プールのフィールドをかどうかを確認する必要があります、 **DefaultAppPool**に設定されている**マネージ コードなし**です。

1. **設定**ダイアログ ボックスをクリックしてデバッグを有効にする**次**を選択、**デバッグ**構成を選択し**の追加ファイルを削除します。移行先**下にある、**ファイルを発行**オプション。

    > [!NOTE]
    > デバッグを無効にする、リリース構成を選択した場合、 *web.config*ファイルの公開時にします。

1. をクリックして**保存**し、アプリを再発行します。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(省略可能)ローカル フォルダーに発行して展開します。

このオプションを使用すると、Powershell、RoboCopy を使用して IIS にアプリケーションをコピーするか、ファイルを手動でコピーする場合、アプリを展開します。

### <a name="BKMK_deploy_asp_net"></a> Windows Server コンピューターで ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後で配置されます。

2. これがまだ開いていない場合は開きます、**インターネット インフォメーション サービス (IIS) マネージャー**です。 (サーバー マネージャーの左側のウィンドウで選択**IIS**です。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**左側のウィンドウに移動**サイト**です。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**です。

4. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

5. 設定、**エイリアス**フィールドを**MyASPApp**、既定のアプリケーション プール (**DefaultAppPool**)、し、設定、**物理パス**に**C:\Publish**です。

6. **接続****アプリケーション プール**です。 開いている**DefaultAppPool**にアプリケーション プール フィールドを設定および**マネージ コードなし**です。

7. IIS マネージャーで新しいサイトを右クリックし、選択**アクセス許可の編集**、その IUSR、IIS_IUSRS、または web アプリへのアクセスが承認された読み取りと実行権限を持つユーザー用に構成されたユーザーを確認します。

    これらのユーザーのアクセス権を持つ 1 つ表示されない場合は、読み取りと実行権限を持つユーザーとして IUSR を追加する手順を移動します。

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>発行および Visual Studio から、ローカル フォルダーに発行してアプリを配置

発行し、ファイル システムまたはその他のツールを使用してアプリを展開することもできます。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> ダウンロードして、Windows Server のリモート ツールのインストール

このチュートリアルでは、Visual Studio 2017 を使用します。

リモート デバッガーのダウンロード ページを開くときに問題があればを参照してください。[ファイルのダウンロードをブロック解除](../debugger/remote-debugging.md#unblock_msvsmon)ヘルプを参照します。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 一部のシナリオでは、ファイル共有から、リモート デバッガーを実行する最も効率的なができます。 詳細については、次を参照してください。[ファイル共有からのリモート デバッガーの実行](../debugger/remote-debugging.md#fileshare_msvsmon)です。
  
## <a name="BKMK_setup"></a> Windows Server のリモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要があるその他のユーザーのアクセス許可を追加または変更した場合、認証モード リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)です。

サービスとしてリモート デバッガーを実行する方法については、次を参照してください。[リモート デバッガーをサービスとして実行](../debugger/remote-debugging.md#bkmk_configureService)です。

## <a name="BKMK_attach"></a> Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターには、デバッグしようとしているソリューションを開きます (**MyASPApp**この記事の内容のすべての手順を従っているかどうか)。
2. Visual Studio で、**デバッグ > プロセスにアタッチする**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017 を使用して、以前にアタッチした同じプロセスを再アタッチできます**デバッグ > プロセスを再アタッチしています.**(Shift + Alt + P)。 

3. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4022**です。
4. をクリックして**更新**です。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが見つからない場合は、(ポートが必要です) リモート コンピューター名の代わりに IP アドレスを使用して再試行してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

    使用する場合、**検索**、ボタンをクリックする必要があります[UDP ポート 3702 を開く](#bkmk_openports)サーバーにします。

5. **[すべてのユーザーからのプロセスを表示する]** をオンにします。
6. すばやく検索するプロセス名の最初の文字を入力**dotnet.exe** (用 ASP.NET Core)。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. **[アタッチ]** をクリックします。

8. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動**http://\<リモート コンピューター名 >** です。
    
    ASP.NET の Web ページが表示されるはずです。

9. ASP.NET アプリケーションの実行では、リンクをクリックして、**に関する**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

## <a name="bkmk_openports"></a> Windows Server で必要なポートを開くのトラブルシューティング。

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure vm を使用して、ポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)です。 

必要なポート:

- 80 - IIS の必要な
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[リモート デバッガーのポート割り当て](../debugger/remote-debugger-port-assignments.md)詳細です。
- 8172 - (省略可能) は、Web デプロイを Visual Studio からアプリを展開に必要です。
- UDP 3702 - (省略可能) 検出ポートを使用する、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

1. Windows Server 上のポートを開く、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**です。

2. 選択し**受信の規則 > 新しいルール > ポート**、順にクリック**次**です。 (UDP 3702 選択**送信の規則**代わりにします)。

3. **特定のローカル ポート**をポート番号を入力し、をクリックして**次**です。

4. をクリックして**接続を許可する**、 をクリックして**次**です。

5. ポートを有効にする をクリックして 1 つまたは複数のネットワークの種類を選択して**次**です。

    選ぶ種類には、リモート コンピューターが接続しているネットワークが含まれている必要があります。
6. 名を追加 (たとえば、 **IIS**、 **Web Deploy**、または**msvsmon**) をクリックして、受信の規則の**完了**。

    受信の規則または送信の規則の一覧で、新しい規則が表示されます。

    詳細について Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)です。

3. 必要なその他のポートの追加の規則を作成します。
