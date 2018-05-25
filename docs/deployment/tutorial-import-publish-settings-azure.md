---
title: インポートすることによって Azure に発行発行の設定
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2cf6c17f3017bb1021423b19b32b36749fe0744d
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>インポートすることによって Azure App Service にアプリケーションを公開 Visual Studio で発行設定

使用することができます、**発行**をインポートするツールの設定を発行し、アプリを展開します。 この記事では使用して Azure の App Service の発行設定しますが、使用することをインポートするのと同様の手順から設定を発行する[IIS](../deployment/tutorial-import-publish-settings-iis.md)です。 一部のシナリオでは、発行設定プロファイルを Visual Studio のインストールごとに、サービスへの展開を手動で構成するよりも高速にすることができますの使用します。

次の手順は、Visual Studio での ASP.NET、ASP.NET Core と .NET Core のアプリに適用されます。 インポートすることも発行の設定[Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio)アプリ。 手順は、Visual Studio 2017 15.6 のバージョンに対応します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * Azure App Service からの発行設定ファイルを生成します。
> * 発行設定ファイルを Visual Studio にインポートします。
> * Azure App Service にアプリを配置します。

発行設定ファイル (*\*.publishsettings*) 発行プロファイルとは異なる (*\*.pubxml*) Visual Studio で作成します。 発行設定ファイルが Azure App Service によって作成され、Visual Studio にし、インポートすることができます。

> [!NOTE]
> だけを Visual Studio が公開プロファイルをコピーする必要がある場合 (*\*.pubxml*ファイル) を別の Visual Studio のインストールが 1 つから、公開プロファイルを見つけることができます *\<profilename\>.pubxml*で、  *\\< projectname\>\Properties\PublishProfiles*マネージ プロジェクトの種類のフォルダーです。 Web サイト、探します、 *\App_Data*フォルダーです。 発行プロファイルは、MSBuild XML ファイルです。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 年 1 をインストールする必要があります、 **ASP.NET**と **.NET Framework**開発ワークロード。 アプリについては、.NET Core も必要があります、 **.NET Core**ワークロード。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

* Azure App Service を作成します。 詳細については、次を参照してください。 [Visual Studio を使用して Azure に ASP.NET Core web アプリを配置](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)です。 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成します。

1. Visual Studio を実行するコンピューターで次のように選択します。**ファイル > 新しいプロジェクト**です。

1. **Visual c#** または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

    指定されたプロジェクト テンプレートが見つからない場合にをクリックして、**開いている Visual Studio インストーラー**の左側のウィンドウ内のリンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 必須の Visual Studio のワークロードは、インストールする必要がありますを特定するには、この記事で前提条件を参照してください。

1. いずれかを選択**MVC** (.NET Framework) または**Web アプリケーション (モデル-ビュー-コント ローラー)** (.NET Core) のことを確認および**認証なし**を選択して、をクリックして**OK**です。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service で発行設定ファイルを作成します。

1. Azure ポータルでは、Azure App Service を開きます。

1. をクリックして**Get 発行プロファイル**ローカル プロファイルを保存するとします。

    ![発行プロファイルを取得します。](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    ファイルが、 *.publishsettings*ファイル拡張子が保存されている場所に生成されました。 次のコードでは、(より読みやすい書式) 内のファイルの部分的な例を示します。

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
    通常は、上記の *.publishsettings ファイルには、Visual Studio で、Web デプロイ、および 1 つを使用して、FTP を使用してを展開する展開に使用できる 2 つの発行プロファイルが含まれています。 上記のコードでは、Web Deploy のプロファイルが表示されます。 両方のプロファイルは、プロファイルをインポートするときに、後でインポートされます。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定のインポートおよび展開

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポート、および、Azure App Service に、ASP.NET アプリケーションを展開する発行設定ファイルを作成します。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
