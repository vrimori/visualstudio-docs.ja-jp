---
title: Web サイトに発行します。
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077504"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Visual Studio を使用して web サイトに Web アプリを発行します。

使用することができます、**発行**Visual Studio から web サイトに ASP.NET、ASP.NET Core、.NET Core、および Python のアプリを発行するためのツール。 For Node.js が手順がサポートされていますが、ユーザー インターフェイスは異なります。

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Web サイトに発行します。

1. ソリューション エクスプ ローラーでプロジェクトを右クリックし、選択**発行**(を使用して、または、**ビルド** > **発行**メニュー項目)。

    ![ソリューション エクスプ ローラーでプロジェクトのコンテキスト メニューの [発行] コマンド](../deployment/media/quickstart-publish.png "発行の選択")

1. 以前に任意の発行プロファイルを構成する場合、**発行**ウィンドウが表示されます。 選択**新しいプロファイルを作成する**します。

1. **発行先を選択** ダイアログ ボックスで、選択**IIS、FTP など**します。

    ![IIS、FTP などの選択](../deployment/media/quickstart-publish-iis-ftp.png "選択 IIS、FTP など。")

1. **[発行]** を選びます。 プロファイルの発行設定 ダイアログ ボックスが表示されます。

    ![フォルダーを選択して](../deployment/media/quickstart-publish-settings-web.png "フォルダーの選択")

1. **メソッドを公開**フィールドに、メソッドを選択します。 **Web Deploy**または**FTP**します。 表示される設定は、次に、公開方法に対応します。 Web Deploy では、Web アプリケーションや Web サイトの IIS サーバーへのデプロイを簡略化し、サーバー上のアプリケーションとしてインストールする必要があります。 使用して、 [Web プラットフォーム インストーラー](https://www.microsoft.com/web/downloads/platform.aspx)をインストールします。

1. 発行方法に必要な設定を構成し、選択**接続の検証**です。 サーバーまたはターゲットが使用可能な設定が正しい場合は、接続を示すメッセージが検証されると、および発行する準備ができました。

    ![接続の確認](../deployment/media/quickstart-publish-web-deploy.png "接続の確認")

1. 選択**設定**、デバッグまたはリリース構成をデプロイしを選択するかどうかなど、他の展開設定を構成する**保存**します。 リモートでデバッグしている場合は、デバッグ構成が必要です。

1. を発行する**発行**します。 出力ウィンドウには、デプロイの進行状況と結果が表示されます。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して、発行プロファイルを作成する方法について説明しました。 発行を構成することもできます。 プロファイルをインポートして発行設定します。

> [!div class="nextstepaction"]
> [発行設定のインポートと IIS へのデプロイ](tutorial-import-publish-settings-iis.md)
