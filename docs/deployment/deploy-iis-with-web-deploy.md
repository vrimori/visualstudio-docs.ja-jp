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
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080851"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Visual Studio で Web Deploy を使用してリモートの IIS コンピューターに ASP.NET を配置します。

この記事を設定して、Visual Studio 2017 ASP.NET MVC 4.5.2 アプリケーションを構成し、IIS にデプロイする方法について説明します。 この記事には、Windows server 上の IIS の基本構成の設定および Visual Studio からアプリを展開する方法の手順が含まれています。 ここでは、サーバーにインストールされているコンポーネントに必要なあるおよびデプロイする準備ができているかどうかを確認する手順です。 ASP.NET Core アプリケーションを展開する場合は、いくつかの手順は異なります。 ASP.NET Core アプリを展開するを参照してください。[発行の設定をインポートすることによって IIS にアプリケーションを発行](../deployment/tutorial-import-publish-settings-iis.md)手順についてはします。 一部の ASP.NET と ASP.NET Core シナリオでは高速にデプロイする発行の設定をインポートすることによって IIS です。

これらの手順は、これらのサーバー構成でテストされています。
* Windows Server 2012 R2 と IIS 8 (Windows Server 2008 R2 の server 手順は異なります)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>ASP.NET 4.5.2 を作成する Visual Studio コンピューターでアプリケーション
  
1. Visual Studio が実行されているコンピューターで、次のように選択します。**ファイル** > **新しいプロジェクト**します。

1. **Visual c#** または**Visual Basic**、選択**Web**、中央のペインのいずれかを  **ASP.NET Web アプリケーション (.NET Framework)** し**OK**します。

    指定されたプロジェクト テンプレートが表示されない場合にクリックして、 **Visual Studio インストーラーを開く**の左側のウィンドウで、リンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 インストールする必要がありますが、必要な Visual Studio ワークロードを特定するには、この記事で前提条件を参照してください。

1. 選択**MVC** (.NET Framework) を確認して**認証なし**が選択されているし、をクリックし、 **[ok]** します。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. 選択**ビルド** > **ソリューションのビルド**プロジェクトをビルドします。

## <a name="install-and-configure-iis-on-windows-server"></a>インストールし、Windows Server で IIS を構成します。

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Windows Server 上のブラウザーのセキュリティ設定を更新します。

(既定では有効です)、Internet explorer セキュリティ強化の構成が有効な場合は、一部の web サーバー コンポーネントをダウンロードするための信頼済みサイトとして、一部のドメインを追加する必要があります。 移動して、信頼済みサイトを追加**インターネット オプション** > **セキュリティ** > **信頼済みサイト** > **サイト**. 次のドメインを追加します。

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

ソフトウェアをダウンロードするときに、さまざまな web サイトのスクリプトおよびリソースを読み込むためのアクセス許可を与える要求を取得する可能性があります。 必須ではありませんが、プロセスを簡略化する次のようにクリックします。 これらのリソースのいくつか**追加**入力を求められたらします。

## <a name="install-aspnet-45-on-windows-server"></a>Windows Server での ASP.NET 4.5 をインストールします。

詳細な情報を IIS に ASP.NET をインストールする場合は、「 [ASP.NET 3.5 および ASP.NET 4.5 を使用して IIS 8.0](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

1. サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**します。

1. Web Platform Installer (WebPI) を使用して ASP.NET 4.5 をインストールする (Windows Server 2012 R2 で、サーバー ノードから次のように選択します**Web プラットフォームの新しいコンポーネントの取得**、ASP.NET の検索)。

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Windows Server 2008 R2 を使用している場合は、代わりにこのコマンドを使用して ASP.NET 4 をインストールします。

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. システムの再起動 (実行または**net stop was/y**続けて**net start w3svc**システム パスに変更を適用するコマンド プロンプトから)。

## <a name="install-web-deploy-36-on-windows-server"></a>Windows Server 上の 3.6 のインストール Web 配置します。

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Windows Server コンピューター上の ASP.NET Web サイトを構成します。

1. Windows エクスプ ローラーを開き、新しいフォルダーを作成**C:\Publish**、ASP.NET プロジェクトを後でデプロイされます。

2. 開くことがまだ開いていない場合、**インターネット インフォメーション サービス (IIS) マネージャー**します。 (サーバー マネージャーの左側のウィンドウで次のように選択します。 **IIS**します。 サーバーを右クリックして**インターネット インフォメーション サービス (IIS) マネージャー**)。

3. **接続**で左側のウィンドウに移動**サイト**します。

4. 選択、**既定の Web サイト**、選択**基本設定**、設定と、**物理パス**に**C:\Publish**します。

5. **[既定の Web サイト]** ノードを右クリックして、 **[アプリケーションの追加]** を選択します。

6. 設定、**エイリアス**フィールドを**MyASPApp**、アプリケーション プールの既定値を受け入れます (**DefaultAppPool**)、設定、**物理パス**に**C:\Publish**します。

7. **接続**、**アプリケーション プール**します。 開いている**DefaultAppPool**にアプリケーション プールのフィールドを設定および**ASP.NET v4.0** (ASP.NET 4.5 は、アプリケーション プールのオプションではありません)。

8. サイトでは、IIS マネージャーで選択されて、次のように選択します。**アクセス許可の編集**、その IUSR、IIS_IUSRS、またはユーザーのアプリケーション プールが読み取りと実行権限を持つ権限を持つユーザー用に構成されたことを確認します。 これらのユーザーの [なし] が存在する場合は、読み取りと実行権限を持つユーザーとして IUSR を追加します。

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>発行し、Visual Studio から Web Deploy を使用してアプリを配置

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

また、ポートのトラブルシューティングを行う方法については、次のセクションを読み取る必要があります。

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Windows Server で必要なポートを開く: のトラブルシューティング

ほとんどの設定では、ASP.NET と Web 配置のインストールに必要なポートが開かれます。 ただし、ポートが開いていることを確認する必要があります。

> [!NOTE]
> Azure VM 上でポートを開く必要があります、[ネットワーク セキュリティ グループ](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80)します。 

必要なポート:

* 80 に必要な IIS 用。
* 8172-Visual Studio からアプリのデプロイへの Web 配置に必要な

1. Windows Server 上のポートを開くを開き、**開始**メニューで、検索**セキュリティが強化された Windows ファイアウォール**します。

2. クリックして**受信の規則** > **新しいルール** > **ポート**します。 選択**次へ** **特定のローカル ポート**をポート番号を入力し、をクリックして**次へ**、し**接続を許可する**、次へ をクリックし、名前を追加 (**IIS**、 **Web Deploy**、または**msvsmon**)、受信の規則にします。

    詳細について、Windows ファイアウォールを構成する場合を参照してください。[リモート デバッグ用の Windows ファイアウォールを構成する](../debugger/configure-the-windows-firewall-for-remote-debugging.md)します。

3. その他の必要なポートの追加の規則を作成します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポートしたや、IIS に ASP.NET アプリを展開発行設定ファイルを作成します。 インポートすることでデプロイすることもできます。 設定を発行します。

> [!div class="nextstepaction"]
> [デプロイをインポートすることによって IIS に発行設定](../deployment/tutorial-import-publish-settings-iis.md)
