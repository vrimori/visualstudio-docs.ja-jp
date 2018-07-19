---
title: 公開発行の設定をインポートすることによって IIS
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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808466"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>インポートすることによって IIS にアプリケーションを発行する Visual Studio で発行の設定

使用することができます、**発行**をインポートするツール発行の設定とアプリをデプロイします。 この記事では使用して、IIS の設定を発行し、使用することが発行の設定をインポートする同様の手順[Azure App Service](../deployment/tutorial-import-publish-settings-azure.md)します。 一部のシナリオでの使用の発行設定プロファイルが Visual Studio のインストールごとに IIS への配置を手動で構成するよりも高速にすることができます。

次の手順は、Visual Studio で ASP.NET、ASP.NET Core、および .NET Core アプリに適用されます。 手順は、Visual Studio 2017 バージョン 15.6 に対応します。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 発行設定ファイルを生成できるように、IIS を構成します。
> * 発行設定ファイルを作成します。
> * 発行設定ファイルを Visual Studio にインポートします。
> * IIS へのアプリをデプロイします。

発行設定ファイル (*\*.publishsettings*) 発行プロファイルとは異なります (*\*.pubxml*) Visual Studio で作成します。 発行設定ファイルが IIS または Azure App Service では、作成者や、手動で作成することができますし、Visual Studio にインポートします。

> [!NOTE]
> だけ、Visual Studio の発行プロファイルをコピーする必要がある場合 (\*.pubxml ファイル) から別の Visual Studio の 1 つのインストール、発行のプロファイルを見つけることができます *\<profilename\>.pubxml*、 *\\< projectname\>\Properties\PublishProfiles*マネージ プロジェクトの種類のフォルダー。 Web サイト、探します、 *\App_Data*フォルダー。 発行プロファイルは、MSBuild XML ファイルです。

## <a name="prerequisites"></a>前提条件

* Visual Studio 2017 をインストールする必要があります、 **ASP.NET**と **.NET Framework**開発ワークロード。 .NET Core アプリでは、する必要も、 **.NET Core**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

* IIS から発行設定ファイルを生成するには、Windows Server 2012 または Windows Server 2016 を実行するコンピューターをいる必要があり、正しく構成されている IIS Web サーバーの役割があります。 ASP.NET 4.5 または ASP.NET Core のいずれかをインストールする必要があります。 ASP.NET Core では、次を参照してください。 [IIS への発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)します。 ASP.NET 4.5 では、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 および ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)します。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成します。

1. Visual Studio が実行されているコンピューターで、次のように選択します。**ファイル** > **新しいプロジェクト**します。

1. **Visual c#** または**Visual Basic**、選択**Web**、中央のペインのいずれかを [ **ASP.NET Web アプリケーション (.NET Framework)** または (c# のみ) **ASP.NET Core Web アプリケーション**、] をクリックし、 **OK**します。

    指定されたプロジェクト テンプレートが表示されない場合にクリックして、 **Visual Studio インストーラーを開く**の左側のウィンドウで、リンク、**新しいプロジェクト** ダイアログ ボックス。 Visual Studio インストーラーが起動します。 インストールする必要がありますが、必要な Visual Studio ワークロードを特定するには、この記事で前提条件を参照してください。

1. いずれかを選択**MVC** (.NET Framework) または**Web アプリケーション (モデル-ビュー-コント ローラー)** (.NET Core) のことを確認および**認証なし**が選択されているし、順にクリックします**OK**します。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. 選択**ビルド** > **ソリューションのビルド**プロジェクトをビルドします。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>インストールし、Windows Server で Web 配置の構成

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS での発行設定ファイルを作成します。

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートおよび展開

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常がデプロイした後、自動的に開始する必要があります。 Visual Studio から起動はしない場合は、IIS でアプリを起動します。 ASP.NET Core でのアプリケーション プールのフィールドを確認する必要があります、 **DefaultAppPool**に設定されている**マネージ コードなし**します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポートしたや、IIS に ASP.NET アプリを展開発行設定ファイルを作成します。 Visual Studio の他の発行オプションの概要が必要な場合があります。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
