---
title: "Visual Studio で Python を使用した Azure リモート デバッグ | Microsoft Docs"
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68fdc53-65a1-423c-8964-9815dbb3387e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: a4ddd2d52aa1a1e4437c0d1f7821761700c2a91e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/18/2017

---

# <a name="remotely-debugging-python-code-on-azure"></a>Azure 上の Python コードのリモート デバッグ

[Visual Studio での Python サポート](installation.md)には、Azure App Service 上で実行されている Python コードをリモートでデバッグする機能が含まれています。 単純なリモート デバッグとは異なり、このシナリオの対象コンピューターには TCP 経由で直接アクセスできません。そのため Visual Studio は、HTTP 経由でデバッガー プロトコルを公開するプロキシを提供します。 Web テンプレートを使用して作成したプロジェクトでは、生成される `web.debug.config` ファイル内にこのプロキシが自動的に構成されます。 リモート デバッグは、「[Azure App Service への発行](template-web.md#publishing-to-azure-app-service)」で説明している方法でプロジェクトのデバッグ構成を発行した場合にも有効になります。

Azure リモート デバッグは Web ソケットを使用するため、[Azure Portal](https://portal.azure.com) で App Service に対してソケットを有効にする必要があります。これを行うには、**[設定] > [アプリケーションの設定]** に移動し、**[全般設定] > [Web ソケット]**  を **[オン]** にしてから **[保存]** を選択して変更を適用します。 (**[デバッグ]** の設定は、Python のデバッグには適用されません。)

![Azure Portal での Web ソケットの有効化](media/azure-remote-debugging-enable-web-sockets.png)

プロジェクトが正しく配置され、Web ソケットが有効化されたら、Visual Studio の**サーバー エクスプローラー** (**[表示] > [サーバー エクスプローラー]**) から App Service にアタッチできます。 **[Azure] > [App Service]** の該当するリソース グループでサイトを見つけて右クリックし、**[Attach Debugger (Python) (デバッガーのアタッチ (Python))]** を選択します。 (**[デバッガーのアタッチ]** コマンドは IIS 下で実行されている .NET アプリケーション用であり、.NET コードと Python アプリのホストが同じである場合にのみ役立ちます)。

下の「[サーバー エクスプローラーを使用しないアタッチ](#attaching-without-server-explorer)」で説明するように、直接アタッチするための一連の手順が Visual Studio で示されます。 **[Attach Debugger (Python) (デバッガーのアタッチ (Python))]** コマンドが表示されない場合や Visual Studio をサイトにアタッチできない場合は、「[Azure リモート デバッグのトラブルシューティング](debugging-azure-remote-troubleshooting.md)」をご覧ください。

アタッチが成功すると、Visual Studio はデバッガー ビューに切り替わります。 ツールバーには、`wss://` URI などのプロセスのデバッグ状況が表示されます。

![Azure App Service Web サイトのデバッグ](media/azure-remote-debugging-attached.png)

アタッチ後のデバッグ作業は通常のリモート デバッグとほぼ同じですが、いくつかの制約があります。 特に、受信要求を処理して FastCGI 経由で Python コードに委任する IIS Web サーバーには、要求の処理のタイムアウトがあります。これは既定では 90 秒です。 要求の処理にタイムアウトよりも長い時間がかかった場合 (たとえば、プロセスがブレークポイントで一時停止している場合など) は、IIS がプロセスを終了し、デバッグ セッションも終了します。 

## <a name="attaching-without-server-explorer"></a>サーバー エクスプ ローラーを使用しないアタッチ

デバッガーを直接 App Service にアタッチするには、Visual Studio がサイトの `<site_url>/ptvsd` (例: `ptvsdemo.azurewebsites.net/ptvsd`) に配置する WebSocket プロキシの情報ページに記載された手順に従ってください。 このページにアクセスすると、プロキシが正しく構成されていることも確認できます。

![Azure リモート デバッグ プロキシの情報ページ](media/azure-remote-debugging-proxy-info-page.png)

説明に従って、プロジェクトが発行されるたびに再生成される `web.debug.config` ファイル内のシークレットを使用して、URL を作成します。 このファイルは既定ではソリューション エクスプローラーで表示されず、プロジェクトにも含まれないため、すべてのファイルを表示するか、別のエディターでこのファイルを開きます。 ファイルを開いたら、appSetting の `WSGI_PTVSD_SECRET` という名前の値を確認します。

![Azure App Service 内のデバッガー エンドポイントの特定](media/azure-remote-debugging-secret.png)

URL は `wss://<secret>@<site_name>.azurewebsites.net/ptvsd` の形式にする必要があります。そこで、文字列内の &lt;secret&gt; と &lt;site_name&gt; を実際の値で置き換えます。

デバッガーをアタッチするには、**[デバッグ] > [プロセスにアタッチ]** を選択します。**[トランスポート]** ドロップダウンで **[Python remote debugging (Python リモート デバッグ)]** を選択し、**[修飾子]** テキスト ボックスに URL を入力して、Enter キーを押します。 Visual Studio が App Service への接続に成功すると、一覧に 1 つの Python プロセスが表示されます。 このプロセスを選択し、**[アタッチ]** を選択してデバッグを開始します。

![[プロセスにアタッチ] ダイアログを使用した Azure Web サイトへの接続](media/azure-remote-debugging-manual-attach.png)

