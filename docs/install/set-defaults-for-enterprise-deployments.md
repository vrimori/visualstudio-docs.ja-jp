---
title: Visual Studio のエンタープライズ展開に既定値を設定する
description: Visual Studio のエンタープライズ展開で使用するドメイン ポリシーとその他の構成操作について説明します。
ms.date: 05/05/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f229ea889a478281ee0db123da00cd67c82ec13a
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Visual Studio のエンタープライズ展開に既定値を設定する

Visual Studio の展開に影響するレジストリ ポリシーを設定することができます。 これらのポリシーは新しいインストーラーに対してグローバルであり、次に対する影響があります。

- 他のバージョンまたはインスタンスと共有されているパッケージがいくつかインストールされている場合
- パッケージがキャッシュされている場合
- すべてのパッケージがキャッシュされている場合

これらのポリシーのいくつかを[コマンド ライン オプション](use-command-line-parameters-to-install-visual-studio.md)を使用して設定してコンピューターのレジストリ値を設定できるだけでなく、グループ ポリシーを使用して組織全体にこれらを配布することもできます。

## <a name="registry-keys"></a>レジストリ キー

一部の場所ではエンタープライズの既定を設定して、グループ ポリシーを使用するかレジストリから直接、管理を有効にすることができます。 Visual Studio は順番にエンタープライズ ポリシーが設定されているかを確認し、以下の順番でポリシー値が検出された時点で、残りのキーは無視されます。

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (64 ビット オペレーティング システム)

> [!IMPORTANT]
> `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` キーを設定せず、代わりの他のキーのいずれかを設定する場合は、他の両方のキーを 64 ビット オペレーティング システムに設定する必要があります。 この問題は、製品の将来の更新プログラムで対処されます。

いくつかのレジストリ値は、未設定の場合、最初に使われたときに自動的に設定されます。 これにより、以後のインストールでも同じ値が使われるようになります。 これらの値は、2 番目のレジストリ キーである `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` に格納されます。

以下のレジストリ値を設定できます。

| **Name** | **Type** | **既定値** | **説明** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` または `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | パッケージ マニフェストと、ペイロード (省略可能) が格納されるディレクトリ。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | パッケージのペイロードはインストール後も保持されます。 この値はいつでも変更できます。 ポリシーを無効にすると、修復または変更するインスタンスでキャッシュされたパッケージのペイロードがすべて削除されます。 詳細については、「[disable or move the package cache](disable-or-move-the-package-cache.md)」 (パッケージ キャッシュの無効化または移動) を参照してください。 |
| `SharedInstallationPath` | `REG_SZ` または `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Visual Studio の異なるバージョンのインスタンスで共有されているパッケージがいくつかインストールされているディレクトリ。 この値はいつでも変更できますが、変更が反映されるのは以後のインストールのみです。 元の場所に既にインストールされている製品は移動しないでください。移動すると、正しく機能しない場合があります。 |

> [!IMPORTANT]
> インストール後に `CachePath` のレジストリ ポリシーを変更する場合は、既存のパッケージ キャッシュを新しい場所に移動して、`SYSTEM` および `Administrators` にフル コントロールが、`Everyone` に読み取りアクセスが可能になるようにセキュリティを保護する必要があります。
> 既存のキャッシュの移動やセキュリティの保護に失敗すると、今後のインストールで問題が発生する場合があります。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

 * [Visual Studio のインストール](install-visual-studio.md)
 * [パッケージ キャッシュの無効化または移動](disable-or-move-the-package-cache.md)
 * [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
