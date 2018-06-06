---
title: Web Deploy を使用して IIS に ASP.NET を配置します。
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794202"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Visual Studio で Web Deploy を使用して IIS のリモート コンピューターに ASP.NET を展開します。

この記事では、セットアップし、Visual Studio 2017 ASP.NET MVC 4.5.2 アプリケーションを構成し、IIS に配置する方法について説明します。 この記事には、Windows server 上の IIS の基本的な構成設定、および Visual Studio からアプリの展開のステップが含まれます。 ここでは、サーバーがインストールされているコンポーネントを必要なことと、展開する準備ができたらかどうかを確認する手順です。 ASP.NET Core アプリケーションを展開する場合は、いくつかの手順は異なります。 ASP.NET Core アプリケーションを展開するを参照してください。[発行の設定をインポートすることによって IIS にアプリケーションを発行](../deployment/tutorial-import-publish-settings-iis.md)手順についてはします。 ASP.NET および ASP.NET Core のシナリオでは高速に展開するインポートすることによって IIS 設定を発行します。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 8 (Windows Server 2008 R2 のサーバーの手順が異なる)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>ASP.NET 4.5.2 を作成する Visual Studio コンピューターにアプリケーション
  
1. Visual Studio を実行するコンピューターで次のように選択します。**ファイル > 新しいプロジェクト**です。

1. **Visual c#** または**Visual Basic**、選択**Web**、し、中央のペインで **[ASP.NET Web アプリケーション (.NET Framework)]** をクリックし、 **OK**です。

    指定されたプロジェクト テンプレートが見つからない場合にをクリックして、**開いている Visual Studio インストーラー**の左側のウィンドウ内のリンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 必須の Visual Studio のワークロードは、インストールする必要がありますを特定するには、この記事で前提条件を参照してください。

1. 選択**MVC** (.NET Framework) ことを確認し、**認証なし**を選択して、をクリックして**OK**です。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="bkmk_configureIIS"></a> インストールして Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(これは既定で有効)、Internet explorer セキュリティ強化の構成が有効な場合は、いくつかの web サーバー コンポーネントをダウンロードするために信頼済みサイトとしていくつかのドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**です。 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むための権限を許可する要求を取得することがあります。 これらのリソースの一部は必要ありません、クリックしてプロセスを簡易化、**追加**されたらです。

## <a name="BKMK_deploy_asp_net"></a> Windows Server に ASP.NET 4.5 をインストールします。

詳細な情報を IIS で ASP.NET をインストールする場合は、「 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

1. サーバー マネージャーの左側のウィンドウで選択**IIS**です。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**です。

1. Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します**新しい Web Platform コンポーネントの取得**、ASP.NET の検索)。

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. システムを再起動 (実行または**net stop が/y**続く**net 開始 w3svc**システム パスへの変更を取得するコマンド プロンプトから)。

## <a name="BKMK_install_webdeploy"></a> インストール Web 3.6 Windows Server での展開します。

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Windows Server コンピューターで ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後で配置されます。

2. これがまだ開いていない場合は開きます、**インターネット インフォメーション サービス (IIS) マネージャー**です。 (サーバー マネージャーの左側のウィンドウで選択**IIS**です。 サーバーを右クリックし **インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**左側のウィンドウに移動**サイト**です。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**です。

5. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

6. 設定、**エイリアス**フィールドを**MyASPApp**、既定のアプリケーション プール (**DefaultAppPool**)、し、設定、**物理パス**に**C:\Publish**です。

7. **接続****アプリケーション プール**です。 開いている**DefaultAppPool**にアプリケーション プール フィールドを設定および**ASP.NET v4.0** (ASP.NET 4.5 は、アプリケーション プールのオプションではありません)。

8. IIS マネージャーで選択されているサイトで次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、または読み取りと実行権限を持つ承認済みユーザーにアプリケーション プールが構成されているユーザーを確認します。 これらのユーザーが存在しない場合、読み取りと実行権限を持つユーザーとして IUSR を追加します。

## <a name="bkmk_webdeploy"></a> 発行し、Visual Studio からの Web デプロイを使用してアプリを配置

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

またのセクションを参照する必要があります[ポートのトラブルシューティング](#bkmk_openports)です。

## <a name="bkmk_openports"></a> Windows Server で必要なポートを開くのトラブルシューティング。

ほとんどの設定では、ASP.NET および Web Deploy のインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure vm を使用して、ポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)です。 

必要なポート:

* 80 - IIS の必要な
* 8172-Visual Studio からアプリを配置する Web の展開に必要な

1. Windows Server 上のポートを開く、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**です。

2. 選択し、**受信の規則 > 新しいルールの追加 > ポート**です。 選択**次へ**し、**特定のローカル ポート**をポート番号を入力し、をクリックして**次へ**、し**接続を許可する**、次へ をクリックし、名前を追加 (**IIS**、 **Web Deploy**、または**msvsmon**)、受信の規則にします。

    詳細について Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)です。

3. 必要なその他のポートの追加の規則を作成します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポート、および、IIS に ASP.NET アプリケーションを展開する発行設定ファイルを作成します。 インポートして展開することもできます。 設定を発行します。

> [!div class="nextstepaction"]
> [展開をインポートすることによって IIS 設定を発行します。](../deployment/tutorial-import-publish-settings-iis.md)