---
title: "プライベート ネットワーク内の URL のホワイトリスト登録 | Microsoft Docs"
ms.custom: 
ms.date: 09/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a4093c7ebba74493a64833bfbf83ee6d28ef1ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="whitelisting-urls-in-a-private-network"></a>プライベート ネットワーク内の URL のホワイトリスト登録

ファイアウォールなどのセキュリティ アプライアンスを使用するプライベート ネットワークで Visual Studio を使用する場合、Visual Studio を一部のネットワーク リソースに接続できない可能性があります。 これらのリソースには、サインインとライセンス取得のための Visual Studio Team Services (VSTS)、NuGet、および Azure サービスが含まれます。 Visual Studio でこれらのリソースのいずれかに接続できない場合は、次のエラー メッセージが表示されます。

  **基になる接続が閉じられました: 送信時に、予期しないエラーが発生しました**

Visual Studio ではトランスポート層セキュリティ (TLS) 1.2 プロトコルを使用して、ネットワーク リソースに接続します。 Visual Studio で TLS 1.2 を使用している場合、一部のプライベート ネットワーク上のセキュリティ アプライアンスによって特定のサーバー接続がブロックされます。 エラーを修正するには、次の URL の接続を有効にします。

- https://management.core.windows.net

- https://app.vssps.visualstudio.com

- https://login.microsoftonline.com

- https://login.live.com

- https://go.microsoft.com

- https://graph.windows.net

- https://app.vsspsext.visualstudio.com

- *.azurewebsites.net (Azure 接続の場合)

- *.nuget.org (NuGet 接続の場合)

- *.visualstudio.com

- cdn.vsassets.io (コンテンツ配信ネットワーク (CDN)、コンテンツをホスト)

- *.gallerycdn.vsassets.io (VSTS 拡張機能をホスト)

- static2.sharepointonline.com (フォントなど、Visual Studio が使用する Office ファブリック UI キットのリソースをホスト)

> [!NOTE]
> プライベートで所有されている NuGet のサーバー URL は、上記のリストには含まれない場合があります。 %APPData%\Nuget\NuGet.Config を開いて、使用している NuGet のサーバーを確認できます。

## <a name="see-also"></a>関連項目

[プロキシ認証を要求するエラー](../ide/reference/proxy-authorization-required.md)  
[ファイアウォールまたはプロキシ サーバーの内側に Visual Studio をインストールする](../install/install-visual-studio-behind-a-firewall-or-proxy-server.md)
