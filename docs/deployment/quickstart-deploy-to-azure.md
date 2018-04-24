---
title: Azure App Service の Visual Studio への公開 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: dd3fa975070656f54a48452a50e51c172d51c785
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Visual Studio を使用して Azure App Service に ASP.NET または ASP.NET Core アプリケーションを公開します。

**発行**ツールを使用して、ASP.NET、ASP.NET Core、Python、Node.js、および .NET Core のアプリを Azure App Service に発行することができます。

Azure アカウントをもっていない場合は、ここから [サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio) することができます。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#**または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

1. **MVC** を選択し、**認証なし** が選択されていることを確認して、**OK**をクリックします。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish-aspnet.png "選択発行")

1. **発行** ウィンドウで、**Microsoft Azure App Service** を選択します。

    ![Azure App Service の選択](../deployment/media/quickstart-publish-azure.png "Azure App Service の選択")

1. **[発行]**をクリックします。

    **App Service の作成** ダイアログ ボックスが表示されます。

    ![App Service を作成する](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service の作成")
    
1. Visual Studio にサインインしていない場合にサインインし、アプリ サービスの既定の設定フィールドに入力します。

    プロファイル、発行設定 ダイアログ ボックスが表示されます。

    ![フォルダーを選択](../deployment/media/quickstart-publish-settings-web.png "フォルダーを選択します")

    このダイアログ ボックスで使用しているサブスクリプションを選択を選択したり Azure リソース グループなどを作成します。

1. **[作成]**をクリックします。

    Visual Studio が、Azure App Service にアプリを展開し、web アプリがお使いのブラウザーで読み込まれます。

    **発行** ウィンドウの概要から、新しい Azure App Service のサイトの URL を参照してください。

## <a name="next-steps"></a>次の手順

- [Azure への ASP.NET Core アプリケーションを配置します。](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Git を使用した Azure への ASP.NET Core の継続的な配置](/aspnet/core/publishing/azure-continuous-deployment)
