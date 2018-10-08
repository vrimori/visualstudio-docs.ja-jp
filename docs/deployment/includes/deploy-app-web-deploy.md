---
title: Web Deploy を使用してデプロイ
description: Visual Studio で Web Deploy を使用してアプリをデプロイします。
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 4ef232e64f308699c73c60cbe5b155f1d4ebb725
ms.sourcegitcommit: 1c675dae7c348defb32d9f7ccf7079a1062a1c4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244113"
---
Web Deploy の Web Platform Installer を使用してをインストールした場合は、Visual Studio から直接アプリを展開できます。

1. 管理者特権で Visual Studio を起動し、プロジェクトを再度開きます。

    Web Deploy を使用してアプリのデプロイには、管理者特権が必要です。

1. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックして **[公開]** を選択します。

    以前に任意の発行プロファイルを構成する場合、**発行**ウィンドウが表示されます。 クリックして**新しいプロファイル**します。

1. **発行先の選択**を選択します**IIS、FTP など**クリック**発行**します。

    ![RemoteDBG_Publish_IISl](../../debugger/media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. IIS のセットアップの修正の構成パラメーターを入力します。

    ![RemoteDBG_Publish_WebDeployl](../../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    次のステップでの検証しようとすると、ホスト名が解決しない場合は、**サーバー**テキスト ボックスに、IP アドレスを試してください。 含める`http://`でプレフィックスとして、 **Server**フィールド。  ポート 80 を使用するかどうかを確認、 **Server**テキスト ボックス、およびポート 80 と 8172 をポートがファイアウォールで開けることを確認します。

1. 選択**検証**です。 場合は、接続の設定の検証と、発行しようとすることができます。

1. クリックして**発行**アプリを発行します。

    [出力] タブでは、発行が成功すると、およびお使いのブラウザーから、アプリを開いたときのかどうかを示します。

    Web Deploy に言及しているエラーが発生する場合は、Web Deploy のインストール手順を再確認する正しいポートが開いているかどうかを確認して (ポート 8172 を開くサーバーの Web 配置も必要)。

    アプリが正常にデプロイが正しく動作しない場合は、IIS の構成、ASP.NET のインストール、または Web サイトの構成の問題である可能性があります。 Windows Server での具体的なエラー メッセージ、IIS から Web サイトを開くし、し、前の手順を再確認します。
