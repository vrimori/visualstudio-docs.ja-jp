---
title: Visual Studio for Mac をインストールする
description: Visual Studio for Mac とクロスプラット フォーム開発に必要なその他のコンポーネントをインストールする手順について説明します。
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 22B1F2CD-32AE-464D-80AC-C8AB4786B015
ms.openlocfilehash: 5ad3154390494c3d949ceba1cc84ded87d33a3fd
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294995"
---
# <a name="set-up-and-install-visual-studio-for-mac"></a>Visual Studio for Mac の設定とインストール

## <a name="setup"></a>セットアップ

ネイティブのクロスプラットフォーム アプリの開発を始めるには、Visual Studio for Mac をダウンロードするときに、インストールして準備時にセットアップする必要があるものがいくつかあります。

Visual Studio で iOS を使用するには、以下が必要です。

* macOS Sierra 10.12 以降が搭載された Mac
* Xcode 8.3 以降。 通常は最新の安定バージョンをお勧めします。
* Apple ID。 Apple ID をまだ持っていない場合は、 https://appleid.apple.com で新しい ID を作成できます。 Xcode をインストールしてサインインするには、Apple ID を持っている必要があります。

## <a name="install"></a>インストール

1. [https://visualstudio.microsoft.com/](https://visualstudio.microsoft.com/) から Visual Studio for Mac をダウンロードします

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

   すべてのプラットフォームをインストールすることを希望されない場合には、以下のガイドを使用してインストールするプラットフォームを決めることがきます。

   * **Xamarin を使用するアプリ**:
      - Xamarin.Forms – **Android** と **iOS** プラットフォームを選択します。
      - iOS のみ – **iOS** プラットフォームを選択します ([ **Xcode**](https://developer.apple.com/xcode/) をインストールする必要があります)。
      - Android のみ – **Android** プラットフォームを選択します (関連する依存関係も選択する必要があります)。
      - Mac のみ – **macOS** プラットフォームを選択します ([ **Xcode**](https://developer.apple.com/xcode/) をインストールする必要があります)。
      - 完全なクロスプラットフォームの Xamarin アプリ – **Android**、**iOS**、および**macOS** プラットフォームを選択します。
   * **.NET Core アプリケーション** – **.NET Core** プラットフォームを選択します。
   * **ASP.NET Core Web アプリケーション** – **.NET Core** プラットフォームを選択します。
   * **クロスプラットフォームの Unity ゲーム開発** – Visual Studio for Mac 以外の追加のプラットフォームをインストールする必要はありません。 Unity 拡張機能のインストールの詳細については、[Unity セットアップ ガイド](setup-vsmac-tools-unity.md)に関するページをご覧ください。

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
> 元のインストールでプラットフォームやツールをインストールしなかった場合 (手順 6 でオフにした場合)、そのコンポーネントを後で追加するには、[インストーラー](https://visualstudio.microsoft.com/vs/)をもう一度実行する必要があります。

## <a name="install-visual-studio-for-mac-behind-a-firewall-or-proxy-server"></a>ファイアウォールまたはプロキシ サーバーの内側に Visual Studio for Mac をインストールする

ファイアウォールの内側に Visual Studio for Mac をインストールするには、ソフトウェアに必要なツールと更新プログラムのダウンロードができるように特定のエンドポイントにアクセスできる必要があります。

以下の場所にアクセスできるようにネットワークを構成します。

* [Visual Studio エンドポイント](/visualstudio/install/install-visual-studio-behind-a-firewall-or-proxy-server)

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

他のワークロードについては、[ワークロード](workloads.md)に関するページをご覧ください。

## <a name="see-also"></a>関連項目

- [Visual Studio 2017 のインストール (Windows)](/visualstudio/install/install-visual-studio)