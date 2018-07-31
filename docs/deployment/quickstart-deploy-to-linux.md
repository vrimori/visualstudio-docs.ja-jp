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
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341749"
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

## <a name="clean-up-resources"></a>リソースをクリーンアップする

上記の手順では、リソース グループ内の Azure リソースを作成します。 これらのリソースを今後必要に予定がない場合は、リソース グループを削除することによって削除できます。
Azure portal で左側のメニューから選択**リソース グループ**選び**myResourceGroup**します。
リソース グループ ページで、表示されたリソースが削除するものになっていることを確認します。
選択**削除**、型**myResourceGroup**でクリックしてテキスト ボックスに、**削除**します。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して Linux で App Service へのデプロイの発行プロファイルを作成する方法について説明しました。 詳細については、Azure を使用して Linux に発行することができます。

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
