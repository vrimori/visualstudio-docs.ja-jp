---
title: "Visual Studio for Mac をインストールする | Microsoft Docs"
description: "Visual Studio for Mac とクロスプラット フォーム開発に必要なその他のコンポーネントをインストールする手順について説明します。"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 7f91a28449ffad135058438ec767095818cc8527
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="setup-and-install-visual-studio-for-mac"></a>Visual Studio for Mac のセットアップとインストール

## <a name="setup"></a>セットアップ

ネイティブのクロスプラットフォーム アプリの開発を始めるには、Visual Studio for Mac をダウンロードするときに、インストールして準備時にセットアップする必要があるものがいくつかあります。

Visual Studio で iOS を使用するには、以下が必要です。

* macOS Sierra 10.12 以降が搭載された Mac
* Xcode 8.3 以降。 通常は最新の安定バージョンをお勧めします。
* Apple ID。 Apple ID をまだ持っていない場合は、https://appleid.apple.com で新しい ID を作成できます。Xcode をインストールしてサインインするには、Apple ID を持っている必要があります。

## <a name="install"></a>インストール

1. Visual Studio for Mac を [https://www.visualstudio.com/](https://www.visualstudio.com/) からダウンロードします

2. インストーラー パッケージをダウンロードしたら、**VisualStudioInstaller.dmg** ファイルをクリックしてインストーラーをマウントし、次の図のようにロゴをダブルクリックして実行します。

  ![インストーラー ダイアログ](media/installer-image1.png)

3. 次の図のようなアラート ダイアログが表示されることがあります。 この場合は、**[開く]** をクリックします。

  ![アラート ダイアログ](media/installer-image2.png)

4. インストールまたは更新が必要なコンポーネントを検証するために、インストーラーによってシステムが検査されます。

  ![システムの評価](media/installer-image3.png)

5. プライバシーとライセンスの条項に同意することを求めるアラート ダイアログが表示されます。 条項に同意する場合は **[続行]** ボタンを押します。

  ![ライセンスのダイアログ](media/installer-image4.png)

6. インストーラーにより、必須コンポーネントのうち不足していて、ダウンロードおよびインストールが必要なコンポーネントの一覧が表示されます。 ここでダウンロードする製品を選択します。

  ![項目の選択](media/installer-image5.png)

  このインストール画面には、各コンポーネントのサイズとバージョンが表示されます。 各コンポーネントをクリックすると、そのコンポーネントの依存ファイルの一覧 (Android の場合)、ダウンロードする追加パッケージ (.NET Core の場合)、必要な追加アプリケーション (iOS と macOS の場合) が表示されます。

  ![Android の追加の依存ファイル](media/installer-image6.png)

7. 選択を完了したら、**[インストールと更新]** ボタンを選択してインストール プロセスを開始します。

8. 選択した項目のダウンロードおよびインストール処理が始まります。

  ![インストールの開始](media/installer-image7.png)

  ![Xamarin.Mac のダウンロード](media/installer-image8.png)

  ![インストールの完了](media/installer-image9.png)

9. 各コンポーネントで、インストールを完了するために必要なアクセス許可を昇格するように求められることがあります。 インストール処理を続行するには、管理者の資格情報をここに入力します。

  ![アクセス許可を入力してインストーラーの処理を続行する](media/installer-image10.png)

10. インストールが成功したら、**[スタート]** を押して Visual Studio でアプリ開発を始めることができます。

  ![Visual Studio を開く](media/installer-image11.png)

> [!NOTE]
元のインストールでプラットフォームやツールをインストールしなかった場合 (手順 6 でオフにした場合)、そのコンポーネントを後で追加するには、[インストーラー](https://www.visualstudio.com/vs/)をもう一度実行する必要があります。

## <a name="manual-installation"></a>手動インストール

インストールが失敗したか、インストールのいずれかのコンポーネントでエラーが発生している場合は、手動インストールで問題を解決できる場合があります。 必要なコンポーネントを確認してそれぞれをダウンロードするには、以下の手順を実行します。

1. Visual Studio インストーラーの 2 番目の画面で、メニュー バーに移動して **[View Manual Installation Instructions]\(手動インストールの手順の表示\)** を選択します。

    ![手動インストールのメニュー項目を示しているオプション](media/installer-image12.png)

2. 手順に従って、コンポーネントを手動でダウンロードしてインストールしてください。

  ![手動インストールのダイアログ](media/installer-image13.png)

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>ファイアウォールまたはプロキシ サーバーの内側に Visual Studio for Mac をインストールする

ファイアウォールの内側に Visual Studio for Mac をインストールするには、ソフトウェアに必要なツールと更新プログラムのダウンロードができるように特定のエンドポイントにアクセスできる必要があります。

以下の場所にアクセスできるようにネットワークを構成します。

* [Visual Studio エンドポイント](https://docs.microsoft.com/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)