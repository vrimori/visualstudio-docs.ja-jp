---
title: Python での Azure リモート デバッグのトラブルシューティング
description: Visual Studio を使って Azure App Service で実行している Python アプリケーションをデバッグしようとするときの問題をトラブルシューティングする方法を説明します。
ms.date: 06/26/2018
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
ms.openlocfilehash: f545fa223aa929b79016352e799d112bceddaf1c
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341464"
---
# <a name="remote-debugging-troubleshooter-for-python-and-azure"></a>Python と Azure のリモート デバッグのトラブルシューティング

Visual Studio は、次のいずれかの理由で [リモート デバッグのための Azure App Service](debugging-remote-python-code-on-azure.md) へのアタッチに失敗します。

| 理由 | 解像度 |
| --- | --- |
| Visual Studio 2013 Update 4 以降がインストールされていません。 | 適切なバージョンを [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) からインストールします。 |
| App Service に配置されているプロジェクトが Visual Studio で開いているプロジェクトと一致しません。 | 正しいプロジェクトを Visual Studio に読み込みます。 |
| プロジェクトが **[デバッグ]** 構成で配置されていません。 | **ソリューション エクスプローラー**でプロジェクトを右クリックして **[発行]** を選択し、アプリケーションを再配置します。 **[設定]** タブで、**[デバッグ]** 構成が選択されていることを確認します。 |
| App Service が実行されていません。 | Visual Studio の**サーバー エクスプローラー**か Azure Portal から App Service を起動します。 |
| App Service が Web ソケットを使用するように構成されていません。 | [Azure Portal](https://portal.azure.com) を開いて該当の App Service に移動し、**[設定]** > **[アプリケーションの設定]** を開きます。**[全般設定]** > **[Web ソケット]** を **[オン]** にして、**[保存]** を選択します。 (このブレードに表示される **[デバッグ]** のオプションは、Python デバッグには*適用されません*。) |
| *web.debug.config* がデバッグ プロキシを無効にするように変更されています。 | このファイルを削除して、プロジェクトを App Service に再発行します。その間に Visual Studio によってファイルが再作成されます。 |

参照:

- [Python の Azure リモート デバッグ](debugging-remote-python-code-on-azure.md)
