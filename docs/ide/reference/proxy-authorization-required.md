---
title: "プロキシ認証を要求するエラーの修正 | Microsoft Docs"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2d24ae1-9902-460e-b72a-0299eed9ee82
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e33e0e2896ccb3a5f7fe6d6da57f509af30d77fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="proxy-authorization-required"></a>プロキシ認証が要求される

このエラーは通常、ユーザーがプロキシ サーバーを経由してインターネットに接続し、Visual Studio が一部のネットワーク リソースに対して行った呼び出しをプロキシ サーバーがブロックしたときに発生します。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- Visual Studio を再起動します。 プロキシ認証のダイアログ ボックスが表示されます。 ダイアログ ボックスに資格情報を入力します。

- 上記の手順で問題が解決しない場合、考えられる原因は、プロキシ サーバーが http://go.microsoft.com のアドレスに対しては資格情報を要求せず、*.visualStudio.com のアドレスに対しては資格情報を要求することです。 これらのサーバーの場合、次の URL のリストをホワイトリストに設定し、Visual Studio におけるあらゆるサインイン シナリオのブロックを解除する必要があります。

    - *.windows.net

    - *.microsoftonline.com

    - *.visualstudio.com

    - *.microsoftonline.com

    - *.live.com

- http://go.microsoft.com をホワイトリストから削除すると、Visual Studio を再起動したとき、http://go.microsoft.com アドレスとサーバー エンドポイントの両方にプロキシ認証ダイアログが表示されます。

    OR

- プロキシで既定の資格情報を使用する場合は、次の手順を実行します。

    1. **devenv.exe.config** (devenv.exe 構成ファイル) を、**%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** または **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** で見つけます。

    1. 構成ファイル内で、 `<system.net>` ブロックを探し、次のコードを追加します。

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        `proxyaddress="<http://<yourproxy:port#>`には、使用しているネットワークの正しいプロキシ アドレスを挿入する必要があります。

    OR

- [このポスト](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx) の指示に従ってプロキシの使用を許可するコードを追加することもできます。
