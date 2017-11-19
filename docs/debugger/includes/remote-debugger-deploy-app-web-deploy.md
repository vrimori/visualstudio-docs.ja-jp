---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 27cff46f5a68ef28f247aa159a2b8be5db56b0fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
Web Deploy の Web Platform Installer を使用してをインストールした場合は、Visual Studio から直接アプリを展開することができます。

1. 管理者特権で Visual Studio を起動し、プロジェクトを再度開きます。

    Web Deploy を使用してアプリを展開するには、管理者特権が必要です。

2. **ソリューション エクスプローラー**で、プロジェクト ノードを右クリックして **[公開]**を選択します。

3. **発行先の選択****[ IIS、FTP など]** をクリック**発行**です。

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

4. IIS のセットアップの修正の構成パラメーターを入力します。

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    次のステップでの検証しようとすると、ホスト名が解決しない場合は、**サーバー**テキスト ボックスに、IP アドレスを再試行してください。 含める`http://`でのプレフィックスとして、**サーバー**フィールドです。  ポート 80 を使用するかどうかを確認、**サーバー**テキスト ボックス、およびポート 80 がファイアウォールで開かれているかどうかを確認します。

6. をクリックして**[次へ]**、選択、**デバッグ**構成を選択し、**先で追加ファイルを削除**下にある、**ファイルを発行**オプション。

    > [!NOTE]
    > リリース構成を選択した場合の公開時に、web.config ファイルでデバッグを無効にします。

5. をクリックして**Prev**を選択し**検証**です。 場合は、接続の設定の検証と、発行しようとすることができます。

6. をクリックして**発行**アプリを発行します。

    [出力] タブは、発行が成功するとお使いのブラウザーが、アプリを開きますを示しています。

    Web Deploy に言及しているエラーが発生した場合、Web Deploy のインストール手順を再確認し、正しいポートが開いているかどうかを確認 (Web Deploy ポート 8172 を開く、サーバーが必要も)。

    アプリが正常に配置が正しく動作しない場合は、IIS の構成、ASP.NET のインストール、または Web サイトの構成の問題である可能性があります。 Windows Server で具体的なエラー メッセージを IIS から Web サイトを開くし、前の手順を再確認します。