---
title: Web Deploy を使用して配置
description: Visual Studio で Web Deploy を使用してアプリを配置します。
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
Web Deploy の Web Platform Installer を使用してをインストールした場合は、Visual Studio から直接アプリを展開することができます。

1. 管理者特権で Visual Studio を起動し、プロジェクトを再度開きます。

    Web Deploy を使用してアプリを展開するには、管理者特権が必要です。

1. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックして **[公開]** を選択します。

    任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイル**です。

1. **発行先の選択****[IIS、FTP など]** をクリック**発行**です。

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. IIS のセットアップの修正の構成パラメーターを入力します。

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    次のステップでの検証しようとすると、ホスト名が解決しない場合は、**サーバー**テキスト ボックスに、IP アドレスを再試行してください。 含める`http://`でのプレフィックスとして、**サーバー**フィールドです。  ポート 80 を使用するかどうかを確認、**サーバー**テキスト ボックス、およびポート 80 がファイアウォールで開かれているかどうかを確認します。

1. をクリックして **[次へ]**、選択、**デバッグ**構成を選択し、**先で追加ファイルを削除**下にある、**ファイルを発行**オプション。

    > [!NOTE]
    > リリース構成を選択した場合の公開時に、web.config ファイルでデバッグを無効にします。

1. をクリックして**Prev**を選択し**検証**です。 場合は、接続の設定の検証と、発行しようとすることができます。

1. をクリックして**発行**アプリを発行します。

    [出力] タブは、発行が成功するとお使いのブラウザーが、アプリを開きますを示しています。

    Web Deploy に言及しているエラーが発生した場合、Web Deploy のインストール手順を再確認し、正しいポートが開いているかどうかを確認 (Web Deploy ポート 8172 を開く、サーバーが必要も)。

    アプリが正常に配置が正しく動作しない場合は、IIS の構成、ASP.NET のインストール、または Web サイトの構成の問題である可能性があります。 Windows Server で具体的なエラー メッセージを IIS から Web サイトを開くし、前の手順を再確認します。
