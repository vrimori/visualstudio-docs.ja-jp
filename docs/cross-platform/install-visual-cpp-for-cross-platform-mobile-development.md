---
title: Visual C++ for Cross-Platform Mobile Development のインストール | Microsoft Docs
ms.custom: ''
ms.date: 05/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aaea6b8d-55eb-4427-8185-c050f855c257
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 5dffe82511e75889ea588cb23b1f19490f991ab0
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251908"
---
# <a name="install-cross-platform-mobile-development-with-c"></a>C++ によるクロスプラットフォーム モバイル開発をインストールする

Visual Studio で C++ を使うと、Windows デスクトップ アプリ、ユニバーサル Windows プラットフォーム (UWP) アプリ、Linux アプリ、そして今では Android および iOS 用のアプリも、ビルドできます。 **C++ によるモバイル開発**ワークロードは、Visual Studio にインストール可能なコンポーネントのセットであり、クロスプラットフォームの iOS、Android、および UWP Visual Studio テンプレートを含みます。 すぐに始めるために必要なクロスプラットフォーム ツールおよび SDK がインストールされるので、それらを自分で検索、ダウンロード、構成する必要はありません。 これらのツールを Visual Studio で使用することで、クロスプラットフォーム プロジェクトを簡単に作成、編集、デバッグ、テストできます。 このトピックでは、Visual Studio を使って C++ でクロスプラットフォーム アプリを開発するために必要なツールとサード パーティのソフトウェアをインストールする方法について説明します。 概要については、「[Visual C++ クロスプラットフォーム モバイル](https://go.microsoft.com/fwlink/p/?LinkId=536383)」を参照してください。

## <a name="requirements"></a>必要条件

- インストール要件については、「[Visual Studio 2017 製品ファミリのシステム要件](/visualstudio/productinfo/vs2017-system-requirements-vs)」を参照してください。

   > [!IMPORTANT]
   > Windows 7 または Windows Server 2008 R2 を使用している場合は、Windows デスクトップ アプリケーション、Android Native Activity アプリおよびライブラリ、iOS 用のアプリとコード ライブラリのためのコードを開発できますが、Windows Phone アプリまたは UWP アプリのコードは開発できません。

特定のデバイス プラットフォームのアプリをビルドするには、いくつかの追加要件があります。

- Windows Phone エミュレーターおよび Microsoft Visual Studio Emulator for Android には、Hyper-V を実行できるコンピューターが必要です。 エミュレーターをインストールして実行する前に、Windows の Hyper-V 機能を有効にする必要があります。 詳細については、エミュレーターの[システム要件](system-requirements-for-the-visual-studio-emulator-for-android.md)をご覧ください。

- Android SDK に付属している x86 Android エミュレーターは、Intel HAXM ドライバーを実行できるコンピューター向けに最適化されています。 このドライバーには、VT-x および Execute Disable Bit をサポートしている Intel x64 プロセッサが必要です。 詳しくは、「[Intel® Hardware Accelerated Execution Manager (Intel® HAXM)](https://go.microsoft.com/fwlink/p/?LinkId=536385)」をご覧ください。

- iOS 用のコードをビルドするには、Apple ID、iOS Developer Program アカウント、[Xcode](https://go.microsoft.com/fwlink/p/?LinkId=536387) バージョン 6 以降を OS X Mavericks (バージョン 10.9) 以降のバージョンで実行できる Mac コンピューターが必要です。 インストール手順のリンクについては、「[iOS 用ツールのインストール](#install-tools-for-ios)」をご覧ください。

## <a name="get-the-tools"></a>ツールを取得する

C++ でのモバイル開発は、Visual Studio の Community、Professional、Enterprise エディションで利用できます。 Visual Studio を入手するには、[Visual Studio のダウンロード](https://go.microsoft.com/fwlink/p/?linkid=517106) ページにアクセスしてください。 クロスプラットフォーム モバイル開発ツールは、Visual Studio 2015 Update 2 以降で利用できます。

## <a name="install-the-tools"></a>ツールのインストール

Visual Studio 2017 用の Visual Studio インストーラーには、Visual Studio での Android および iOS の開発に必要な C++ 言語ツール、テンプレート、およびコンポーネントをインストールする **C++ によるモバイル開発**ワークロードが含まれます。 Android のビルドおよびデバッグに必要な GCC および Clang ツールセット、および iOS 開発用の Mac と通信するコンポーネントがインストールされます。 また、iOS および Android アプリの開発をサポートするために必要なサードパーティ製のツールとソフトウェア開発キットもすべてインストールされます。 これらのサードパーティ製ツールのほとんどは、Android プラットフォームのサポートに必要なオープン ソースのソフトウェアです。

- Android Native Development Kit (NDK) は、Android プラットフォームを対象にした C++ コードをビルドする場合に必要になります。

- Android のビルド プロセスには、Android SDK、Apache Ant、および Java SE Development Kit が必要です。

- Google Android Emulator および Intel Hardware Accelerated Execution Manager は、オプションですがお勧めするコンポーネントです。 Android デバイス上で直接開発およびデバッグできますが、通常、デバッグにはデスクトップでエミュレーターを使う方が簡単です。 また、Microsoft は、別途インストール可能な Visual Studio Emulator for Android も提供しています。

#### <a name="to-install-the-mobile-development-with-c-workload-in-visual-studio-2017"></a>Visual Studio 2017 で C++ によるモバイル開発ワークロードをインストールするには

1. **[スタート]** メニューから **Visual Studio インストーラー**を実行します。

1. Visual Studio が既にインストールされている場合は、インストールされている Visual Studio の中で変更するバージョンの **[変更]** ボタンをクリックします。 それ以外の場合は、**[インストール]** を選んで Visual Studio をインストールします。

1. **[ワークロード]** タブで、下にスクロールして、Visual Studio インストーラーの **[C++ によるモバイル開発]** ワークロードを選びます。 このワークロードを選ぶと、C++ による開発に必要な他のコンポーネントも選択されます。 他のワークロードを選び、個々のコンポーネントを同時にインストールすることもできます。 UWP もターゲットとするクロスプラットフォームのコードをビルドするには、**[ユニバーサル Windows プラットフォーム開発]** ワークロードを選びます。

1. **[インストールの詳細]** ウィンドウで、**[C++ によるモバイル開発]** を展開します。 **[オプション]** セクションでは、NDK の追加バージョン、Google Android Emulator、Intel Hardware Accelerated Execution Manager、IncrediBuild ビルド アクセラレーション ツールを選ぶことができます。

1. 既定では、1 つまたは複数の Android SDK セットアップ コンポーネントが、ワークロードによって組み込まれます。 Android SDK の追加バージョンを使用できます。 インストールに追加するには、**[個別のコンポーネント]** タブを選び、**[SDK、ライブラリ、およびフレームワーク]** セクションまで下にスクロールして選びます。

1. **[変更]** または **[インストール]** ボタンを選んで、**C++ によるモバイル開発**ワークロードと他の選択したワークロードおよびオプションのコンポーネントをインストールします。

   インストールが完了したら、インストーラーを閉じて、コンピューターを再起動します。 サード パーティ製コンポーネントの一部の設定操作は、コンピューターを再起動するまで有効になりません。

   > [!IMPORTANT]
   > 確実にすべてを正しくインストールするには、再起動する必要があります。

1. Visual Studio を開きます。 Visual Studio を実行するのが初めての場合は、構成してサインインするまでに時間がかかることがあります。 Visual Studio の準備ができたら、更新プログラムを確認し、それらをインストールします。

#### <a name="to-install-the-mobile-development-component-and-third-party-tools-in-visual-studio-2015"></a>Visual Studio 2015 でモバイル開発コンポーネントとサードパーティのツールをインストールするには

Visual Studio 2015 を使っている場合、そのインストーラーには Visual C++ for Cross-Platform Mobile Development をインストールするオプションが含まれます。このオプションでは、Visual Studio 2015 において必要な C++ 言語ツール、テンプレート、およびコンポーネントがインストールされます。

1. Visual Studio 2015 インストーラーを実行します。 オプションのコンポーネントをインストールするために、インストールの種類として **[カスタム]** を選びます。 **[次へ]** を選んで、インストールするオプションのコンポーネントを選びます。

1. **[機能の選択]** で、**[クロスプラットフォーム モバイル開発]** を展開し、**[Visual C++ モバイル開発]** を選びます。

   ![[Visual C&#43;&#43; モバイル開発] を選択する](../cross-platform/media/cppmdd_install_vcmdd.png "CPPMDD_Install_VCMDD")

   既定では、**[Visual C++ モバイル開発]** を選ぶと、**[プログラミング言語]** オプションは **[Visual C++]** をインストールするように設定され、**[共通ツールおよびソフトウェア開発キット]** オプションは必要なサード パーティ製コンポーネントをインストールするように設定されます。 必要な場合、その他のコンポーネントを選択することができます。 既定では、**[Microsoft Visual Studio Emulator for Android]** も選ばれます。 既にインストールされているコンポーネントは、一覧では非アクティブとして表示されます。

   ユニバーサル Windows アプリをビルドし、Android および iOS プロジェクトとの間でコードを共有するには、**[機能の選択]** で、**[Windows 開発と Web 開発]** を展開し、**[ユニバーサル Windows アプリ開発ツール]** をオンにします。 ユニバーサル Windows アプリをビルドする予定がない場合は、このオプションを省略できます。

   **[次へ]** を選択して続行します。

1. サードパーティ製コンポーネントには、それぞれ独自のライセンス条項があります。 ライセンス条項を表示するには、各コンポーネントの横にある **[ライセンス条項]** リンクを選びます。 **[インストール]** を選択して、コンポーネントを追加し、Visual Studio と、Visual C++ for Cross-Platform Mobile Development をインストールします。

1. インストールが完了したら、インストーラーを閉じて、コンピューターを再起動します。 サード パーティ製コンポーネントの一部の設定操作は、コンピューターを再起動するまで有効になりません。

   > [!IMPORTANT]
   > 確実にすべてを正しくインストールするには、再起動する必要があります。

   Microsoft Visual Studio Emulator for Android コンポーネントのインストールが失敗した場合は、お使いのコンピューターで Hyper-V が有効になっていない可能性があります。 **[Windows の機能の有効化または無効化]** コントロール パネル アプリを使って Hyper-V を有効にしてから、Visual Studio インストーラーをもう一度実行ます。

   > [!NOTE]
   > お使いのコンピューターまたは Windows のバージョンで Hyper-V がサポートされていない場合は、Microsoft Visual Studio Emulator for Android コンポーネントを使用できません。 Windows の Home エディションには、Hyper-V のサポートが含まれていません。

1. Visual Studio を開きます。 Visual Studio を実行するのが初めての場合は、構成してサインインするまでに時間がかかることがあります。 Visual Studio の準備が完了したら、 **[ツール]** メニューで **[拡張機能と更新プログラム]**、 **[更新プログラム]** の順に選びます。 Visual C++ for Cross-Platform Mobile Development または Microsoft Visual Studio Emulator for Android 用の利用可能な Visual Studio の更新プログラムがある場合は、それらをインストールします。

## <a name="install-tools-for-ios"></a>Install tools for iOS

Visual C++ for Cross-Platform Mobile Development を使用して、iOS コードを編集およびデバッグし、iOS シミュレーターまたは iOS デバイスに配置することができます。ただし、ライセンスの制限により、コードのビルドはリモートの Mac 上で行わなければなりません。 Visual Studio を使用して iOS アプリをビルドおよび実行するには、Mac 上にリモート エージェントをセットアップして構成する必要があります。 インストール方法、前提条件、構成オプションの詳細については、「[Install And Configure Tools to Build using iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)」を参照してください。 iOS 用にビルドするのでない場合は、この手順を省略できます。

## <a name="install-or-update-dependencies-manually"></a>手動による依存関係のインストールまたは更新

**C++ によるモバイル開発**ワークロード (または、Visual Studio 2015 では Visual C++ モバイル開発オプション) をインストールするときに、サードパーティの 1 つ以上の依存関係を Visual Studio インストーラーでインストールしないことにした場合、それらの依存関係は、後で「[ツールのインストール](#install-the-tools)」の手順に従ってインストールできます。 最新のサードパーティ製コンポーネントをインストールするため、Visual Studio インストーラーは定期的に更新されます。 それを使って、更新された SDK と NDK をインストールできます。 また、Visual Studio とは別にインストールまたは更新することもできます。

> [!CAUTION]
> Java 以外の依存関係は、任意の順序でインストールできます。 JDK は、Android SDK をインストールする前にインストールして構成する必要があります。

次の情報を参照し、リンクを使用して、従属関係を手動でインストールします。

- [Java SE 開発キット](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

   既定では、インストーラーによって Java のツールが *C:\Program Files (x86)\Java* に格納されます。

- [Android SDK](https://developer.android.com/sdk/index.html#command-tools)

   インストール中に、推奨されたとおりに API を更新します。 最低でも Android 5.0 Lollipop (API レベル 21) の SDK がインストールされていることを確認します。 既定では、インストーラーによって Android SDK が *C:\Program Files (x86)\Android\android-sdk* に格納されます。

   Android SDK ディレクトリにある SDK Manager アプリをもう一度実行すると、SDK を更新したり、オプション ツールや追加の API レベルをインストールしたりできます。 **[管理者として実行]** を使用して SDK Manager アプリを実行しなければ、更新のインストールが失敗する可能性があります。 Android アプリのビルドで問題が発生した場合は、SDK Manager を確認して、インストール済み SDK の更新プログラムの有無を調べてください。

   Android SDK に付属している Android エミュレーターのいくつかを使用するには、オプションの Intel HAXM ドライバーをインストールする必要があります。 Intel HAXM ドライバーを正常にインストールするには、Windows から Hyper-V 機能を削除する必要がある場合があります。 Windows Phone エミュレーターおよび Microsoft Visual Studio Emulator for Android を使用するには、Hyper-V 機能を復元する必要があります。 詳細については、[Android Emulator ハードウェアの高速化](https://docs.microsoft.com/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)に関するページを参照してください。

- [Android NDK](https://developer.android.com/tools/sdk/ndk/index.html)

   既定では、インストーラーによって Android NDK が *C:\ProgramData\Microsoft\AndroidNDK* に格納されます。 Android NDK をもう一度ダウンロードしてインストールすると、NDK のインストールを更新できます。

- [Apache Ant](https://ant.apache.org/bindownload.cgi)

   既定では、インストーラーによって Apache Ant が *C:\Program Files (x86)\Microsoft Visual Studio 14.0\Apps* に格納されます。

- [Microsoft Visual Studio Emulator for Android](https://aka.ms/vscomemudownload)

   Microsoft Visual Studio Emulator for Android は、コードをテストおよびデバッグするのに役立つ、オプションのエミュレーターです。 Visual Studio Emulator for Android のリリース後に、Google は Intel の HAXM によるハードウェア アクセラレーションを使うように Android エミュレーターを更新しました。 可能な場合は、Google の高速化されたエミュレーターを使うことをお勧めします。最新の Android OS イメージと Google Play サービスにアクセスできます。

ほとんどの場合、Visual Studio によって、インストールしたサードパーティ製ソフトウェアの構成が検出され、内部環境変数にインストール パスが保持されます。 これらのクロス プラットフォーム開発ツールの既定のパスは、Visual Studio IDE でオーバーライドできます。

#### <a name="to-set-the-paths-for-third-party-tools"></a>サード パーティのツールのパスを設定するには

1. Visual Studio のメニュー バーで、**[ツール]** > **[オプション]** の順に選びます。

1. **[オプション]** ダイアログ ボックスで、 **[クロス プラットフォーム]** > **[C++]** > **[Android]** の順に選びます。

   ![Android ツールのパス オプション](../cross-platform/media/cppmdd_options_android.PNG "CPPMDD_Options_Android")

1. ツールが使用するパスを変更するには、パスの横にあるチェック ボックスをオンにして、テキスト ボックスでフォルダー パスを編集します。 参照ボタン (**...**) を使用して **[場所を選択]** ダイアログを開き、フォルダーを選ぶこともできます。

1. **[OK]** を選んで、カスタム ツール フォルダーの場所を保存します。

## <a name="see-also"></a>関連項目

- [iOS を使用してビルドするためのツールのインストールおよび構成](install-and-configure-tools-to-build-using-ios.md)
- [Visual C++ クロスプラットフォーム モバイル](https://go.microsoft.com/fwlink/p/?LinkId=536383)
