---
title: App Service on Linux に発行する
ms.date: 07/23/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- azure
ms.openlocfilehash: 3e80f96e1af39747a6dfa9fb9737ec11bb5baf00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951938"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Visual Studio を使用して App Service on Linux に ASP.NET Core アプリを発行する

**発行**ツールを使用して、App Service on Linux に ASP.NET Core アプリを発行することができます。

**発行**ツールを使用して App Service on Linux にデプロイするには、Visual Studio 2017 バージョン 15.7 が必要です。

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>App Service on Linux に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します (または **[ビルド]** > **[発行]** メニュー項目を使用します)。

    ![ソリューション エクスプローラーのプロジェクト コンテキスト メニューにある [発行] コマンド](../deployment/media/quickstart-publish.png "[発行] を選択する")

1. 以前に発行プロファイルを構成した場合、**[発行]** ウィンドウが表示されます。その場合は、**[新しいプロファイルの作成]** を選択します。

1. **[発行先を選択]** ダイアログ ボックスで、**[App Service Linux]** を選びます。

    ![Azure App Service を選択する](../deployment/media/quickstart-publish-linux.png "Azure App Service を選択する")

1. **[発行]** を選びます。 **[App Service の作成]** ダイアログ ボックスが表示されます。 必要に応じて、Azure アカウントでサインインすると、既定のアプリ サービス設定がフィールドに取り込まれます。

    ![App Service の作成](../deployment/media/quickstart-publish-settings-app-service-linux.png "Azure App Service の作成")

1. **[作成]** を選択します。 Visual Studio によってアプリが Azure App Service にデプロイされ、ブラウザに Web アプリが読み込まれます。 プロジェクト プロパティの **[発行]** ウィンドウに、サイト URL とその他の詳細が示されます。

    ![プロファイルの概要を示す [発行] プロパティ ウィンドウ](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>リソースをクリーンアップする

上記の手順では、リソース グループに Azure リソースを作成しました。 今後、これらのリソースを必要としない場合は、リソース グループを削除することでリソースを削除できます。
Azure portal の左側のメニューから、**[リソース グループ]**、**[myResourceGroup]** の順に選択します。
リソース グループ ページで、リストされたリソースが削除対象であることを確認します。
**[削除]** を選択し、テキスト ボックスに「**myResourceGroup**」と入力してから、**[削除]** を選びます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して、App Service on Linux にデプロイするための発行プロファイルを作成する方法を学習しました。 Azure を使用する Linux への発行に関する詳細を確認できます。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
