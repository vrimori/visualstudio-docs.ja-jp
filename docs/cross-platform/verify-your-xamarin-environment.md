---
title: Xamarin 環境を検証する | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: fd39882e-06d1-4b39-80d2-4d07b6e4f8f5
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: 9ae697825d0d4a2c380c6f0d540153fbf06d4da4
ms.sourcegitcommit: d7209d61e812b34d06c2aa267bdf50fbc714d0e0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "42627120"
---
# <a name="verify-your-xamarin-environment"></a>Xamarin 環境を検証する

インストーラーが完了したら ( [Setup and install](../cross-platform/setup-and-install.md)を参照)、数分をかけて、Xamarin 開発を実行するための準備ができているかどうかを確認します。

 インストールの確認が終わったら、次のチュートリアルの一方または両方を試します。

-   「[Visual Studio での Xamarin Froms を使用したアプリ作成の基本事項](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md)」では、Xamarin.Forms アプリケーションをビルドします。

-   「[Visual Studio で Xamarin を使用してネイティブ UI を備えたアプリを作成する](../cross-platform/build-apps-with-native-ui-using-xamarin-in-visual-studio.md)」では、各プラットフォームのネイティブ ユーザー インターフェイスを使用しますが、.NET Standard ライブラリの一部のコードを共有します。

## <a name="all-platforms"></a>すべてのプラットフォーム

Visual Studio で、まず、**[ツール]** > **[拡張機能と更新プログラム]** の順に選択し、いずれかの Xamarin コンポーネントに更新が必要であるかどうかを確認します。

次に、**[ファイル]** > **[新しいプロジェクト]** の順に選択し、Visual Studio で新しい Xamarin.Forms ソリューションを作成します。 ダイアログで、**[Visual C#]** > **[クロスプラットフォーム]** の順に展開し、**[モバイル アプリ (Xamarin.Forms)]** を選択し、**[OK]** をクリックします。 ダイアログが表示されたら **[空のアプリ]** を選択します。 **[コード共有方法]** で **[.NET Standard]** を選択します。 **[OK]** をクリックします。

以上の操作で、4 つのプロジェクトが含まれるソリューションが作成されます。4 つのプロジェクトとは、共有 .NET Standard 2.0 ライブラリ プロジェクトと、Android、iOS、ユニバーサル Windows プラットフォーム (UWP) のそれぞれに合わせて作られたアプリケーション プロジェクトです。

![空のアプリ Xamarin.Forms テンプレートから新しいプロジェクトを作成した結果](../cross-platform/media/crossplat-xamarin-verify-1.png "CrossPlat Xamarin Verify 1")

## <a name="android"></a>Android

1. **[ツール]、[Android]、[Android SDK マネージャー]** の順に進み、最新の Android SDK ツールがインストールされていることを確認してください。 Android SDK Tools、Android SDK Platform ツール、Android SDK Build ツールの最新版をインストールします。 常に最新レベルの Android API をインストールする必要はありません。 必要な API レベルは、対象となるプラットフォーム レベルによって異なります。 通常、Xamarin プラットフォームをインストールすると、必要なレベルの Android プラットフォームがインストールされます。

2.  デバイスまたはエミュレーターでビルドとデバッグを検証します。

    -   ソリューション エクスプローラーで Android プロジェクトを右クリックして **[スタートアップ プロジェクトに設定]** をクリックします。

    -   ツール バーには、利用できる Android デバイスとエミュレーターの一覧が含まれるドロップダウンが表示されるはずです。

    Android デバイスの [設定] ページの [開発者] オプションで、USB デバッグを有効にする必要があります。 有効にすると、デバイスとコンピューターを USB ケーブルで接続できます。

    エミュレーターも一覧表示されます。 いずれかのデバイスまたは Visual Studio エミュレーターを選択します。

  ![デバッグ ターゲットとして Visual Studio Emulator for Android を選択する](../cross-platform/media/crossplat-xamarin-verify-3.png "CrossPlat Xamarin Verify 3")

  詳細については、Microsoft DevOps ブログの「[Introducing Visual Studio's Emulator for Android](https://blogs.msdn.microsoft.com/devops/2014/11/12/introducing-visual-studios-emulator-for-android/)」 (Visual Studio の Emulator for Android の概要) をご覧ください。 エミュレーターを機能させるときに問題が発生する場合は、「[Visual Studio Emulator for Android のトラブルシューティング](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)」を参照してください。 **[ツール]、[Android]、[Android Emulator マネージャー]** の順に選択し、エミュレーターの新しいデバイス プロファイルを作成することもできます。

3. **F5** キーを押すと、プログラムがコンパイルされ、Android デバイスまたはエミュレーターに配置されます。

## <a name="windows"></a>Windows

1.  ソリューション エクスプローラーでユニバーサル Windows プロジェクトを右クリックして **[スタートアップ プロジェクトに設定]** をクリックします。

2.  **[ソリューション プラットフォーム]** ドロップダウンで、**[x86]** または **[x64]** を選択します。 **[ローカル コンピューター]** を選択します。

3.  **F5** キーを押すと、プログラムがデスクトップに配置されます。

## <a name="ios"></a>iOS

1.  「[Mac への接続](/xamarin/ios/get-started/installation/windows/connecting-to-mac/)」で説明されているように、ネットワーク上で Mac が利用でき、Visual Studio とペアになっていることを確認してください。

2.  ソリューション エクスプローラーで iOS プロジェクトを右クリックして **[スタートアップ プロジェクトに設定]** を選択します。

3.  次に示すように、Visual Studio のビルド ドロップダウン リストでターゲットに **[iPhoneSimulator]** を選択するか、Mac にテザリングされたデバイスがある場合、ターゲットに **[iPhone]** を選択します。

 ![iPhoneSimulator ビルド ターゲットを選択しています](../cross-platform/media/crossplat-xamarin-verify-5.png "CrossPlat Xamarin Verify 5")

 シミュレーターが一覧にない場合、Mac で Xcode を起動し、**[Xcode]** > **[ユーザー設定]** の順に選択し、**[ダウンロード]** をクリックします。 **[コンポーネント]** という見出しの下に、ダウンロード可能なシミュレーターのバージョンが表示されます。 デバッグに関する詳しい説明については、[iOS のデバッグ](/xamarin/ios/deploy-test/debugging-in-xamarin-ios)に関するページを参照してください。

4.  [Visual Studio] ドロップダウンからエミュレーター デバイス ターゲットを選択します。

 ![iPhone デバッグ ターゲットを選択しています](../cross-platform/media/crossplat-xamarin-verify-6.png "CrossPlat Xamarin Verify 6")

5. **F5** キーを押してデバッガーを起動します。 Mac 上のシミュレーターが起動し、Visual Studio でのデバッグ中にアプリを操作できるようになります。 iPhone または iPad の実機を Mac に接続した場合はこの一覧に表示され、代わりに選択できます。 デバイスもシミュレーターも表示されない場合、Mac との接続を確認してください。 上の手順 1 でリンクされている記事を参照するか、**[ツール]** > **[iOS]** > **[Mac とペアリング]** の順に進んでください。

6.  Mac に接続する際に問題が発生した場合は、「[接続のトラブルシューティング](/xamarin/ios/get-started/installation/windows/connecting-to-mac/troubleshooting/)」をご覧ください。

7.  "インストールされている iOS の署名キーに一致するプロビジョニング プロファイルがインストールされていません" というエラーが表示された場合は、次の改善案を試してください。

  - [Xcode へのアカウントの追加](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1)に関するページ (apple.com) の説明に従って、Mac 上の Xcode に Apple ID アカウントが追加されていることを確認します。  アカウントの追加後、必ず Visual Studio と Xcode の両方を再起動します。

  - iOS バンドル署名タブの iOS プロジェクト プロパティで、アクティブなデバッグ構成のカスタム権利フィールドが空であることを確認します。  注: 上記のエラー メッセージが表示された場合は、この設定の削除だけを試してみる必要があります。

  ![CrossPlat Xamarin Verify 8](../cross-platform/media/crossplat-xamarin-verify-8.png "CrossPlat Xamarin Verify 8")
