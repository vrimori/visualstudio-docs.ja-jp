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
ms.openlocfilehash: 907fecd348dba46f6d3375d2d994b04ec1cf1eb5
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
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

* Visual Studio 2017 年 1 をインストールする必要があります、 **ASP.NET**と **.NET Framework**開発ワークロード。 アプリについては、.NET Core も必要があります、 **.NET Core**ワークロード。

    まだ Visual Studio をインストールしていない場合は、[ここ](http://www.visualstudio.com)から無料でインストールできます。

* IIS から発行設定ファイルを生成するには Windows Server 2012 または Windows Server 2016 を実行しているコンピューターが必要し、正しく構成されている IIS Web サーバーの役割をする必要があります。 ASP.NET 4.5 または ASP.NET Core のいずれかをインストールする必要があります。 ASP.NET Core では、次を参照してください。[を IIS に発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)です。 ASP.NET 4.5 では、次を参照してください。 [IIS 8.0 を使用して ASP.NET 3.5 と ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)です。

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

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定のインポートおよび展開

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常に配置した後、自動的に開始する必要があります。 Visual Studio から起動はしない場合は、IIS でアプリを起動します。 ASP.NET core アプリケーション プールのフィールドをかどうかを確認する必要があります、 **DefaultAppPool**に設定されている**マネージ コードなし**です。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Visual Studio にインポート、および、IIS に ASP.NET アプリケーションを展開する発行設定ファイルを作成します。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
