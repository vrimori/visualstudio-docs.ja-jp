---
title: "パッケージ キャッシュの無効化または移動 | Microsoft Docs"
description: "Visual Studio 展開のパッケージ キャッシュを無効化、有効化、移動します。"
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 639c6e52f522bbdb2868d610f0b002abb9dda082
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="disable-or-move-the-package-cache"></a>パッケージ キャッシュの無効化または移動

パッケージ キャッシュは、インターネット接続がないときに Visual Studio やその他の関連製品の修復が必要になった場合のために、インストール済みパッケージのソースを提供します。 しかしながら、ドライブやシステムを設定しておくことで、すべてのパッケージを維持する必要がなくなることもあります。
インストーラーは必要なときにパッケージをダウンロードします。そのため、ディスク領域を節約または復元する場合、パッケージ キャッシュを無効化したり、移動したりできます。

## <a name="disable-the-package-cache"></a>パッケージ キャッシュの無効化

新しいインストーラーで Visual Studio やその他の製品をインストール、変更、修復する前に、`--nocache` スイッチでインストーラーを開始できます。

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

あらゆる製品に対して行うあらゆる操作でその製品の既存パッケージがすべて削除されます。インストール後、パッケージは保存されません。 Visual Studio の変更や修復でパッケージが必要になる場合、自動的にダウンロードされ、インストール後に削除されます。

キャッシュを再有効化する場合、代わりに `--cache` を渡します。 必要なパッケージのみがキャッシュされます。そのため、すべてのパッケージを復元する必要がある場合、ネットワークの接続を切断する前に Visual Studio を修復する必要があります。

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

また、Visual Studio をインストール、変更、修復する前にキャッシュを無効化するように `KeepDownloadedPayloads` [レジストリ ポリシー](set-defaults-for-enterprise-deployments.md)を設定できます。

## <a name="move-the-package-cache"></a>パッケージ キャッシュの移動

共通のシステム構成は、SSD に Windows をインストールし、ソース コードやプログラム バイナリなど、開発用には大きなハード ディスク (またはハード ディスクより大容量のストレージ) を利用することです。 オフラインで作業する場合、代わりにパッケージ キャッシュを移動できます。

現在のところ、Visual Studio をインストール、変更、修復する前に `CachePath` [レジストリ ポリシー](set-defaults-for-enterprise-deployments.md)を設定する場合にのみこれが可能です。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

 * [Visual Studio のインストール](install-visual-studio.md)
 * [エンタープライズ展開に既定値を設定する](set-defaults-for-enterprise-deployments.md)
 * [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
