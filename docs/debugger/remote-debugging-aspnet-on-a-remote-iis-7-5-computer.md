---
title: "リモートの IIS のリモート コンピューター上の ASP.NET のデバッグ |Microsoft ドキュメント"
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed7ae018725e4ba2da5239609d90276d007827aa
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>IIS: リモート コンピューター上の ASP.NET のリモート デバッグ
IIS に配置されている ASP.NET アプリケーションをデバッグするには、インストールし、アプリが展開されているコンピューターでリモート ツールを実行して Visual Studio から、実行中のアプリにアタッチし、します。

![リモート デバッガー コンポーネント](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

このガイドでは、設定、Visual Studio 2017 ASP.NET MVC 4.5.2 アプリケーションを構成して、IIS に展開、および Visual Studio からリモート デバッガーをアタッチする方法について説明します。 ASP.NET Core リモート デバッグを参照してください。 [IIS コンピューター上のリモート デバッグ ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)です。 配置して、Azure を使用して IIS 上でデバッグすることもできます。 詳細については、次を参照してください。 [Azure 上でリモート デバッグ](../debugger/remote-debugging-azure.md)です。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 8 (Windows Server 2008 R2 のサーバーの手順が異なる)

## <a name="requirements"></a>必要条件

リモート デバッガーは、Windows Server の Windows Server 2008 Service Pack 2 以降ではサポートします。 要件の一覧については、次を参照してください。[要件](../debugger/remote-debugging.md#requirements_msvsmon)です。

> [!NOTE]
> プロキシを介して接続されている 2 台のコンピューター間でのデバッグはサポートされていません。 国の間での待機時間の長いまたはダイヤルアップ、インターネットなどの低帯域幅接続またはインターネット経由でのデバッグはお勧めしませんが失敗することも非常に遅くします。

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>ASP.NET 4.5.2 を作成する Visual Studio コンピューターにアプリケーション
  
1. MVC の ASP.NET アプリケーションを新規作成します。 (**ファイル > 新規 > プロジェクト**選択してから、* * Visual c# > Web > ASP.NET Web アプリケーションです。 **[ASP.NET 4.5.2** テンプレート] セクションで、 **[MVC]**を選択します。 確認して**Docker のサポートを有効にする**が選択されていないことと**認証**に設定されている**認証なし**です。 プロジェクトに名前を**MyASPApp**)。

2. HomeController.cs ファイルを開き、 `About()` メソッドにブレークポイントを設定します。

## <a name="bkmk_configureIIS"></a>インストールして Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

設定によっては、セキュリティには、このチュートリアルで説明されているソフトウェアを簡単にダウンロードするため、お使いのブラウザーに次の信頼済みサイトを追加するときに保存可能性があります。 これらのサイトへのアクセスは必要な場合があります。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Internet Explorer を使用している場合に移動して、信頼済みサイトを追加できます**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**です。 これらの手順は、その他のブラウザーによって異なります。 (My.visualstudio.com からリモート デバッガーの古いバージョンをダウンロードする場合は、いくつか追加の信頼済みサイトが必要にサインインします。)

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むための権限を許可する要求を取得することがあります。 これらの追加リソースは、ほとんどの場合、ソフトウェアをインストールする必要はありません。

## <a name="BKMK_deploy_asp_net"></a>Windows Server に ASP.NET 4.5 をインストールします。

詳細な情報を IIS で ASP.NET をインストールする場合は、「 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

1. Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します**新しい Web Platform コンポーネントの取得**、ASP.NET の検索)。

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe ir**

2. システムを再起動 (実行または**net stop が/y**続く**net 開始 w3svc**システム パスへの変更を取得するコマンド プロンプトから)。

## <a name="BKMK_install_webdeploy"></a>(省略可能)インストール Web 3.6 Windows Server での展開します。

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>Windows Server コンピューターで ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後で配置されます。

2. 開く、**インターネット インフォメーション サービス (IIS) マネージャー**です。 (サーバー マネージャーの左側のウィンドウで選択**IIS**です。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**左側のウィンドウに移動**サイト**です。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**です。

5. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]**を選択します。

6. 設定、**エイリアス**フィールドを**MyASPApp**、既定のアプリケーション プール (**DefaultAppPool**)、し、設定、**物理パス**に**C:\Publish**です。

7. **接続****アプリケーション プール**です。 開いている**DefaultAppPool**にアプリケーション プール フィールドを設定および**ASP.NET v4.0** (ASP.NET 4.5 は、アプリケーション プールのオプションではありません)。

8. IIS マネージャーで選択されているサイトで次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、または読み取りと実行権限を持つ承認済みユーザーにアプリケーション プールが構成されているユーザーを確認します。 これらのユーザーが存在しない場合、読み取りと実行権限を持つユーザーとして IUSR を追加します。

## <a name="bkmk_webdeploy"></a>(省略可能)発行し、Visual Studio からの Web デプロイを使用してアプリを配置

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

またのセクションを参照する必要があります[ポートのトラブルシューティング](#bkmk_openports)です。

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(省略可能)発行および Visual Studio から、ローカル フォルダーに発行してアプリを配置

発行し、ファイル システムまたはその他のツールを使用してアプリを展開することもできます。

1. (ASP.NET 4.5.2)Web.config ファイルが .NET Framework の正しいバージョンを一覧表示されることを確認してください。  など、ASP.NET 4.5.2 を対象とする場合は、web.config でこのバージョンが表示されていることを確認してください。
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    たとえば、4.5.2 ではなく ASP.NET 4 をインストールする場合は、バージョンは 4.0 をする必要があります。

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>ダウンロードして、Windows Server でリモート ツールのインストール

このチュートリアルでは、Visual Studio 2017 を使用します。

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> 一部のシナリオでは、ファイル共有から、リモート デバッガーを実行する最も効率的なができます。 詳細については、次を参照してください。[ファイル共有からのリモート デバッガーの実行](../debugger/remote-debugging.md#fileshare_msvsmon)です。
  
## <a name="BKMK_setup"></a>Windows Server のリモート デバッガーを設定します。

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> 必要があるその他のユーザーのアクセス許可を追加または変更した場合、認証モード リモート デバッガーのポート番号を参照してください。[リモート デバッガーを構成する](../debugger/remote-debugging.md#configure_msvsmon)です。

サービスとしてリモート デバッガーを実行する方法については、次を参照してください。[リモート デバッガーをサービスとして実行](../debugger/remote-debugging.md#bkmk_configureService)です。

## <a name="BKMK_attach"></a> Visual Studio コンピューターから ASP.NET アプリケーションにアタッチする

1. Visual Studio コンピューターで開く、 **MyASPApp**ソリューションです。
2. Visual Studio で、**デバッグ > プロセスにアタッチする**(Ctrl + Alt + P)。

    > [!TIP]
    > Visual Studio 2017 を使用して、以前にアタッチした同じプロセスを再アタッチできます**デバッグ > プロセスを再アタッチしています.**(Shift + Alt + P)。 

3. 修飾子のフィールドに設定**\<リモート コンピューター名 >: 4022**です。
4. をクリックして**更新**です。
    **[選択可能なプロセス]** ウィンドウにプロセスがいくつか表示されます。

    すべてのプロセスが見つからない場合は、(ポートが必要です) リモート コンピューター名の代わりに IP アドレスを使用して再試行してください。 使用することができます`ipconfig`IPv4 アドレスを取得するコマンド ラインでします。

5. **[すべてのユーザーからのプロセスを表示する]**をオンにします。
6. すばやく検索するプロセス名の最初の文字を入力**w3wp.exe** ASP.NET 4.5 用です。

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. をクリックして**アタッチ**

8. リモート コンピューターの Web サイトを開きます。 ブラウザーに移動**http://\<リモート コンピューター名 >**です。
    
    ASP.NET の Web ページが表示されるはずです。
9. ASP.NET アプリケーションの実行では、リンクをクリックして、**に関する**ページ。

    Visual Studio で、ブレークポイントにヒットするはずです。

## <a name="bkmk_openports"></a>Windows Server で必要なポートを開くのトラブルシューティング。

ほとんどの設定では、ASP.NET とリモート デバッガーのインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure vm を使用して、ポートを開く必要があります、[ネットワーク セキュリティ グループ](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)です。 

必要なポート:

- 80 - IIS の必要な
- 8172 - (Web は、Visual Studio からアプリを展開する展開のために必要な省略可能)
- 4022-Visual Studio 2017 からのリモート デバッグに必要な (を参照してください[リモート デバッガーのポート割り当て](../debugger/remote-debugger-port-assignments.md)詳細です。
- UDP 3702 - (省略可能) 検出ポートを使用する、**検索**Visual Studio でリモート デバッガーをアタッチするときにボタンをクリックします。

1. Windows Server 上のポートを開く、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**です。

2. 選択し、**受信の規則 > 新しいルールの追加 > ポート**です。 選択**次へ**し、**特定のローカル ポート**をポート番号を入力し、をクリックして**次へ**、し**接続を許可する**、次へ をクリックし、名前を追加 (**IIS**、 **Web Deploy**、または**msvsmon**)、受信の規則にします。

    詳細について Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)です。

3. 必要なその他のポートの追加の規則を作成します。