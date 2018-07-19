---
title: Xamarin for Visual Studio のインストール | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.prod: visual-studio-dev15
ms.technology: vs-ide-mobile
author: charlespetzold
ms.author: chape
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a0f9240cd729d26eecd3c098c28799369b48cea6
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924370"
---
# <a name="setup-and-install"></a>セットアップとインストール

Xamarin を使用して一般的な C#/.NET コード ベースからネイティブの iOS、Android、Windows のアプリを作成するには、次のハードウェアとソフトウェアが必要です。

-   Windows アプリと Android アプリの開発: Visual Studio 2017 (Xamarin 開発機能を含む) がインストールされている Windows 開発コンピューター (仮想マシンではない)。

-   iOS アプリの開発: Xcode と Visual Studio for Mac がインストールされている、macOS Sierra 10.12 以降を搭載した Mac。

Xamarin プラットフォームを使用するために別個のライセンスを用意する必要はありません。

Windows と Mac のコンピューターを同時にセットアップできます。また、インストーラーを実行している間に、「[Learn about mobile development with Xamarin (Xamarin によるモバイル開発の概要)](../cross-platform/learn-about-mobile-development-with-xamarin.md)」にアクセスして、必要な背景情報を読んだり見たりすることができます。

このセットアップとインストールを実行した後、Xamarin プラットフォームを使用する上で問題が発生した場合、[forums.xamarin.com](http://forums.xamarin.com/) に質問を投稿してください。

<a name="prereq" />

## <a name="pre-requisites"></a>前提条件

###  <a name="for-targeting-windows-and-android"></a>Windows と Android を対象とする場合

Visual Studio 2017 インストールの前提条件の詳細は、「[Visual Studio 2017 製品ファミリのシステム要件](/visualstudio/productinfo/vs2017-system-requirements-vs)」にあります。

Windows 10 とすべての更新プログラムをインストールしている仮想マシンではなく実機の Windows コンピューターに Visual 2017 をインストールします。

### <a name="for-targeting-ios"></a>iOS を対象とする場合

Windows コンピューターから iOS のエミュレーターとデバイスをターゲットにするには、macOS 10.12 以降を装備し、Xcode 8.3 をインストールし、ネットワークに接続している Mac または Mac mini も必要になります。 要件の詳細については、「[Visual Studio for Mac のセットアップとインストール](/visualstudio/mac/installation)」を参照してください。

<a name="windows" />

##  <a name="windows-setup-visual-studio-and-xamarin"></a>Windows のセットアップ (Visual Studio と Xamarin)

Visual Studio 2017 をまだインストールしていない場合、次の手順を行います。

1.  [任意のエディションの Visual Studio 2017 のインストーラーをダウンロードして起動します](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) (Community、Professional、Enterprise)。 Visual Studio 2017 Community は無料版です。 Professional 版と Enterprise 版には 30 日間のお試し期間があり、その後はライセンスが必要になります。

2.  **[インストールしています]** ダイアログが表示されたら、次のボックスを選択します。

    - **[Mobile & Gaming (モバイルとゲーム)] > [.NET によるモバイル開発]**。 これを選択すると、さまざまな Android ツールやソフトウェア開発キットも自動的に選択されます。

        ![[Gaming and Mobile Development (ゲームとモバイル開発)] の [モバイル開発] オプションを選択する](../cross-platform/media/cross-plat-xamarin-setup-2a.png "クロスプラットフォーム Xamarin セットアップ 2")

    - (省略可能) **[Windows] > [ユニバーサル Windows プラットフォーム開発]**。

Visual Studio 2017 は既にインストールしているが、Xamarin プラットフォームはまだインストールしていない場合、次の手順を行います。

1. **[スタート]** メニューから **Visual Studio インストーラー**を実行します。

2.  インストーラー内で、**[詳細]** ボタンをクリックし、**[変更]** を選択します。

    ![Visual Studio のインストールで [変更] オプションを選択する](../cross-platform/media/cross-plat-xamarin-setup-1a.png "クロスプラットフォームの Xamarin セットアップ 1")

3.  **[インストールしています]** ダイアログが表示されたら、**[モバイルとゲーム]、[.NET によるモバイル開発]** の順に選択し、(任意で) **[Windows]、[ユニバーサル Windows プラットフォーム開発]** の順に選択します。 **[.NET によるモバイル開発]** オプションでは、既存の Xamarin インストールも更新されるはずです。

インストールの実行中、Mac のセットアップ手順を続行し、「[Xamarin を使用したモバイル開発について学習します](../cross-platform/learn-about-mobile-development-with-xamarin.md)」をお読みください。

5.  インストールが完了したら、Visual Studio を起動し、アカウントを求められたら Microsoft アカウントでサインインします。 これは Windows で使用するのと同じアカウントです。

6.  Android アプリをテストする場合、実機の Android デバイスがないときは、[Android SDK Emulator](/xamarin/android/get-started/installation/android-emulator/) を使います。

<a name="mac" />

##  <a name="mac-setup-apple-id-xcode-and-xamarin"></a>Mac のセットアップ (Apple ID、Xcode、および Xamarin)

1.  [https://appleid.apple.com](https://appleid.apple.com/) で無料の Apple ID を作成します (まだ作成していない場合)。 この Apple ID は Xcode をインストールしてサインインするために必要です。

2.  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) から Xcode をダウンロードしてインストールし、apple.com の「[Adding Your Account to Xcode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1)」 (Xcode にアカウントを追加する) の説明に従って、Apple ID を追加します。

3.  「[Visual Studio for Mac のセットアップとインストール](/visualstudio/mac/installation)」の説明に従い、Visual Studio for Mac をダウンロードしてインストールします。

4.  Windows と Mac のコンピューターの両方に Xamarin をインストールしたら、「[Mac への接続](/xamarin/ios/get-started/installation/windows/connecting-to-mac/)」の手順に従って、Windows コンピューター上の Visual Studio から iOS と Mac を操作できるようにします。

両方のコンピューターが同じローカル ネットワーク上にある必要があります。
