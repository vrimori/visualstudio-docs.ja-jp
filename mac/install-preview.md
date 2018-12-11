---
title: プレビュー リリースをインストールする
description: Visual Studio for Mac の更新およびプレビュー リリース (Visual Studio 2019 for Mac プレビューを含む) へのアクセスについて説明します。
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 0E1EF257-9DE4-4653-9DF4-805CE007A1A1
ms.openlocfilehash: b5eea8c2c894b7eeaa13c83ae6698d1297de9297
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2018
ms.locfileid: "52896758"
---
# <a name="install-a-preview-release"></a>プレビュー リリースをインストールする

::: zone pivot="vsmac2019"

> [!TIP]
> Visual Studio 2019 for Mac プレビューが利用できるようになりました。 初めての場合は、Visual Studio for Mac の最新の安定版リリースとサイド バイ サイドでインストールすることができます。

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Visual Studio 2019 for Mac プレビューの要件

* macOS High Sierra 10.13 以降が搭載された Mac。

iOS または macOS 向けに Xamarin アプリをビルドするには、以下も必要になります。

* Xcode 10.0 以降。 通常は最新の安定バージョンをお勧めします。
* Apple ID。 Apple ID をまだ持っていない場合は、 https://appleid.apple.com で新しい ID を作成できます。 Xcode をインストールしてサインインするには、Apple ID を持っている必要があります。

## <a name="installing-the-preview"></a>プレビューのインストール

1. [Visual Studio for Mac のプレビュー ページ](https://aka.ms/vs4mac-preview)から、プレビュー インストーラーをダウンロードします。
2. ダウンロードが完了したら、**[VisualStudioforMacPreviewInstaller.dmg]** をクリックしてインストーラーをマウントし、矢印のロゴをダブルクリックして実行します。

    [![大きい矢印をクリックしてインストールを開始する](media/install-preview-installer-sml.png)](media/install-preview-installer.png#lightbox)

3. インターネットから、ダウンロードしているアプリケーションに関する警告が表示される場合があります。 **[開く]** をクリックします。
4. インストーラーがシステムを確認するまで待ちます。

    [![インストーラーがシステムにインストールされているコンポーネントを確認する](media/install-preview-checking-sml.png)](media/install-preview-checking.png#lightbox)

5. プライバシーとライセンス条項を確認するように求める警告が表示されます。 リンクに従ってそれらを読んでから、同意する場合は **[続行]** を押します。

    [![プライバシーと条項へのリンクに従って、同意する場合は続行する](media/install-preview-privacy-sml.png)](media/install-preview-privacy.png#lightbox)

6. 使用可能なワークロードの一覧が表示されます。 使用するワークロードを選択します。

    [![インストールしたいオプションのワークロード機能を選択する](media/install-preview-selection-sml.png)](media/install-preview-selection.png#lightbox)

    現在使用している Visual Studio for Mac 2017 がバージョン 7.7 よりも古い場合は、最新の安定バージョン (これはサイド バイ サイド インストールをサポートするために必要) へのアップグレードの承認を求められます。 アップグレードを承認するには、**[続行]** を押します。

    ![安定バージョンを 7.7 にアップグレードする必要があります](media/install-preview-older-upgrade.png)

7. 選択を行ったら、**[インストール]** ボタンを押します。
8. インストーラーではダウンロードの進行状況が表示され、Visual Studio for Mac と選択したワークロードがインストールされます。 インストールに必要な権限を付与するため、パスワードの入力が求められる場合があります。
9. **Visual Studio (プレビュー)** は、プレビュー バージョンをテストしたいときにいつでも使うことができ、運用作業には最新の安定版の Visual Studio に切り替えることができます。 2 つのアイコンが表示されます。

    ![安定版のアイコンとプレビュー版のアイコンの違い](media/install-preview-icons-sml.png)

企業環境でのインストール中にネットワークに問題が発生した場合は、[ファイアウォールまたはプロキシの背後へのインストール](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)の指示を確認してください。

[リリース ノート](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes)における変更点について学習します。

::: zone-end
::: zone pivot="vsmac2017"

## <a name="install-an-update-for-visual-studio-2017-for-mac"></a>Visual Studio 2017 for Mac の更新プログラムをインストールする

Visual Studio for Mac の新しいバージョンは、正式にリリースされる前に、プレビューとしてリリースされます。 プレビュー リリースでは、製品に完全に組み込まれる前の新機能を試し、最新の修正プログラムを受け取ることができます。

Visual Studio for Mac のプレビュー リリースは、個別のダウンロードではなく、更新プログラムとして配布されます。 [更新](update.md)に関する記事で説明されているように、Visual Studio for Mac には Stable、Beta、Alpha の 3 つの更新チャネルがあります。

ほとんどのプレビュー リリースは **Beta** と **Alpha** の両方のチャネルで使用できますが、[プレビューのリリース ノート](/visualstudio/releasenotes/vs2017-mac-preview-relnotes)で常に最新の正確な情報を確認してください。

Visual Studio for Mac のプレビューをインストールするには、次の手順を使用します。

1. **[Visual Studio] > [更新の確認]** に移動します。
2. [更新チャネル] コンボ ボックスで、**[ベータ]** を選びます。
3. **[Switch channel]\(チャネルの切り替え\)** ボタンを選んで選択したチャネルに切り替え、新しい更新プログラムのダウンロードを開始します。
4. **[再起動して更新プログラムをインストールする]** ボタンを選んで、更新プログラムのインストールを始めます。

Visual Studio for Mac の更新について詳しくは、[更新](update.md)に関するページをご覧ください。

::: zone-end