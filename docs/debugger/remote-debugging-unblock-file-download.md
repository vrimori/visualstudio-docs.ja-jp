---
title: リモート ツールのダウンロードをブロック解除します。
ms.custom: ''
ms.date: 07/19/2018
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- remote debugging, unblock download
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0586b8f0699ec2eca5843d59df1b6ddd7cecbd3
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180661"
---
# <a name="how-to-unblock-the-download-of-the-remote-tools-on-windows-server"></a>方法: Windows Server のリモート ツールのダウンロードをブロック解除

Windows Server 上の Internet Explorer で、既定のセキュリティ設定により、リモート ツールなどのコンポーネントをダウンロードする時間がかかる。

* Web サイトを開くと、リソースを含むドメインが明示的に許可しない限り、web リソースへのアクセスが阻止される Internet explorer セキュリティ強化の構成が有効になっている (つまり、信頼されている)。 この設定を無効にすることができます、私たちは勧めしませんセキュリティ リスクを表すことができるため。

* 既定の設定、Windows Server 2016 で**インターネット オプション** > **セキュリティ** > **インターネット** >  **カスタム レベル** > **ダウンロード**ファイルのダウンロードも無効にします。 Windows サーバー上で直接リモート ツールをダウンロードする場合は、ファイルのダウンロードを有効にする必要があります。

Windows Server 上のツールをダウンロードするには、次のいずれかを勧め。

* 1 つ実行中の Visual Studio などの別のコンピューターにリモート ツールをダウンロードし、コピー、 *.exe*ファイルを Windows サーバーにします。

* リモート デバッガーを実行する[ファイル共有から](../debugger/remote-debugging.md#fileshare_msvsmon)Visual Studio コンピューターにします。

* Windows サーバー上で直接リモート ツールをダウンロードし、信頼済みサイトを追加するプロンプトに同意します。 多くの場合、最新の web サイトには、これにより、膨大な数のため、多くのサードパーティのリソースが含まれます。 さらに、リダイレクトされたリンクは、手動で追加する必要があります。 ダウンロードを開始する前に、信頼済みサイトの一部を追加することができます。 移動して**インターネット オプション > セキュリティ > 信頼済みサイト > サイト**し、次のサイトを追加します。

  * visualstudio.microsoft.com
  * download.visualstudio.microsoft.com
  * 方法: 空

  My.visualstudio.com にデバッガーの古いバージョンは、これらの追加サイトをそのログインが成功したかどうかを確認を追加します。

  * microsoft.com
  * go.microsoft.com
  * download.microsoft.com
  * my.visualstudio.com
  * login.microsoftonline.com
  * login.live.com
  * secure.aadcdn.microsoftonline されました。
  * msft.sts.microsoft.com
  * auth.gfx.ms
  * app.vssps.visualstudio.com
  * vlscppe.microsoft.com
  * query.prod.cms.rt.microsoft.com

    選択して、リモート ツールのダウンロード中にこれらのドメインを追加する場合は**追加**入力を求められたらします。

    ![ブロックされたコンテンツ ダイアログ ボックス](../debugger/media/remotedbg-blocked-content.png)

    ソフトウェアをダウンロードすると、さまざまな web サイトのスクリプトおよびリソースを読み込むためのアクセス許可を与えるいくつか追加の要求が表示されます。 My.visualstudio.com でそのログインが成功したかどうかを確認する追加のドメインを追加することをお勧めします。