---
title: インポートすることによって Azure に発行する発行の設定
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808322"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>インポートして Azure App Service にアプリケーションを発行する Visual Studio で発行の設定

使用することができます、**発行**をインポートするツール発行の設定とアプリをデプロイします。 この記事では使用して、Azure App Service の発行設定しますが、使用することができますをインポートする同様の手順から設定を発行する[IIS](../deployment/tutorial-import-publish-settings-iis.md)。 一部のシナリオでの使用の発行設定プロファイルが Visual Studio のインストールごとに、サービスへの展開を手動で構成するよりも高速にすることができます。

次の手順は、Visual Studio で ASP.NET、ASP.NET Core、および .NET Core アプリに適用されます。 インポートすることも発行の設定[Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)アプリ。 手順は、Visual Studio 2017 バージョン 15.6 に対応します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * Azure App Service から発行設定ファイルを生成します。
> * 発行設定ファイルを Visual Studio にインポートします。
> * Azure App Service へのアプリをデプロイします。

発行設定ファイル (*\*.publishsettings*) 発行プロファイルとは異なります (*\*.pubxml*) Visual Studio で作成します。 発行設定ファイルは、Azure App Service によって作成され、Visual Studio にし、インポートすることができます。

> [!NOTE]
> だけ、Visual Studio の発行プロファイルをコピーする必要がある場合 (*\*.pubxml*ファイル) から別の Visual Studio の 1 つのインストール、発行のプロファイルを見つけることができます *\<profilename\>.pubxml*の *\\< projectname\>\Properties\PublishProfiles*マネージ プロジェクトの種類のフォルダー。 Web サイト、探します、 *\App_Data*フォルダー。 発行プロファイルは、MSBuild XML ファイルです。

## <a name="prerequisites"></a>前提条件

* Visual Studio 2017 をインストールする必要があります、 **ASP.NET**および **。NET Framework**開発ワークロード。 .NET Core アプリも必要があります、します。**NET Core**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

* Azure App Service を作成します。 詳細については、次を参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリのデプロイ](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)します。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成します。

1. Visual Studio が実行されているコンピューターで、次のように選択します。**ファイル** > **新しいプロジェクト**します。

1. **Visual c#** または**Visual Basic**、選択**Web**、中央のペインのいずれかを [ **ASP.NET Web アプリケーション (.NET Framework)** または (c# のみ) **ASP.NET Core Web アプリケーション**、] をクリックし、 **OK**します。

    指定されたプロジェクト テンプレートが表示されない場合にクリックして、 **Visual Studio インストーラーを開く**の左側のウィンドウで、リンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 インストールする必要がありますが、必要な Visual Studio ワークロードを特定するには、この記事で前提条件を参照してください。

1. いずれかを選択**MVC** (.NET Framework) または**Web アプリケーション (モデル-ビュー-コント ローラー)** (.NET Core) のことを確認および**認証なし**が選択されているし、順にクリックします**OK**します。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. 選択**ビルド** > **ソリューションのビルド**プロジェクトをビルドします。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service での発行設定ファイルを作成します。

1. Azure portal では、Azure App Service を開きます。

1. クリックして**発行プロファイルの取得**ローカル プロファイルを保存します。

    ![発行プロファイルを取得します。](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    ファイルを *.publishsettings*保存した場所にファイル拡張子が生成されました。 次のコードでは、(より読みやすい書式) 内のファイルの部分の例を示します。

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    通常は、上記の *.publishsettings ファイルには、FTP を使用してデプロイする Web デプロイ、および 1 つを使用してデプロイする 1 つの Visual Studio で使用できる 2 つの発行プロファイルが含まれています。 上記のコードでは、Web Deploy プロファイルが表示されます。 両方のプロファイルは、プロファイルをインポートするときに、後でインポートされます。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートおよび展開

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポートしたや、Azure App Service に ASP.NET アプリを展開発行設定ファイルを作成します。 Visual Studio での公開オプションの概要が必要な場合があります。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
