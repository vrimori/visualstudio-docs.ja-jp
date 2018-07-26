---
title: App Service on Linux への公開します。
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 9f79cef595b3a58426b596fc1019c59b801a02d5
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252363"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio を使用して Linux 上の App Service に ASP.NET Core アプリを発行します。

使用することができます、**発行**ASP.NET Core アプリを Azure App Service on Linux に発行するためのツール。

使用して Linux 上の App Service へのデプロイ、**発行**ツールが Visual Studio 2017 バージョン 15.7 が必要です。

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>App Service on Linux への公開します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**発行**(を使用して、または、**ビルド** > **発行**メニュー項目)。

    ![ソリューション エクスプ ローラーでプロジェクトのコンテキスト メニューの [発行] コマンド](../deployment/media/quickstart-publish.png "発行の選択")

1. 以前に任意の発行プロファイルを構成する場合、**発行**ウィンドウが表示されたらでどのケースを選択します**新しいプロファイルを作成する**します。

1. **発行先を選択** ダイアログ ボックスで、選択**App Service Linux**します。

    ![Azure App Service を選択](../deployment/media/quickstart-publish-linux.png "Azure App Service の選択")

1. **[発行]** を選びます。 **App Service の作成** ダイアログ ボックスが表示されます。 Azure アカウントでサインインし、必要に応じて、既定の app service の設定は、フィールドを設定する場合。

    ![App Service の作成](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service の作成")

1. **[作成]** を選択します。 Visual Studio は、Azure App Service にアプリを配置し、ブラウザーで web アプリを読み込みます。 プロジェクトのプロパティ**発行**サイトの URL とその他の詳細ウィンドウに表示されます。

    ![発行プロファイルの概要を示すプロパティ ウィンドウ](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して Linux で App Service へのデプロイの発行プロファイルを作成する方法について説明しました。 詳細については、Azure を使用して Linux に発行することができます。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
