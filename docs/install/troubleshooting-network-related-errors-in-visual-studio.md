---
title: "Visual Studio をインストールまたは使用するときのネットワーク関連のエラーのトラブルシューティング | Microsoft Docs"
description: 
ms.custom: 
ms.date: 02/12/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs, Visual Studio
- proxy errors, Visual Studio
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d4d1e330a6ab378c61876b3f869f88b2a29c35a1
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2018
---
# <a name="troubleshooting-network-related-errors-when-you-install-or-use-visual-studio"></a>Visual Studio をインストールまたは使用するときのネットワーク関連のエラーのトラブルシューティング
ファイアウォールまたはプロキシ サーバーの内側で Visual Studio をインストールし使用するときに発生する可能性があるネットワークまたはプロキシに関連する最も代表的なエラーの解決策を紹介します。

## <a name="error-proxy-authorization-required"></a>エラー: "プロキシ認証を要求するエラー"

このエラーは通常、ユーザーがプロキシ サーバーを経由してインターネットに接続し、Visual Studio が一部のネットワーク リソースに対して行った呼び出しをプロキシ サーバーがブロックしたときに発生します。

### <a name="to-fix-this-error"></a>このエラーを修復するには:

- Visual Studio を再起動します。 プロキシ認証のダイアログ ボックスが表示されます。 ダイアログ ボックスに入力を求めるメッセージが表示されたら、資格情報を入力します。

- Visual Studio を再起動しても問題が解決しない場合は、考えられる原因は、プロキシ サーバーが http:&#47;&#47;go.microsoft.com のアドレスに対しては資格情報を要求せず、&#42;.visualStudio.com のアドレスに対しては資格情報を要求することです。 これらのサーバーの場合、次の URL をホワイトリストに設定し、Visual Studio におけるあらゆるサインイン シナリオのブロックを解除することを検討する必要があります。

    - &#42;.windows.net

    - &#42;.microsoftonline.com

    - &#42;.visualstudio.com

    - &#42;.microsoft.com

    - &#42;.live.com

- http:&#47;&#47;go.microsoft.com をホワイトリストから削除すると、Visual Studio を再起動したとき、http:&#47;&#47;go.microsoft.com のアドレスとサーバー エンドポイントの両方にプロキシ認証ダイアログが表示されます。

    OR

- プロキシで既定の資格情報を使用する場合は、次のアクションを実行します。

    1. **devenv.exe.config** (devenv.exe 構成ファイル) を、**%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** または **%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE** で見つけます。

    1. 構成ファイル内で、`<system.net>` ブロックを探し、次のコードを追加します。

        ```xml
        <defaultProxy enabled="true" useDefaultCredentials="true">
            <proxy bypassonlocal="True" proxyaddress=" HYPERLINK "http://<yourproxy:port#" http://<yourproxy:port#>"/>
        </defaultProxy>
        ```

        `proxyaddress="<http://<yourproxy:port#>`には、使用しているネットワークの正しいプロキシ アドレスを挿入する必要があります。

    OR

- 「[How to connect through an authenticated Web Proxy](http://blogs.msdn.com/b/rido/archive/2010/05/06/how-to-connect-to-tfs-through-authenticated-web-proxy.aspx)」 (認証された Web プロキシを通して接続する方法) ブログ投稿に含まれる手順に従うこともできます。プロキシを使用するためのコードを追加する方法が説明されています。

## <a name="error-the-underlying-connection-was-closed"></a>エラー: "接続が切断されました"

ファイアウォールが設定されたプライベート ネットワークで Visual Studio を使用する場合、Visual Studio を一部のネットワーク リソースに接続できない可能性があります。 これらのリソースには、サインインとライセンス取得のための Visual Studio Team Services (VSTS)、NuGet、および Azure サービスが含まれます。 Visual Studio でこれらのリソースのいずれかに接続できない場合は、次のエラー メッセージが表示されることがあります。

  **基になる接続が閉じられました: 送信時に、予期しないエラーが発生しました**

Visual Studio ではトランスポート層セキュリティ (TLS) 1.2 プロトコルを使用して、ネットワーク リソースに接続します。 Visual Studio で TLS 1.2 を使用している場合、一部のプライベート ネットワーク上のセキュリティ アプライアンスによって特定のサーバー接続がブロックされます。

### <a name="to-fix-this-error"></a>このエラーを修復するには:

次の URL の接続を有効にします。

- https:&#47;&#47;management.core.windows.net

- https:&#47;&#47;app.vssps.visualstudio.com

- https:&#47;&#47;login.microsoftonline.com

- https:&#47;&#47;login.live.com

- https:&#47;&#47;go.microsoft.com

- https:&#47;&#47;graph.windows.net

- https:&#47;&#47;app.vsspsext.visualstudio.com

- &#42;.azurewebsites.net (Azure 接続の場合)

- &#42;.visualstudio.com

- cdn.vsassets.io (コンテンツ配信ネットワーク (CDN)、コンテンツをホスト)

- &#42;.gallerycdn.vsassets.io (VSTS 拡張機能をホスト)

- static2.sharepointonline.com (フォントなど、Visual Studio が使用する Office UI ファブリック キットのリソースをホスト)

- &#42;.nuget.org (NuGet 接続の場合)

 > [!NOTE]
 > プライベートで所有されている NuGet のサーバー URL は、このリストには含まれない場合があります。 %APPData%\Nuget\NuGet.Config で使用している NuGet のサーバーを確認できます。


## <a name="get-support"></a>サポートを受ける
Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 インストールに関するトラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目
* [ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールして使用する](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [Visual Studio 2017 のインストール](install-visual-studio.md)
