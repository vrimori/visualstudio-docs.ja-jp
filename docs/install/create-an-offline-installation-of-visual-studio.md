---
title: "Visual Studio のオフライン インストールを作成する | Microsoft Docs"
description: "Visual Studio をオフラインでインストールする方法について説明します。"
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 8b0902c7e2d3c2b51ecd915647a3e8a03e49c641
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Visual Studio 2017 のオフライン インストールを作成する

Visual Studio 2017 インストーラーは、さまざまなネットワーク環境またはさまざまなコンピューター環境で問題なく動作するように設計されています。

- 新しいワークロード ベース モデルでは、旧バージョンの Visual Studio よりダウンロード量が少なくなります (最小インストールではわずか 300 MB で済みます)。
- 汎用の "ISO" または zip ファイルと違い、コンピューターに必要なパッケージしかダウンロードしません。 たとえば、不要な場合には 64 ビット ファイルをダウンロードしません。
- インストール プロセス中、アンチウイルス/プロキシ ソフトウェアによる干渉を最小限に抑えるために、3 つの異なるダウンロード技術 (WebClient、BITS、WinInet) が試されます。
- Visual Studio のインストールに必要なファイルはグローバル配信ネットワークで配信されます。そのため、ローカル サーバーから届けられます。

[Visual Studio Web インストーラー](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)をお試しください&mdash;その利便性を実感していただけるものと考えております。

 > [!div class="button"]
 > [Visual Studio 2017 をダウンロードする](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

インターネット接続が利用できないか、信頼性が低いためにオフラインでインストールする場合、「[低帯域幅または信頼性の低いネットワーク環境に Visual Studio 2017 をインストールする](../install/install-vs-inconsistent-quality-network.md)」をご覧ください。 コマンド ラインを利用してオフライン インストールの完了に必要なファイルのローカル キャッシュを作成できます。 このプロセスは以前のバージョンで利用できた ISO ファイルに置き換わるものです。

> [!NOTE]
> 企業の IT 管理者が、インターネットに対してファイアウォールを施したクライアント ワークステーションのネットワークに Visual Studio 2017 を展開する場合、「[Visual Studio 2017 のネットワーク インストールを作成する](../install/create-a-network-installation-of-visual-studio.md)」と「[Special considerations for installing Visual Studio in an offline environment](../install/install-visual-studio-in-offline-environment.md)」(オフライン環境での Visual Studio のインストールに関する特別な考慮事項) を参照してください。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページにあるトラブルシューティングのヒントをご覧ください。 また、Visual Studio IDE の [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから製品の問題を Microsoft に報告していただくことや、[UserVoice](https://visualstudio.uservoice.com/forums/121579) でご提案を共有していただくこともできます。 [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。 [Gitter コミュニティの Visual Studio に関する意見交換](https://gitter.im/Microsoft/VisualStudio) ([GitHub](https://github.com/) アカウントが必要) から、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。
