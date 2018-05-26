---
title: ローカル フォルダーに配置します。
description: アプリをローカル フォルダーに配置します。
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
1. **ソリューション エクスプ ローラー**プロジェクト ノードを右クリックし、選択、**発行**(Web フォームの**Web アプリの発行**)。

    任意の発行プロファイルを構成していない場合、**発行**ウィンドウが表示されます。 をクリックして**新しいプロファイル**です。

1. **発行**ダイアログ ボックスで、**フォルダー**をクリックして**参照**、新しいフォルダーを作成し、 **C:\Publish**です。

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    アプリについては、Web フォームを選択して**カスタム**発行 ダイアログ ボックスで、プロファイル名を入力し、選択**OK**です。

1. をクリックして**プロファイルを作成**ドロップダウン リストで (**発行**は、既定値)。

1. **発行**ダイアログ ボックスで、をクリックして、**設定**リンクをクリックして、**設定**タブです。

1. 構成を設定**デバッグ****すべての既存のファイルを発行する前に削除**、順にクリック**保存**です。

    > [!NOTE]
    > リリース ビルドを使用する場合を発行するときに、web.config ファイルでデバッグを無効にします。

1. **[発行]** をクリックします。

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    アプリケーションの発行、**デバッグ**ローカル フォルダーにプロジェクトの構成。 出力ウィンドウに進行状況を示しています。

1. Visual Studio コンピューターからの ASP.NET プロジェクト ディレクトリを ASP.NET アプリ用に構成されたローカル ディレクトリにコピー (この例では**C:\Publish**) Windows Server コンピューターにします。 このチュートリアルでは、想定していますが、手動でコピーする、PowerShell、Xcopy、Robocopy などその他のツールを使用することができます。

    > [!CAUTION]
    >  コードまたは再構築に変更を加える必要がある場合は再パブリッシュする必要がありますしてこの手順を繰り返します。 リモート コンピューターにコピーした実行可能ファイルは、ローカルのソースとシンボルに正確に一致している必要があります。    受信はこれを行わない場合、`cannot find or open the PDB file`プロセスをデバッグしようとする場合に、Visual Studio で警告します。

1. Windows Server、お使いのブラウザーでアプリを開くことで、アプリが正しく実行できることを確認します。

    アプリが正常に動作しない場合がありますが一致しない、サーバーと、Visual Studio コンピューターにインストールされている ASP.NET のバージョン間か IIS または Web サイトの構成に問題があります。 前の手順を再確認します。
