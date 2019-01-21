---
title: Visual Studio 2019 for Mac プレビューをインストールする
description: Visual Studio 2019 for Mac プレビューとクロスプラット フォーム開発に必要なその他のコンポーネントをインストールする手順について説明します。
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: acd8f3bc4f5fefa0a0c8b273856579067fb33c6a
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315900"
---
# <a name="install-visual-studio-2019-for-mac-preview"></a>Visual Studio 2019 for Mac プレビューをインストールする

> [!NOTE]
> Visual Studio 2019 for Mac プレビューは、Visual Studio for Mac の最新の安定版リリースとサイド バイ サイドでインストールすることができます。 インストール時に、既存の Visual Studio が最新の安定版ではない場合は更新するように求められます。

## <a name="requirements-for-the-visual-studio-2019-for-mac-preview"></a>Visual Studio 2019 for Mac プレビューの要件

- macOS High Sierra 10.13 以降が搭載された Mac。

iOS または macOS 向けに Xamarin アプリをビルドするには、以下も必要になります。

- Xcode 10.0 以降。 通常は最新の安定バージョンをお勧めします。
- Apple ID。 Apple ID をまだ持っていない場合は、 https://appleid.apple.com で新しい ID を作成できます。 Xcode をインストールしてサインインするには、Apple ID を持っている必要があります。

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

    現在使用している Visual Studio 2017 for Mac がバージョン 7.7 よりも古い場合は、最新の安定バージョン (これはサイド バイ サイド インストールをサポートするために必要) へのアップグレードの承認を求められます。 アップグレードを承認するには、**[続行]** を押します。

    ![安定バージョンを 7.7 にアップグレードする必要があります](media/install-preview-older-upgrade.png)

7. 選択を行ったら、**[インストール]** ボタンを押します。
8. インストーラーではダウンロードの進行状況が表示され、Visual Studio for Mac と選択したワークロードがインストールされます。 インストールに必要な権限を付与するため、パスワードの入力が求められる場合があります。
9. **Visual Studio (プレビュー)** は、プレビュー バージョンをテストしたいときにいつでも使うことができ、運用作業には最新の安定版の Visual Studio に切り替えることができます。 2 つのアイコンが表示されます。

    ![安定版のアイコンとプレビュー版のアイコンの違い](media/install-preview-icons-sml.png)

企業環境でのインストール中にネットワークに問題が発生した場合は、[ファイアウォールまたはプロキシの背後へのインストール](https://docs.microsoft.com/visualstudio/mac/installation#install-visual-studio-for-mac-behind-a-firewall-or-proxy-server)の指示を確認してください。

[リリース ノート](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-preview-relnotes)における変更点について学習します。

> [!NOTE]
> 元のインストールでプラットフォームやツールをインストールしなかった場合 (手順 6 でオフにした場合)、そのコンポーネントを後で追加するには、インストーラーをもう一度実行する必要があります。

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>ファイアウォールまたはプロキシ サーバーの内側に Visual Studio for Mac をインストールする

ファイアウォールの内側に Visual Studio for Mac をインストールするには、ソフトウェアに必要なツールと更新プログラムのダウンロードができるように特定のエンドポイントにアクセスできる必要があります。

以下の場所にアクセスできるようにネットワークを構成します。

- [Visual Studio エンドポイント](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

## <a name="next-steps"></a>次の手順

Visual Studio for Mac をインストールすると、アプリのコードの記述を開始できます。 以下のガイドで、次の手順であるプロジェクトの記述と配置について説明します。

### <a name="ios"></a>iOS

1. [Hello, iOS](https://developer.xamarin.com/guides/ios/getting_started/hello,_iOS/)
2. [デバイス プロビジョニング](https://developer.xamarin.com/guides/ios/getting_started/installation/device_provisioning) (デバイスでアプリケーションを実行する場合)。

### <a name="android"></a>Android

1. [Xamarin Android SDK Manager の使用](https://developer.xamarin.com/guides/android/getting_started/installation/android-sdk/?ide=xs)
2. [Android SDK エミュレーター](https://developer.xamarin.com/guides/android/getting_started/installation/android-emulator/)
4. [開発用のデバイスの設定](https://developer.xamarin.com/guides/android/getting_started/installation/set_up_device_for_development/)

### <a name="net-core-apps-aspnet-core-web-apps-unity-game-development"></a>.NET Core アプリ, ASP.NET Core Web アプリ, Unity ゲーム開発

他のワークロードについては、[ワークロード](/visualstudio/mac/workloads)に関するページをご覧ください。

## <a name="see-also"></a>関連項目

- [Visual Studio 2017 のインストール (Windows)](/visualstudio/install/install-visual-studio)
