---
title: 発行設定をインポートして IIS に発行する
description: 発行プロファイルを作成してインポートし、Visual Studio から IIS にアプリケーションを配置します
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 13a4210e24fe64db79be897bc159477e9b2f5a3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897387"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Visual Studio で発行設定をインポートしてアプリケーションを IIS に発行する

**[発行]** ツールを使用して、発行設定をインポートしてからアプリを配置することができます。 この記事では、IIS の発行設定を使用していますが、同様の手順を使用して [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md) の発行設定をインポートすることができます。 場合によっては、Visual Studio のインストールごとに IIS への配置を手動で構成するよりも、発行設定プロファイルを使用する方が早い場合があります。

これらの手順は、Visual Studio で ASP.NET、ASP.NET Core、および .NET Core アプリケーションに適用されます。 この手順は、Visual Studio 2017 バージョン 15.6 に対応しています。

このチュートリアルでは、次の作業を行います。

> [!div class="checklist"]
> * 発行設定ファイルを生成できるように IIS を構成する
> * 発行設定ファイルを作成する
> * 発行設定ファイルを Visual Studio にインポートする
> * IIS にアプリを配置する

発行設定ファイル (*\*.publishsettings*) は、Visual Studio で作成される発行プロファイル (*\*.pubxml*) とは異なります。 発行設定ファイルは、IIS または Azure App Service を使用して作成するか、手動で作成して Visual Studio にインポートすることができます。

> [!NOTE]
> Visual Studio 発行プロファイル (\*.pubxml ファイル) を Visual Studio のあるインストールから別のインストールにコピーするだけであれば、マネージド プロジェクトの種類の *\\<projectname\>\Properties\PublishProfiles* フォルダー内に発行プロファイル *\<profilename\>.pubxml* があります。 Web サイトについては、*\App_Data* フォルダー以下を確認してください。 発行プロファイルは MSBuild XML ファイルです。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 をインストールし、**ASP.NET** と **.NET Framework** の開発ワークロードをインストールしている必要があります。 .NET Core アプリの場合は、**.NET Core** のワークロードも必要です。

    Visual Studio をまだインストールしていない場合は、 [Visual Studio のダウンロード](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  ページに移動し、無料試用版をインストールしてください。

* IIS から発行設定ファイルを生成するには、Windows Server 2012 または Windows Server 2016 を実行しているコンピューターが必要です。また、IIS Web サーバー ロールが正しく構成されている必要があります。 ASP.NET 4.5 または ASP.NET Core もインストールする必要があります。 ASP.NET Core については、[IIS への発行](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration)に関するセクションを参照してください。 ASP.NET 4.5 については、「[IIS 8.0 Using ASP.NET 3.5 and ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)」(ASP.NET 3.5 および ASP.NET 4.5 を使用する IIS 8.0) を参照してください。

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Visual Studio で新しい ASP.NET プロジェクトを作成する

1. Visual Studio を実行しているコンピューター上で **[ファイル]** > **[新しいプロジェクト]** の順に選択します。

1. **[Visual C#]** または **[Visual Basic]** で **[Web]** を選択し、中央のウィンドウで **[ASP.NET Web アプリケーション (.NET Framework)]** または (C# のみ) **[ASP.NET Core Web アプリケーション]** を選択し、**[OK]** をクリックします。

    指定したプロジェクト テンプレートが表示されない場合は、**[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウにある **[Visual Studio インストーラーを開く]** リンクをクリックします。 Visual Studio インストーラーが起動します。 インストールする必要がある Visual Studio ワークロードを特定するには、この記事の前提条件を参照してください。

1. **[MVC]**.(.NET Framework) または **[Web アプリケーション (モデル ビュー コントローラー)]** (.NET Core の場合)、**[認証なし]** がオンであることを確認してから **[OK]** をクリックします。

1. 「**MyWebApp**」のような名前を入力し、**[OK]** をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **[ビルド]** > **[ソリューションのビルド]** の順に選択し、プロジェクトをビルドします。

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Windows Server に Web 配置をインストールして構成する

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Windows Server 上の IIS に発行設定ファイルを作成する

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Visual Studio で発行設定をインポートして配置する

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

アプリが正常に配置されたら、自動的に起動されます。 Visual Studio から起動しない場合は、IIS でアプリを起動します。 ASP.NET Core の場合、**DefaultAppPool** の [アプリケーション プール] フィールドが **[マネージド コードなし]** に設定されていることを確認する必要があります。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、発行設定ファイルを作成して Visual Studio にインポートし、IIS に ASP.NET アプリを配置しました。 Visual Studio の他の発行オプションの概要を確認することができます。

> [!div class="nextstepaction"]
> [配置でのはじめに](../deployment/deploying-applications-services-and-components.md)
