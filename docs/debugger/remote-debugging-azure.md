---
title: リモート デバッグでは、IIS と Azure の ASP.NET Core |Microsoft ドキュメント
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 202e9ce6e0a53c6967ebe1bacaa6553a1241298e
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Visual Studio 2017 で Azure での IIS で ASP.NET Core のリモート デバッグ

このガイドでは、設定、Visual Studio 2017 ASP.NET Core アプリケーションを構成して、Azure を使用して IIS に展開、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。

Azure でのリモート デバッグするための推奨方法は、シナリオによって異なります。

* Azure App Service の ASP.NET Core をデバッグするを参照してください。[スナップショット デバッガーを使用して Azure のデバッグ apps](../debugger/debug-live-azure-applications.md)です。 これは、推奨される方法です。
* 従来のデバッグ機能を使用して Azure App Service の ASP.NET Core をデバッグするには、このトピックの手順に従います (を参照してください[Azure App Service でのリモート デバッグ](#remote_debug_azure_app_service))。

    このシナリオで Azure に Visual Studio からアプリを配置する必要がありますが、手動でインストールするか、次の図に示すように、IIS または (これらのコンポーネントは点線で表されます)、リモート デバッガーを構成する必要はありません。

    ![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM 上の IIS をデバッグするには、このトピックの手順に従います (を参照してください[Azure VM 上でリモート デバッグ](#remote_debug_azure_vm))。 IIS でのカスタマイズされた構成を使用できますが、セットアップと展開の手順はさらに複雑です。

    Azure VM での Azure に Visual Studio からアプリを配置する必要がありする必要も、IIS の役割と、リモート デバッガーを手動でインストールの次の図に示すようにします。

    ![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service Fabric の ASP.NET Core をデバッグするを参照してください。[リモート Service Fabric アプリケーションのデバッグ](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)です。

> [!WARNING]
> このチュートリアルの手順を完了したときに作成する Azure リソースを削除することを確認します。 このように不要な料金を回避できます。


### <a name="requirements"></a>要件

プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での待機時間の長いまたはダイヤルアップ、インターネットなどの低帯域幅接続またはインターネット経由でのデバッグはお勧めしませんが失敗することも非常に遅くします。 要件の一覧については、次を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)です。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 コンピューター上の ASP.NET Core アプリケーションを作成します。 

1. 新しい ASP.NET Core アプリケーションを作成します。 (選択**ファイル > 新規 > プロジェクト**選択してから、 **Visual c# > Web > ASP.NET Core Web アプリケーション**)。

    **ASP.NET Core**テンプレート セクションで、 **Web アプリケーション**です。

2. 確認して**ASP.NET Core 2.0**が選択されているを**Docker のサポートを有効にする**は**いない**選択されていることと**認証**に設定されています。**認証なし**です。

3. プロジェクトの名前**MyASPApp**  をクリック**OK**新しいソリューションを作成します。

4. About.cshtml.cs ファイルを開きにブレークポイントを設定、`OnGet`メソッド (既存のテンプレートで HomeController.cs 代わりに開きにブレークポイントを設定、`About()`メソッド)。

## <a name="remote_debug_azure_app_service"></a> Azure App Service の ASP.NET Core のリモート デバッグ

Visual Studio から簡単に発行し、完全にプロビジョニングされている IIS のインスタンスにアプリのデバッグできます。 ただし、IIS の構成が事前設定し、カスタマイズすることはできません。 詳細な手順についてを参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリを配置](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)です。 (IIS をカスタマイズする機能を実行する場合に、デバッグを実行、 [Azure VM](#BKMK_azure_vm))。 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>サーバー エクスプ ローラーを使用してリモート デバッグとアプリを展開するには

1. Visual Studio でプロジェクト ノードを右クリックして選択**発行**です。

    任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイル**です。

1. 選択**Azure App Service**から、**発行**ダイアログ ボックスで、**新規作成**、発行する指示に従います。

    詳細については、次を参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリを配置](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)です。

    ![Azure App Service に発行する](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 開いている**サーバー エクスプ ローラー** (**ビュー** > **サーバー エクスプ ローラー**) の App Service のインスタンスを右クリックし、選択、 **デバッガーの接続**.

1. ASP.NET アプリケーションの実行では、リンクをクリックして、**に関する**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

    これで完了です。 このトピックの手順の残りの部分は、Azure VM でのリモート デバッグに適用されます。

## <a name="remote_debug_azure_vm"></a> Azure VM でリモート デバッグの ASP.NET Core

Windows Server 用 Azure VM を作成しをインストールし、IIS およびその他の必要なソフトウェア コンポーネントを構成します。 これは、App Service を Azure に展開するよりも時間がかかるし、このチュートリアルでは、残りの手順に従うことが必要です。

最初で説明されているすべての手順に従います[実行 IIS をインストールして](/azure/virtual-machines/windows/quick-create-portal)です。

ネットワーク セキュリティ グループでポート 80 を開くときにもリモート デバッガーのポート 4022 を開きます。 このように、後で開くにはできません。

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>アプリは、Azure VM で既に IIS で実行されているか。

この記事には、Windows server 上の IIS の基本的な構成設定、および Visual Studio からアプリの展開のステップが含まれます。 ここでは、サーバーにインストールされているアプリが正常に実行できることと、リモート デバッグする準備ができたら、必要なコンポーネントが含まれているかどうかを確認する手順。

* IIS で、アプリが実行されていて、リモート デバッガーをダウンロードし、デバッグを開始に移動したい[ダウンロードして、Windows Server のリモート ツールをインストール](#BKMK_msvsmon)です。

* アプリがセットアップされている、展開するかどうかを確認するのに役立つこのトピックのすべての手順に従いますをデバッグすることができるように、IIS で正しく実行する場合。

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(これは既定で有効)、Internet explorer セキュリティ強化の構成が有効な場合は、いくつかの web サーバー コンポーネントをダウンロードするために信頼済みサイトとしていくつかのドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**です。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むための権限を許可する要求を取得することがあります。 これらのリソースの一部は必要ありません、クリックしてプロセスを簡易化、**追加**されたらです。

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server での ASP.NET Core をインストールします。

1. インストール、 [.NET コア Windows Server をホストしている](https://aka.ms/dotnetcore-2-windowshosting)ホスト システムにバンドルできます。 .NET Core ランタイム、.NET Core ライブラリ、および ASP.NET Core モジュール バンドルがインストールされます。 複数の詳細な手順については、次を参照してください。[を IIS に発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)です。

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

インポートする場合は、発行の設定、このセクションをスキップすることができます。

1. **インターネット インフォメーション サービス (IIS) マネージャー** を開き、 **[サイト]** に移動します。

2. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

3. 設定、**エイリアス**フィールドを**MyASPApp**と、アプリケーション プール フィールドを**マネージ コードなし**です。 設定、**物理パス**に**C:\Publish** (ここで、ASP.NET プロジェクトは後で展開されます)。

4. IIS マネージャーで選択されているサイトで次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、または読み取りと実行権限を持つ承認済みユーザーにアプリケーション プールが構成されているユーザーを確認します。

    これらのユーザーのアクセス権を持つ 1 つ表示されない場合は、読み取りと実行権限を持つユーザーとして IUSR を追加する手順を移動します。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(省略可能)発行および Visual Studio から、ローカル フォルダーに発行してアプリを配置

Web Deploy を使用していない場合は、発行およびファイル システムまたはその他のツールを使用してアプリを配置する必要があります。 ファイル システムを使用してパッケージを作成することで開始し、し、パッケージを手動で展開か PowerShell、XCopy、RoboCopy などの他のツールを使用します。 このセクションでは、Web Deploy を使用しない場合、パッケージを手動でコピーが想定しています。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> ダウンロードして、Windows Server のリモート ツールのインストール

このチュートリアルでは、Visual Studio 2017 を使用します。

リモート デバッガーのダウンロード ページを開くときに問題があればを参照してください。[ファイルのダウンロードをブロック解除](../debugger/remote-debugging.md#unblock_msvsmon)ヘルプを参照します。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Windows Server のリモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要があるその他のユーザーのアクセス許可を追加または変更した場合、認証モード リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)です。

### <a name="BKMK_attach"></a> Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターで開く、 **MyASPApp**ソリューションです。
2. Visual Studio で、**デバッグ > プロセスにアタッチする**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017、することができますを使用して、以前にアタッチした同じプロセスにアタッチして再**デバッグ > プロセスを再アタッチしています.**(Shift + Alt + P)。 

3. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4022**です。
4. **[更新]** を生成する必要があります。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが見つからない場合は、(ポートが必要です) リモート コンピューター名の代わりに IP アドレスを使用して再試行してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

    使用する場合、**検索**、ボタンをクリックする必要があります[UDP ポート 3702 を開く](#bkmk_openports)サーバーにします。

5. **[すべてのユーザーからのプロセスを表示する]** をオンにします。

6. すばやく検索するプロセス名の最初の文字を入力*dotnet.exe* (用 ASP.NET Core)。
   
   ASP.NET Core アプリケーションでは、前のプロセス名でした*dnx.exe*です。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. **[アタッチ]** をクリックします。

8. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動**http://\<リモート コンピューター名 >** です。
    
    ASP.NET の Web ページが表示されるはずです。
9. ASP.NET アプリケーションの実行では、リンクをクリックして、**に関する**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

### <a name="bkmk_openports"></a> Windows Server で必要なポートを開くのトラブルシューティング。

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、展開に関する問題のトラブルシューティングを行うし、アプリがファイアウォールの背後にホストされているは、正しいポートが開いていることを確認する必要があります。

Azure vm を使用して、ポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)です。 

必要なポート:

- 80 - IIS の必要な
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[リモート デバッガーのポート割り当て](../debugger/remote-debugger-port-assignments.md)詳細については)。
- UDP 3702 - (省略可能) 検出ポートを使用する、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

さらに、これらのポートは、ASP.NET のインストールで既に開いて必要があります。
- 8172 - (Web は、Visual Studio からアプリを展開する展開のために必要な省略可能)

