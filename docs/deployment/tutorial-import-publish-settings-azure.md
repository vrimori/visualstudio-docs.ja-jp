---
title: 発行設定をインポートして Azure に発行する
description: 発行プロファイルを作成してインポートし、Visual Studio から Azure App Service にアプリケーションを配置する
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98498b59f01bbd8a72a52695203d80a995497823
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690464"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Visual Studio で発行設定をインポートしてアプリケーションを Azure App Service に発行する

**[発行]** ツールを使用して、発行設定をインポートしてからアプリを配置することができます。 この記事では、Azure App Service の発行設定を使用していますが、同様の手順を使用して [IIS](../deployment/tutorial-import-publish-settings-iis.md) から発行設定をインポートすることができます。 場合によっては、Visual Studio のインストールごとにサービスへの配置を手動で構成するよりも、発行設定プロファイルを使用する方が早い場合があります。

これらの手順は、Visual Studio で ASP.NET、ASP.NET Core、および .NET Core アプリケーションに適用されます。 [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) アプリ用の発行設定をインポートすることもできます。 この手順は、Visual Studio 2017 バージョン 15.6 に対応しています。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * Azure App Service から発行設定ファイルを生成する
> * 発行設定ファイルを Visual Studio にインポートする
> * Azure App Service にアプリを配置する

発行設定ファイル (*\*.publishsettings*) は、Visual Studio で作成される発行プロファイル (*\*.pubxml*) とは異なります。 発行設定ファイルは Azure App Service によって作成され、Visual Studio にインポートできます。

> [!NOTE]
> Visual Studio 発行プロファイル (*\*.pubxml* ファイル) を Visual Studio のあるインストールから別のインストールにコピーするだけであれば、マネージド プロジェクトの種類の *\\<projectname\>\Properties\PublishProfiles* フォルダー内に発行プロファイル *\<profilename\>.pubxml* があります。 Web サイトについては、*\App_Data* フォルダー以下を確認してください。 発行プロファイルは MSBuild XML ファイルです。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 をインストールし、ASP.NET と **Web 開発**のワークロードを用意する必要があります。

    Visual Studio をまだインストールしていない場合は、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)  ページに移動し、無料試用版をインストールしてください。

* Azure App Service を作成します。 詳細な手順については、「[Visual Studio を使用して Azure に ASP.NET Core アプリを発行する](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)」を参照してください。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成する

1. Visual Studio を実行しているコンピューター上で **[ファイル]** > **[新しいプロジェクト]** の順に選択します。

1. **[Visual C#]** または **[Visual Basic]** で **[Web]** を選択し、中央のウィンドウで **[ASP.NET Web アプリケーション (.NET Framework)]** または (C# のみ) **[ASP.NET Core Web アプリケーション]** を選択し、**[OK]** をクリックします。

    指定したプロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 **ASP.NET と Web 開発**ワークロードをインストールします。

1. **[MVC]**.(.NET Framework) または **[Web アプリケーション (モデル ビュー コントローラー)]** (.NET Core の場合)、**[認証なし]** がオンであることを確認してから **[OK]** をクリックします。

1. 「**MyWebApp**」のような名前を入力し、**[OK]** をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **[ビルド]** > **[ソリューションのビルド]** の順に選択し、プロジェクトをビルドします。

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Azure App Service で発行設定ファイルを作成する

1. Azure portal で Azure App Service を開きます。

1. **[発行プロファイルの取得]** をクリックし、プロファイルをローカルに保存します。

    ![発行プロファイル名の取得](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    拡張子が *.publishsettings* のファイルは、保存した場所に生成されています。 次のコードは、ファイルの一部の例を読みやすい形式で示しています。

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
    通常、前述の *.publishsettings ファイルには、Visual Studio で使用できる 2 つの発行プロファイル (Web Deploy を使用して配置するものと、FTP を使用して配置するもの) が含まれています。 上記のコードは Web Deploy プロファイルを示しています。 いずれのプロファイルも、後でプロファイルをインポートするときにインポートされます。

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートして配置する

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>次の手順

このチュートリアルでは、発行設定ファイルを作成して Visual Studio にインポートし、Azure App Service に ASP.NET アプリを配置しました。 Visual Studio の発行オプションの概要を確認することができます。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
