---
title: Python での Azure リモート デバッグのトラブルシューティング
description: Visual Studio を使って Azure App Service で実行している Python アプリケーションをデバッグしようとするときの問題をトラブルシューティングする方法を説明します。
ms.date: 07/12/2017
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3d792a411867686abe0734fc67dfe654320d8b38
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Python と Azure のリモート デバッグのトラブルシューティング

Visual Studio は、次のいずれかの理由で [リモート デバッグのための Azure App Service](debugging-remote-python-code-on-azure.md) へのアタッチに失敗します。

| 理由 | 解像度 |
| --- | --- |
| Visual Studio 2013 Update 4 以降がインストールされていません。 | 適切なバージョンを [visualstudio.com](https://www.visualstudio.com/downloads/) からインストールします。 | 
| App Service に配置されているプロジェクトが Visual Studio で開いているプロジェクトと一致しません。 | 正しいプロジェクトを Visual Studio に読み込みます。 |
| プロジェクトが [デバッグ] 構成で配置されていません。 | ソリューション エクスプローラーでプロジェクトを右クリックして **[発行]** を選択し、アプリケーションを再配置します。 **[設定]** タブで、**[デバッグ]** 構成が選択されていることを確認します。 |
| App Service が実行されていません。 | Visual Studio のサーバー エクスプローラーか Azure Portal から App Service を起動します。 |
| App Service が Web ソケットを使用するように構成されていません。 | [Azure Portal](https://portal.azure.com) を開いて該当の App Service に移動し、**[設定] > [アプリケーションの設定]** ブレードを開きます。**[全般設定] > [Web ソケット]** を **[オン]** にして、**[保存]** を選択します。 (このブレードに表示される **[デバッグ]** のオプションは、Python デバッグには*適用されません*。) |
| `web.debug.config` がデバッグ プロキシを無効にするように変更されています。 | このファイルを削除して、プロジェクトを App Service に再発行します。その間に Visual Studio によってファイルが再作成されます。 |

参照:

- [Python の Azure リモート デバッグ](debugging-remote-python-code-on-azure.md)
