---
title: Azure App Service に発行する
ms.date: 06/22/2018
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 4e7cf13658c33caf6b58d6a4e661a8431f377845
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853594"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Visual Studio を使用して Azure App Service に Web アプリを発行する

**発行**ツールを使用して、ASP.NET、ASP.NET Core、Node.js、および .NET Core アプリを Azure App Service や Azure App Service Linux (コンテナーを使用) に発行することができます。 Python アプリの場合は、[Python - Azure App Service への発行](../python/publishing-python-web-applications-to-azure-from-visual-studio.md)に関するページの手順に従います。

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Azure App Service に発行する

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します (または **[ビルド]** > **[発行]** メニュー項目を使用します)。

    ![ソリューション エクスプローラーのプロジェクト コンテキスト メニューにある [発行] コマンド](../deployment/media/quickstart-publish.png "[発行] を選択する")

1. 以前に発行プロファイルを構成した場合、**[発行]** ウィンドウが表示されます。その場合は、**[新しいプロファイルの作成]** を選択します。

1. **[発行先を選択]** ダイアログ ボックスで、**[App Service]** を選びます。

    ![Azure App Service を選択する](../deployment/media/quickstart-publish-azure.png "Azure App Service を選択する")

1. **[発行]** を選びます。 **[App Service の作成]** ダイアログ ボックスが表示されます。 必要に応じて、Azure アカウントでサインインすると、既定のアプリ サービス設定がフィールドに取り込まれます。

    ![App Service の作成](../deployment/media/quickstart-publish-settings-app-service.png "Azure App Service の作成")

1. **[作成]** を選択します。 Visual Studio によってアプリが Azure App Service にデプロイされ、ブラウザに Web アプリが読み込まれます。 プロジェクト プロパティの **[発行]** ウィンドウに、サイト URL とその他の詳細が示されます。

    ![プロファイルの概要を示す [発行] プロパティ ウィンドウ](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>リソースをクリーンアップする

上記の手順では、リソース グループに Azure リソースを作成しました。 今後、これらのリソースを必要としない場合は、リソース グループを削除することでリソースを削除できます。
Azure portal の左側のメニューから、**[リソース グループ]**、**[myResourceGroup]** の順に選択します。
リソース グループ ページで、リストされたリソースが削除対象であることを確認します。
**[削除]** を選択し、テキスト ボックスに「**myResourceGroup**」と入力してから、**[削除]** を選びます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して、Azure にデプロイするための発行プロファイルを作成する方法を学習しました。 Azure App Service から発行設定をインポートして、発行プロファイルを構成することもできます。

> [!div class="nextstepaction"]
> [発行設定のインポートと Azure へのデプロイ](tutorial-import-publish-settings-azure.md)
