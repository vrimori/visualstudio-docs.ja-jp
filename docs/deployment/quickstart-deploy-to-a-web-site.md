---
title: Visual Studio の web サイトへの公開 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b6bacc45d78d1d246f6a91d13549ccc96b276a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Visual Studio 発行ツールを使用して web サイトに web アプリまたは .NET Core アプリを発行します。

使用することができます、**発行**ASP.NET アプリ、web サイトを発行するためのツールです。

次の手順は、ASP.NET、ASP.NET Core、.NET Core および Visual Studio での Python アプリに適用されます。 For Node.js、手順がサポートされますが、ユーザー インターフェイスが異なる。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する 

1. Visual Studio で、**[ファイル]、[新しいプロジェクト]** の順に選択します。

1. **Visual c#**または**Visual Basic**、選択**Web**、し、中央のペインで  **ASP.NET Web アプリケーション (.NET Framework)**(C# の場合のみ)、または**ASP.NET Core Web アプリケーション**、クリックして**OK**です。

1. **MVC** を選択し、**認証なし** が選択されていることを確認して、**OK**をクリックします。

1. **MyWebApp** のような名前を入力して**OK**をクリックします。

    Visual Studio によってプロジェクトが作成されます。

1. **ビルド > ソリューションのビルド** を選択して、プロジェクトをビルドします。

## <a name="publish-to-a-web-site"></a>Web サイトに発行します。

1. ソリューション エクスプローラーで、プロジェクトを右クリックして、**[発行]** を選択します。

    ![選択発行](../deployment/media/quickstart-publish-aspnet.png "選択発行")

1. **発行** ウィンドウで、選択**IIS、FTP、等**です。

    ![IIS、FTP などの選択](../deployment/media/quickstart-publish-iis-ftp.png "IIS の選択、FTP などです。")

1. **[発行]**をクリックします。

    プロファイル、発行設定 ダイアログ ボックスが表示されます。

    ![フォルダーを選択](../deployment/media/quickstart-publish-settings-web.png "フォルダーを選択します")

1. **発行方法**フィールドなどのメソッドを選択**Web Deploy**または**FTP**です。

    表示される設定は、次に、発行メソッドに対応しています。

1. 発行メソッドに必要な設定を構成し、をクリックして**接続の検証**です。

    サーバーまたはターゲットが使用可能な設定が正しい場合は、接続を示すメッセージが検証され、発行する準備ができたらが表示されます。

    ![接続の確認](../deployment/media/quickstart-publish-web-deploy.png "接続の確認")

1. その他の展開設定を構成する場合は、クリックして**設定**です。

    デバッグまたはリリース構成を展開し、をクリックするかどうかなどのオプションを構成する**保存**です。 リモートでデバッグする場合は、デバッグ構成が必要です。

1. 発行するクリックして**発行**です。

    出力ウィンドウは、展開の進行状況と結果を表示します。

## <a name="next-steps"></a>次の手順

- [IIS に ASP.NET を配置する](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
