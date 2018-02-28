---
title: "Azure App Service の Visual Studio への公開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- azure
ms.openlocfilehash: 52da1a2e618d9ececa1c8fd0d90a86e651cd7fde
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Visual Studio を使用して Azure App Service に ASP.NET または ASP.NET Core アプリケーションを公開します。

使用することができます、**発行**ツールを Azure App Service に ASP.NET、ASP.NET Core、Python、Node.js、および .NET Core のアプリを発行します。

Azure アカウントがない場合は[サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio)です。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#**または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

1. 選択**MVC**、ことを確認して**認証なし**を選択して、をクリックして**OK**です。

1. ような名前を入力**MyWebApp**  をクリック**OK**です。

    Visual Studio によってプロジェクトが作成されます。

1. 選択**ビルド > ソリューションのビルド**プロジェクトをビルドします。

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish-aspnet.png "選択発行")

1. **発行** ウィンドウで、選択**Microsoft Azure App Service**です。

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

    概要、**発行** ウィンドウで、新しい Azure App Service のサイトの URL を参照してください。

## <a name="next-steps"></a>次の手順

- [Azure への ASP.NET Core アプリケーションを配置します。](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Git を使用した Azure への ASP.NET Core の継続的な配置](/aspnet/core/publishing/azure-continuous-deployment)
