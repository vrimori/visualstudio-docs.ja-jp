---
title: Visual Studio の web サイトへの公開 |Microsoft ドキュメント
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
- multiple
ms.openlocfilehash: 0f722dcc4ada5643f9de3342b85469fa667d4b7c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766553"
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Visual Studio 発行ツールを使用して web サイトに web アプリまたは .NET Core アプリを発行します。

使用することができます、**発行**ASP.NET アプリ、web サイトを発行するためのツールです。

次の手順は、ASP.NET、ASP.NET Core、.NET Core および Visual Studio での Python アプリに適用されます。 For Node.js、手順がサポートされますが、ユーザー インターフェイスが異なる。

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

## <a name="publish-to-a-web-site"></a>Web サイトに発行します。

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish-aspnet.png "選択発行")

1. 任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイルを作成**です。

1. **発行先の選択** ダイアログ ボックスで、選択**IIS、FTP、等**です。

    ![IIS、FTP などの選択](../deployment/media/quickstart-publish-iis-ftp.png "IIS の選択、FTP などです。")

1. **[発行]** をクリックします。

    プロファイル、発行設定 ダイアログ ボックスが表示されます。

    ![フォルダーを選択](../deployment/media/quickstart-publish-settings-web.png "フォルダーを選択します")

1. **発行方法**フィールドなどのメソッドを選択**Web Deploy**または**FTP**です。

    表示される設定は、次に、発行メソッドに対応しています。 Web Deploy は、IIS サーバーに Web アプリケーションと Web サイトの展開を簡略化され、サーバー上のアプリケーションとしてインストールする必要があります。 使用して、 [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)をインストールします。

1. 発行メソッドに必要な設定を構成し、をクリックして**接続の検証**です。

    サーバーまたはターゲットが使用可能な設定が正しい場合は、接続を示すメッセージが検証され、発行する準備ができたらが表示されます。

    ![接続の確認](../deployment/media/quickstart-publish-web-deploy.png "接続の確認")

1. その他の展開設定を構成する場合は、クリックして**設定**です。

    デバッグまたはリリース構成を展開し、をクリックするかどうかなどのオプションを構成する**保存**です。 リモートでデバッグする場合は、デバッグ構成が必要です。

1. 発行するクリックして**発行**です。

    出力ウィンドウは、展開の進行状況と結果を表示します。

## <a name="next-steps"></a>次の手順

このクイック スタートでは、Visual Studio を使用して、発行プロファイルを作成する方法について学習しました。 パブリッシングを構成することもできます。 発行の設定をインポートしてプロファイルできます。

> [!div class="nextstepaction"]
> [発行設定のインポートと IIS へのデプロイ](tutorial-import-publish-settings-iis.md)
