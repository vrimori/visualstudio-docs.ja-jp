---
title: Xamarin for Visual Studio のインストール | Microsoft Docs
ms.custom: ''
ms.date: 04/13/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cfcad00-352c-4161-814c-f5ae32d8ada8
ms.technology: vs-ide-mobile
author: asb3993
ms.author: amburns
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: a935ab3768d5e900aea681b392e920763cb53016
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="setup-and-install"></a>セットアップとインストール

Xamarin を使用して一般的な C#/.NET コード ベースからネイティブの iOS、Android、および Windows のアプリを作成するには、次の条件を満たす必要があります。

-   Windows アプリと Android アプリの開発: Visual Studio 2017 または 2015 と Xamarin がインストールされている Windows 開発用コンピューター。 [Xamarin を直接インストールする](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install)手順 (xamarin.com) を実行すれば、Visual Studio 2013 を使うこともできます。

-   iOS アプリの開発: Xcode と Xamarin がインストールされている、macOS Sierra 10.12 以降を搭載した Mac。

 Windows と Mac のコンピューターを同時にセットアップできます。また、インストーラーを実行している間に、「[Learn about mobile development with Xamarin (Xamarin によるモバイル開発の概要)](../cross-platform/learn-about-mobile-development-with-xamarin.md)」にアクセスして、必要な背景情報を読んだり見たりすることができます。

このセットアップとインストールを実行した後、Xamarin を使用する上で問題がある場合は、[forums.xamarin.com](http://forums.xamarin.com/) に質問を投稿してください。

> [!NOTE]
> 2016 年 3 月 31 日の時点で、Visual Studio のすべてのエディションに付属のすべての Xamarin に追加のコストはかからず、別個のライセンスは必要ありません。 Xamarin Studio Community for Mac も、学生、OSS 開発者、小規模チームの場合には無料です。 以前の Xamarin ライセンスが構成されている Visual Studio の既存のインストールの場合は、Xamarin をバージョン 4.0.3.214 以降に更新する必要があることにご注意ください。 これを行うには、**[ツール] > [オプション] > [Xamarin] > [その他]** の順に移動し、**[今すぐ確認]** リンクをクリックして、4.0.3.214 更新プログラムをダウンロードします。 Visual Studio を再起動して、**[ツール] > [Xamarin アカウント...]** に移動すると、更新の状況を確認できるはずです。

##  <a name="prereq"></a> 前提条件

###  <a name="for-targeting-windows-and-android"></a>Windows と Android を対象とする場合

1.  推奨: Android エミュレーターのパフォーマンスが最高になるように、Windows 8 以降を実行している (VM ではない) 物理 Windows コンピューター。 (VM ではなく物理コンピューターが必要であることが書かれていましたか?)

2.  Windows 7 以前のコンピューターを使用できます。その場合は、エミュレーターとして Xamarin Player for Android を使用します。

3. どちらの構成でも、接続された物理デバイス上では、いつでもアプリを直接実行できます。

### <a name="for-targeting-ios"></a>iOS を対象とする場合

1.  macOS 10.12 以降が動作する macOS Sierra を搭載した、ネットワーク接続されている Mac または Mac mini (Xcode 8.3 のために必要)。

2.  主要な開発環境として Windows (7 以降) コンピューターで Visual Studio を使う場合は、ネットワーク接続された Mac は、iOS アプリのコンパイルとデバッグ、iOS シミュレーターまたはテザリングされたデバイスへのアタッチ、または Visual Studio でユーザー インターフェイスを設計するためにストーリーボード デザイナーを使う場合にのみ必要になります。 この 2 次的な役割には、古いモデルの Mac で十分です。

##  <a name="windows"></a> Windows のセットアップ (Visual Studio と Xamarin)

> [!TIP]
> 次の手順は、Visual Studio 2017 に適用されます。 Visual Studio 2015 については、[MSDN](setup-and-install.md) をご覧ください。 Xamarin を Visual Studio 2013 (Update 2 が必要) で使うには、[Xamarin の直接インストール](https://developer.xamarin.com/guides/cross-platform/getting_started/requirements/#install) (xamarin.com) の指示に従ってください。

1.  [任意のエディションの Visual Studio 2017 のインストーラーをダウンロードして起動します](https://www.visualstudio.com/downloads/) (Community、Professional、Enterprise)。 Visual Studio 2017 Community は、無料のエディションです。Professional および Enterprise の各エディションは評価版として 30 日間使用できます (その後はライセンスを購入する必要があります)。

    - Visual Studio 2017 を既にインストールしてある場合は、**[スタート]** メニューから **Visual Studio インストーラー**を実行します。

2.  インストーラー内で、**[詳細]** ボタンをクリックし、**[変更]** を選択します。

    ![Visual Studio のインストールで [変更] オプションを選択する](../cross-platform/media/cross-plat-xamarin-setup-1a.png "クロスプラットフォームの Xamarin セットアップ 1")

3.  次のチェック ボックスを選択します。

    - **[Mobile & Gaming (モバイルとゲーム)] > [.NET によるモバイル開発]**。 これにより、[共通のツールとソフトウェア開発キット] の下のさまざまな Android ツールも自動的に選択されます。 このオプションでは、既存の Xamarin インストールも更新されるはずです。

        ![[Gaming and Mobile Development (ゲームとモバイル開発)] の [モバイル開発] オプションを選択する](../cross-platform/media/cross-plat-xamarin-setup-2a.png "クロスプラットフォーム Xamarin セットアップ 2")

    - (省略可能) **[Windows] > [ユニバーサル Windows プラットフォーム開発]**。 これには、ダウンロードに時間がかかるエミュレーター イメージをインストールするためのオプションが含まれています。いつでも Visual Studio インストーラーに戻って後で追加できます。

4.  **[変更]** ボタンをクリックし、プロセスを実行します。 このプロセスでも、完了までにしばらく時間がかかります。その間、Mac のセットアップ手順を続行し、「[Xamarin を使用したモバイル開発について学習します](../cross-platform/learn-about-mobile-development-with-xamarin.md)」を読むことができます。

5.  インストールが完了したら、Visual Studio を起動し、アカウントを求められたら Microsoft アカウントでサインインします (これは Windows で使用するのと同じアカウントです)。

6.  Android アプリをテストする場合、物理デバイスがないときは、[Android SDK Emulator](https://developer.xamarin.com/guides/android/deployment,_testing,_and_metrics/debug-on-emulator/android-sdk-emulator/) を使います。 下記のメモをご覧ください。

> [!NOTE]
> **Windows コンピューター上のエミュレーター**: CPU でサポートされる仮想化テクノロジは、一度に 1 つだけです。このため、開発用コンピューター上では 1 つのみを使用することをお勧めします。 主要な仮想化テクノロジには次の 3 つがあります。Hyper-V (Android 用の Visual Studio エミュレーターおよび Windows Phone エミュレーターで使用)、Virtual Box (Genymotion で使用)、Intel HAXM (Android SDK エミュレーターで使用)。 Hyper-V と Virtual Box 間にはさまざまな問題があるため、特定のコンピューター上では 1 種類のエミュレーターだけを使用することをお勧めします。したがって、Windows 8 以降のコンピューターでは Hyper-V を使用すること、および Windows 7 以前のコンピューターと Mac 上で実行している Windows では HAXM エミュレーターを使用することが前述のとおり推奨されます。

##  <a name="mac"></a> Mac のセットアップ (Apple ID、Xcode、および Xamarin)

1.  [https://appleid.apple.com](https://appleid.apple.com/) で無料の Apple ID を作成します (まだ作成していない場合)。 これは Xcode をインストールしてサインインするために必要です。

2.  [https://developer.apple.com/xcode/](https://developer.apple.com/xcode/) から Xcode をダウンロードしてインストールし、apple.com の「[Adding Your Account to XCode](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppStoreDistributionTutorial/AddingYourAccounttoXcode/AddingYourAccounttoXcode.html#//apple_ref/doc/uid/TP40013839-CH40-SW1)」 (XCode にアカウントを追加する) の説明に従って、Apple ID を追加します。

3.  「 [Xamarin.iOS のダウンロードとインストール](http://developer.xamarin.com/guides/ios/getting_started/installation/mac/) 」(xamarin.com) の手順に従って、Xamarin をダウンロードしてインストールします。

4.  Windows と Mac のコンピューターの両方に Xamarin をインストールしたら、「[Connecting to the Mac](http://developer.xamarin.com/guides/ios/getting_started/installation/windows/xamarin-mac-agent/)」(Mac への接続) (xamarin.com) の手順に従って、Windows コンピューター上の Visual Studio から iOS と Mac を操作できるようにします。

    両方のコンピューターが同じローカル ネットワーク上にある必要があることにご注意ください。