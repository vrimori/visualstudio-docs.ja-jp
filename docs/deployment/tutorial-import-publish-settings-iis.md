---
title: 公開をインポートして IIS の設定を発行します。
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b023349454f71835e13e7cc891b8be92b90c153f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>インポートすることによって IIS にアプリケーションを公開 Visual Studio で発行設定

使用することができます、**発行**をインポートするツールの設定を発行し、アプリを展開します。 この記事では使用して、IIS の発行設定しますが、使用することをインポートするのと同様の手順の発行設定[Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)です。 一部のシナリオでは、発行設定プロファイルを Visual Studio のインストールごとに、IIS への配置を手動で構成するよりも高速にすることができますの使用します。

次の手順は、Visual Studio での ASP.NET、ASP.NET Core と .NET Core のアプリに適用されます。 手順は、Visual Studio 2017 15.6 のバージョンに対応します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 発行設定ファイルを生成できるように、IIS を構成します。
> * 発行設定ファイルを作成します。
> * 発行設定ファイルを Visual Studio にインポートします。
> * IIS にアプリを配置します。

発行設定ファイル (*\*.publishsettings*) 発行プロファイルとは異なる (*\*.pubxml*) Visual Studio で作成します。 発行設定ファイルを IIS または Azure App Service によって作成や、手動で作成することができますし、Visual Studio にインポートします。

> [!NOTE]
> だけを Visual Studio が公開プロファイルをコピーする必要がある場合 (\*.pubxml ファイル) を別の Visual Studio のインストールが 1 つから、公開プロファイルを見つけることができます *\<profilename\>.pubxml*、 *\\< projectname\>\Properties\PublishProfiles*マネージ プロジェクトの種類のフォルダーです。 Web サイト、探します、 *\App_Data*フォルダーです。 発行プロファイルは、MSBuild XML ファイルです。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio をインストールする必要があります、 **ASP.NET**と **.NET Framework**開発ワークロード。 アプリについては、.NET Core も必要があります、 **.NET Core**ワークロード。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

    この記事の手順では Visual Studio 2017 に基づいてに並べ替えられます。

* IIS から発行設定ファイルを生成するには IIS 8.0 Web サーバーの役割が正しく構成されている Windows Server 2012 を実行しているコンピューターが必要し、ASP.NET 4.5 または ASP.NET Core のいずれかがインストールされています。 ASP.NET Core では、次を参照してください。[を IIS に発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)です。 ASP.NET 4.5 では、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成します。

1. Visual Studio を実行するコンピューターで次のように選択します。**ファイル > 新しいプロジェクト**です。

1. **Visual c#** または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

    指定されたプロジェクト テンプレートが見つからない場合にをクリックして、**開いている Visual Studio インストーラー**の左側のウィンドウ内のリンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 必須の Visual Studio のワークロードは、インストールする必要がありますを特定するには、この記事で前提条件を参照してください。

1. いずれかを選択**MVC** (.NET Framework) または**Web アプリケーション (モデル-ビュー-コント ローラー)** (.NET Core) のことを確認および**認証なし**を選択して、をクリックして**OK**です。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>インストールして Windows Server で Web Deploy を構成します。

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS に発行設定ファイルを作成します。

1. IIS を右クリックし、**既定の Web サイト**、選択**展開** > **Web 配置をパブリッシング**です。

    ![Web 配置の構成を構成します。](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. **Web 配置をパブリッシング** ダイアログ ボックスで、設定を確認します。

1. をクリックして**セットアップ**です。

    **結果**パネルで、アクセス権を出力結果に与えられていることと、指定したユーザーのファイルが、 *.publishsettings*で表示されている場所で生成されたファイル拡張子、ダイアログ ボックス。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Windows Server および IIS の構成によって異なる値が表示されます。 次に、いくつかの詳細が表示される値を示します。

    * *Msdeploy.axd*で参照されているファイル、`publishUrl`属性は Web Deploy を動的に生成されたファイルの HTTP ハンドラー。 (テスト目的で`http://myhostname:8172`一般にも同様に機能します)。
    * `publishUrl`ポートは通常は Web Deploy の既定ポート 8172 に設定します。
    * `destinationAppUrl`ポートは通常は IIS の既定ポート 80 に設定します。
    * (後の手順) でホスト名を使用して Visual Studio でリモート ホストに接続できない場合は、ホスト名の代わりに IP アドレスをテストします。

    > [!NOTE]
    > Azure VM で実行されている IIS に発行する場合、Web デプロイおよび IIS のポートは、ネットワーク セキュリティ グループで開く必要があります。 詳細については、次を参照してください。[実行 IIS をインストールして](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic)です。

1. このファイルを Visual Studio が実行されているコンピューターにコピーします。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定のインポートおよび展開

1. ASP.NET プロジェクトを Visual Studio で開くがあるコンピューターで、ソリューション エクスプ ローラーでプロジェクトを右クリックし **発行**です。

1. 任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイルを作成**です。

1. **発行先の選択**ダイアログ ボックスで、をクリックして**プロファイルのインポート**です。

    ![選択を発行](../deployment/media/tutorial-publish-tool-import-profile.png)

1. 前のセクションで作成した発行設定ファイルの場所に移動します。

1. **発行設定ファイルのインポート**ダイアログ ボックスに移動し、前のセクションで作成したプロファイルを選択し、をクリックして**開く**です。

    Visual Studio は、展開プロセスを開始し、進行状況と結果は、出力ウィンドウを示しています。

    場合は、任意の展開エラーが発生する、クリックして**設定**設定を編集します。 設定を変更し、をクリックして**検証**新しい設定をテストします。

    ![発行ツールで設定を編集します。](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポート、および、IIS に ASP.NET アプリケーションを展開する発行設定ファイルを作成します。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
