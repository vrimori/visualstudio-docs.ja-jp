---
title: IIS と Azure での ASP.NET Core のリモート デバッグ |Microsoft Docs
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
ms.openlocfilehash: cc889accc116fb2115ae56155a190ed6ea2d3fc0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38797853"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Visual Studio 2017 での Azure での IIS で ASP.NET Core のリモート デバッグ

このガイドでは、設定、Visual Studio 2017 の ASP.NET Core アプリを構成し、Azure を使用して IIS にデプロイ、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。

Azure 上のリモート デバッグに推奨される方法は、シナリオによって異なります。

* Azure App Service で ASP.NET Core をデバッグするを参照してください。[スナップショット デバッガーを使用してアプリを Azure のデバッグ](../debugger/debug-live-azure-applications.md)します。 これは、推奨される方法です。
* このトピックでは、従来のデバッグ機能を使用して Azure App Service で ASP.NET Core をデバッグする手順 (を参照してください[Azure App Service でのリモート デバッグ](#remote_debug_azure_app_service))。

    このシナリオで Azure に Visual Studio からアプリをデプロイする必要がありますが、手動でインストールまたは次の図に示すように、IIS または (これらのコンポーネントは点線で表されます)、リモート デバッガーを構成する必要はありません。

    ![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Azure VM 上の IIS をデバッグするこのトピックの手順に従います (を参照してください[Azure VM でリモート デバッグ](#remote_debug_azure_vm))。 IIS でのカスタマイズされた構成を使用することができますが、セットアップと展開の手順は複雑です。

    Azure vm を Azure に Visual Studio からアプリをデプロイする必要がありもする必要がある、IIS の役割と、リモート デバッガーを手動でインストールの次の図に示します。

    ![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Azure Service Fabric の ASP.NET Core をデバッグするを参照してください。[リモート Service Fabric アプリケーションをデバッグ](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application)します。

> [!WARNING]
> このチュートリアルでは、手順を完了すると、作成した Azure リソースを削除することを確認します。 その方法は、不要な料金の発生を回避できます。


### <a name="requirements"></a>必要条件

プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での高待機時間またはダイヤルアップ、インターネットなどの低帯域幅接続経由またはインターネット経由でのデバッグは使用しないでと失敗は、ある非常に遅く。 要件の完全な一覧を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)します。

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Visual Studio 2017 のコンピューターで ASP.NET Core アプリケーションを作成します。 

1. 新しい ASP.NET Core アプリケーションを作成します。 (選択**ファイル > 新規 > プロジェクト**を選択し、 **Visual c# > Web > ASP.NET Core Web アプリケーション**)。

    **ASP.NET Core**テンプレート セクション**Web アプリケーション**します。

2. 確認します**ASP.NET Core 2.0**が選択されているを**Docker サポートを有効にする**は**いない**選択されていることと**認証**に設定されています。**認証なし**します。

3. プロジェクトに名前を**MyASPApp**  をクリック**OK**新しいソリューションを作成します。

4. [About.cshtml.cs] ファイルを開きにブレークポイントを設定、`OnGet`メソッド (以前のテンプレートでの代わりに HomeController.cs を開きでブレークポイントを設定、`About()`メソッド)。

## <a name="remote_debug_azure_app_service"></a> Azure App Service で ASP.NET Core のリモート デバッグ

Visual Studio から簡単に発行し、IIS の完全にプロビジョニングされたインスタンスにアプリをデバッグできます。 ただし、IIS の構成が事前設定、カスタマイズすることはできません。 詳細な手順についてを参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリのデプロイ](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)します。 (IIS をカスタマイズする機能が必要な場合のデバッグで試す、 [Azure VM](#remote_debug_azure_vm))。 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>サーバー エクスプ ローラーを使用してリモート デバッグとアプリを展開するには

1. Visual Studio でプロジェクト ノードを右クリックし、選択**発行**します。

    以前に任意の発行プロファイルを構成する場合、**発行**ウィンドウが表示されます。 クリックして**新しいプロファイル**します。

1. 選択**Azure App Service**から、**発行**ダイアログ ボックスで、**新規作成**、発行する指示に従います。

    詳細については、次を参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリのデプロイ](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)します。

    ![Azure App Service に発行する](../debugger/media/remotedbg_azure_app_service_profile.png)

1. 開いている**サーバー エクスプ ローラー** (**ビュー** > **サーバー エクスプ ローラー**)、App Service インスタンスを右クリックし、選択**デバッガーのアタッチ**.

1. 実行中の ASP.NET アプリケーションでリンクをクリックして、**について**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

    これで完了です。 このトピックの手順の残りの部分は、Azure VM でのリモート デバッグに適用されます。

## <a name="remote_debug_azure_vm"></a> Azure VM での ASP.NET Core のリモート デバッグ

Windows Server 向け Azure VM を作成し、インストールし、IIS とその他の必要なソフトウェア コンポーネントを構成します。 これを Azure App Service にデプロイするよりも時間がかかるし、このチュートリアルでは、残りの手順に従うことが必要です。

最初で説明されているすべての手順に従って[実行 IIS をインストールして](/azure/virtual-machines/windows/quick-create-portal)します。

ネットワーク セキュリティ グループでポート 80 を開くときにもリモート デバッガーのポート 4022 を開きます。 これにより、後で開く必要はありません。

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>アプリは、Azure VM で既に IIS で実行されているか。

この記事には、Windows server 上の IIS の基本構成の設定および Visual Studio からアプリを展開する方法の手順が含まれています。 ここでは、サーバーにインストールされているアプリが正常に実行できることと、リモート デバッグする準備が必要なコンポーネントが含まれているかどうかを確認する手順。

* アプリが IIS で実行されていると、リモート デバッガーをダウンロードし、デバッグを開始に移動したい場合[をダウンロードして Windows Server のリモート ツールをインストール](#BKMK_msvsmon)します。

* アプリが設定されている、展開されると、かどうかを確認するのに役立つこのトピックのすべての手順に従いますデバッグできるように、IIS で正しく実行する場合は。

### <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(既定では有効です)、Internet explorer セキュリティ強化の構成が有効な場合は、一部の web サーバー コンポーネントをダウンロードするための信頼済みサイトとして、一部のドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**します。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むためのアクセス許可を与える要求を取得する可能性があります。 必須ではありませんが、プロセスを簡略化する次のようにクリックします。 これらのリソースのいくつか**追加**入力を求められたらします。

### <a name="install-aspnet-core-on-windows-server"></a>Windows Server での ASP.NET Core をインストールします。

1. インストール、 [.NET Core Windows Server ホスティング](https://aka.ms/dotnetcore-2-windowshosting)ホスティング システムにバンドルします。 .NET Core ランタイム、.NET Core ライブラリ、および ASP.NET Core モジュール、バンドルがインストールされます。 詳細についての詳細な手順については、次を参照してください。 [IIS への発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)します。

    > [!NOTE]
    > システムがインターネットに接続があるない場合を入手してインストール、  *[Microsoft Visual C 2015 再頒布可能](https://www.microsoft.com/download/details.aspx?id=53840)* .NET Core Windows Server ホスティング バンドルをインストールする前にします。

3. システムの再起動 (実行または**net stop was/y**続けて**net start w3svc**システム パスに変更を適用するコマンド プロンプトから)。

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

アプリが正常がデプロイした後、自動的に開始する必要があります。 Visual Studio からアプリが起動しない場合は、IIS でアプリを起動します。 ASP.NET Core でのアプリケーション プールのフィールドを確認する必要があります、 **DefaultAppPool**に設定されている**マネージ コードなし**します。

1. **設定**ダイアログ ボックスをクリックしてデバッグを有効にする **[次へ]**、選択、**デバッグ**構成を選び、**追加ファイルを削除移行先**下、**ファイル発行**オプション。

    > [!NOTE]
    > デバッグを無効にするリリース構成を選択した場合、 *web.config*ファイルの公開時にします。

1. クリックして**保存**し、アプリを再発行します。

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(省略可能)ローカル フォルダーに発行してデプロイします。

このオプションを使用するには、RoboCopy、Powershell を使用して IIS にアプリケーションをコピーするか、ファイルを手動でコピーする場合は、アプリをデプロイします。

### <a name="BKMK_deploy_asp_net"></a> Windows Server コンピューターに ASP.NET Web サイトを構成します。

インポートする場合は、発行設定をこのセクションをスキップすることができます。

1. **インターネット インフォメーション サービス (IIS) マネージャー** を開き、 **[サイト]** に移動します。

2. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

3. 設定、**エイリアス**フィールドを**MyASPApp**と、アプリケーション プール フィールドを**マネージ コードなし**します。 設定、**物理パス**に**C:\Publish** (後で配置する ASP.NET プロジェクト)。

4. サイトでは、IIS マネージャーで選択されて、次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、またはユーザーのアプリケーション プールが読み取りと実行権限を持つ権限を持つユーザー用に構成されたことを確認します。

    これらのアクセス権を持つユーザーのいずれかが表示されない場合は、読み取りと実行権限を持つユーザーとして IUSR を追加する手順を移動します。

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(省略可能)発行して、Visual Studio からローカル フォルダーにパブリッシュすることによって、アプリをデプロイ

Web Deploy を使用していない場合は、発行およびファイル システムまたはその他のツールを使用してアプリを配置する必要があります。 ことができます、ファイル システムを使用してパッケージを作成して開始しパッケージを手動で展開するか PowerShell、RoboCopy、または XCopy などの他のツールを使用します。 このセクションで Web Deploy を使用しない場合、手動でパッケージをコピーするいると想定されます。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> ダウンロードして、Windows Server のリモート ツールのインストール

このチュートリアルでは、Visual Studio 2017 を使用します。

リモート デバッガーのダウンロード ページを開くときに問題があればを参照してください。[ファイルのダウンロードをブロック解除](../debugger/remote-debugging.md#unblock_msvsmon)ヘルプを参照します。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Windows Server のリモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要がある追加のユーザーのアクセス許可を追加または変更した場合、認証モード、リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)します。

### <a name="BKMK_attach"></a> Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターでは、デバッグしようとしているソリューションを開きます (**MyASPApp**この記事の手順に従っている場合)。
2. Visual Studio で、次のようにクリックします。**デバッグ > プロセスにアタッチ**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017 では、することができますを使用して、以前にアタッチした同じプロセスにアタッチして再**デバッグ > プロセスに再アタッチしています.**(Shift + Alt + P)。 

3. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4022**します。
4. クリックして**更新**します。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが表示されない場合は、(ポートが必要です)、リモート コンピューター名ではなく IP アドレスを使用してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

    使用する場合、**検索**、ボタンをクリックする必要があります[UDP ポート 3702 を開く](#bkmk_openports)サーバー。

5. **[すべてのユーザーからのプロセスを表示する]** をオンにします。

6. すばやく検索するプロセス名の最初の文字を入力*dotnet.exe* (for ASP.NET Core)。
   
   ASP.NET Core アプリでは、前のプロセス名でした*dnx.exe*します。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. **[アタッチ]** をクリックします。

8. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動します。 **http://\<リモート コンピューター名 >** します。
    
    ASP.NET の Web ページが表示されるはずです。
9. 実行中の ASP.NET アプリケーションでリンクをクリックして、**について**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

### <a name="bkmk_openports"></a> トラブルシューティング: Windows Server で必要なポートを開く

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、デプロイに関する問題のトラブルシューティングを行うと、アプリがファイアウォールの背後にホストされている場合、は、正しいポートが開いていることを確認する必要があります。

Azure VM 上でポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic)します。 

必要なポート:

- 80 に必要な IIS 用。
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md)詳細については)。
- UDP 3702 - (省略可能) 検出ポート使用すると、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

さらに、これらのポートは、ASP.NET のインストールで既に開く必要があります。
- 8172 - (Visual Studio からアプリのデプロイへの Web 配置のために必要な省略可能)

