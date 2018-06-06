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
ms.openlocfilehash: f91fd6e8c101b674b745c120978a47adb17c9b91
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765376"
---
# <a name="publish-an-aspnet-or-aspnet-core-app-to-azure-app-service-using-visual-studio"></a>Visual Studio を使用して Azure App Service に ASP.NET または ASP.NET Core アプリケーションを公開します。

**発行**ツールを使用して、ASP.NET、ASP.NET Core、Python、Node.js、および .NET Core のアプリを Azure App Service に発行することができます。

Azure アカウントをもっていない場合は、ここから [サインアップ](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio) することができます。

## <a name="prerequisites"></a>必須コンポーネント

* Visual Studio 2017 年 1 をインストールする必要があります、 **ASP.NET および web 開発**ワークロードと **。NET デスクトップ開発**ワークロード。 アプリについては、.NET Core する必要があります、します。**NET コア**ワークロード。

    Visual Studio をまだインストールしていない場合は、[Visual Studio のダウンロード](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ページに移動し、無料試用版をインストールしてください。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#** または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

1. 選択**MVC** (かを選択して**Web アプリケーション (モデル-ビュー-コント ローラー)** .NET core)、ことを確認して**認証なし**を選択して、をクリックして **[ok]**.

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish-aspnet.png "選択発行")

1. 任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイルを作成**です。

1. **発行先の選択** ダイアログ ボックスで、選択**App Service**です。

    ![Azure App Service の選択](../deployment/media/quickstart-publish-azure.png "Azure App Service の選択")

1. **[発行]** をクリックします。

    **App Service の作成** ダイアログ ボックスが表示されます。

    ![App Service を作成する](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service の作成")
    
1. Visual Studio にサインインしていない場合にサインインし、アプリ サービスの既定の設定フィールドに入力します。

    プロファイル、発行設定 ダイアログ ボックスが表示されます。

    ![フォルダーを選択](../deployment/media/quickstart-publish-settings-web.png "フォルダーを選択します")

    このダイアログ ボックスで使用しているサブスクリプションを選択を選択したり Azure リソース グループなどを作成します。

1. **[作成]** をクリックします。

    Visual Studio が、Azure App Service にアプリを展開し、web アプリがお使いのブラウザーで読み込まれます。

    **発行** ウィンドウの概要から、新しい Azure App Service のサイトの URL を参照してください。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して Azure へのデプロイの発行プロファイルを作成する方法について学習しました。 パブリッシングを構成することもできます。 プロファイルをインポートしてから Azure App Service の設定を発行します。

> [!div class="nextstepaction"]
> [発行設定のインポートと Azure へのデプロイ](tutorial-import-publish-settings-azure.md)
