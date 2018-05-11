---
title: Xamarin によるモバイル開発の概要 | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2018
ms.topic: conceptual
ms.assetid: e970d936-1df4-4c0c-96e3-ef6191295882
ms.technology: vs-ide-mobile
author: ghogen
ms.author: ghogen
manager: douge
ms.workload:
- xamarin
ms.openlocfilehash: 9a174c8712f4ca9151fc30ddd357f53cec2891cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="learn-about-mobile-development-with-xamarin"></a>Xamarin を使用したモバイル開発について学習します

この記事では、Xamarin によるクロスプラットフォーム モバイル アプリの開発を理解するために役立つ概要を紹介します。 Visual Studio および Xamarinをまだインストールしていない場合は、まず [セットアップとインストール](../cross-platform/setup-and-install.md) プロセスを開始して、ここに戻り、インストーラーの実行中にこれらのリソースを処理します。  
  
> [!NOTE]
> 別途明記されない限り、副次的なページではなく、ここから直接リンクしているページのみを最初に読むことをお勧めします。 インストール プロセスが、この一覧を表示した後もまだ実行している場合は、戻って他のトピックを検索してもかまいません。  
>   
> また、"要点" のマークの付いたトピックを参照したり、後で "詳細" トピックに戻ったりするのも自由です。  
  
## <a name="essentials-introduction-to-xamarin"></a>要点: Xamarin の概要  

*10 分から 20 分*  
  
1.  [Xamarin を使用した Visual Studio におけるモバイル アプリ](https://www.visualstudio.com/xamarin/) (visualstudio.com) は、Xamarin の主要な特性についての簡単な概要を提供します。  
  
2.  Xamarin を宣伝している James Montemagno 氏の[C# と Visual Studio を使用したクロスプラットフォーム モバイル アプリのビルド](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2015-Final-Release-Event/Building-cross-platform-mobile-apps-using-C-and-Visual-Studio-2015) (Channel 9、15 分 16 秒)。 最初の 3 分間は、Xamarin の概要、続けてコードのデモンストレーションです。  
  
## <a name="essentials-overview-of-the-visual-studio-and-xamarin-environment"></a>要点: Visual Studio と Xamarin 環境の概要  

*5 分から 15 分*  
  
-   作業のほとんどは、Visual Studio と Xamarin がインストールされている Windows コンピューターで行います。 そのコンピューターで Windows アプリと Android アプリを直接ビルドし、デスクトップ、デバイス、エミュレーターで実行し、デバッグします。 また、Mac を使用して iOS アプリをリモートでビルド、実行、デバッグできます。 Windows コンピューターの Visual Studio は、iOS Storyboard Designer や iOS シミュレーターにも接続できます。  
  
-   Xcode と Visual Studio for Mac がインストールされている Mac は、iOS アプリのビルド ホスト、署名ホスト、ランタイム環境として機能します。 Windows コンピューターは iOS ビルドをこの Mac に委任します。 アプリケーションは Mac の iOS シミュレーターで実行されるか、Mac に接続されているテザリングされたデバイスで直接実行されます。 Mac 上のアプリと対話できますが、デバッグは Visual Studio で実行します。
  
以上の関係を下に図示します。  
  
![Xamarin 環境における Windows 開発機 と Mac 開発機の関係 ](../cross-platform/media/crossplat-xamarin-learn-1.png "CrossPlat Xamarin Learn 1")  

> [!NOTE]
> この図には Windows Phone を省略せずに記載しています。 Xamarin プラットフォームを使用するとき、推奨されるコード共有オプションは .NET Standard 2.0 ライブラリです。このライブラリは Windows Phone または Windows 10 Mobile デバイスと互換性がありません。 

iOS アプリの使用に関する詳細については、「[Xamarin.iOS for Visual Studio の概要](/xamarin/ios/get-started/installation/windows/introduction-to-xamarin-ios-for-visual-studio/)」を参照してください。
  
## <a name="essentials-how-projects-are-structured"></a>要点: プロジェクトの構造化の方法  

*10 分から 30 分*  
  
1.  [コード共有のオプション](/xamarin/cross-platform/app-fundamentals/code-sharing/)。 新しいアプリケーションの場合、.NET Standard ライブラリを使用してコードを共有してください。 ほとんどのビジネス ロジックのコードは、データベースへのアクセス、REST API の呼び出し、ポータブル Xamarin コンポーネントの呼び出しを含めて、.NET Standard ライブラリに存在します。 (この記事の終わりにある「[詳細: Xamarin コンポーネント](#components)」を参照してください。) Xamarin.Forms で記述された共通の UI コードは、.NET Standard にもあります。  
  
2.  (省略可能) [ケース スタディ: Tasky](/xamarin/cross-platform/app-fundamentals/building-cross-platform-applications/case-study-tasky/) では、フル機能アプリのデザインと構造のベスト プラクティスを説明します。たとえば、データ、データ アクセス、ビジネスの各レイヤーを分離する共有コードでプロジェクトを構成するなどです。  
  
## <a name="essentials-native-and-xamarinforms-ui-layers"></a>要点: ネイティブと Xamarin.Forms UI レイヤー  

*10 分から 40 分*  
  
Xamarin には、優れたアプリを構築する方法が 2 つあります。Xamarin Native と Xamarin.Forms です。  
  
Xamarin Native を使用して、iOS、Android、Windows の各ターゲット プラットフォームに個別の UI コードを記述します。  この方法では、プラットフォーム固有の API に直接アクセスし、プラットフォームごとに UI をカスタマイズして設計できます。  また、それぞれの UI の構築を支援するため、各プラットフォーム用のネイティブのデザイナーとコントロールのすべての機能を利用できます。  
  
Xamarin.Forms では、.NET Standard ライブラリですべてのプラットフォーム用の共有 UI レイヤーを記述できる汎用化された API セットを提供します。  Xamarin.Forms は各ターゲット プラットフォームのネイティブ コントロールに表示され、ネイティブの外観になります。  デザイナーを使用する代わりに、C# と XAML で UI を構築します。  

ほとんどの開発者は Xamarin.Forms を使用します。 Xamarin が初めての開発者にもこれをお勧めします。 Xamarin Native という手法はより難しく、ターゲット プラットフォームの詳細な知識が必要になります。
  
アプローチをあらかじめ決めておく必要はありません。Xamarin Native と Xamarin.Forms の両方を組み合わせてアプリを実装できます。  
  
-   汎用的な画面を構築するには Xamarin.Forms を使用します。 ログイン、連絡先フォーム、検索結果など、プラットフォーム全体で類似のユーザー インターフェイスと類似の機能が与えられます。  
  
-   プラットフォームごとに UI を調整するには、Xamarin.Forms のさまざまなカスタマイズ機能を使用します。 最も単純なカスタマイズ方法として `OnPlatform` API を選択できます。 また、カスタム ビューを作成したり、既存のレンダラーを拡張したり、カスタム レンダラーを作成したりできます。  
  
-   必要に応じて、Xamarin Native を使用し、各プラットフォームに固有の UI 機能を利用する画面を構築します。 1 つの例として、ネイティブ カメラ キャプチャと画像操作を利用する画面があります。  
  
一般的には、最初に Xamarin.Forms を使用し、プラットフォーム全体の UI コード共有を構築します。 次にカスタマイズ機能を使用し、プラットフォーム固有の調整を行います。 完全にプラットフォーム固有の画面が必要な場合は、Xamarin Native を使用して個別に追加できます。  
  
詳細を表示：  
  
1.  [Xamarin.Forms](/xamarin/xamarin-forms/) は、簡単な概要、Xamarin.Forms とネイティブ UI レイヤー (つまり、Xamarin.iOS と Xamarin.Android) を比較した長所と短所を提供します。  
  
2.  James Montemagno 氏のビデオ「[Xamarin.Forms: Native iOS, Android & Windows apps with C# & XAML](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/704)」 (Xamarin.Forms: C# と XAML を使用した、ネイティブの iOS、Android および Windows アプリ) (Channel9、13 分 3 秒) の最初の 3 分間では、別の構成で概要を紹介しており、それに続けてデモを見ることができます。  
  
3.  (省略可能) [Xamarin.Forms の概要](/xamarin/xamarin-forms/get-started/introduction-to-xamarin-forms/)  
  
4.  (省略可能) [デバイス クラス](/xamarin/xamarin-forms/platform/device/) ドキュメントでカスタマイズに `OnPlatform` を使用する例をご覧ください。
  
5.  (省略可能) Jason Smith による「[クロスプラットフォーム - Xamarin.Forms によるモバイル プラットフォーム間での UI コードの共有](https://msdn.microsoft.com/magazine/dn904669.aspx)」 (MSDN マガジン) では、Xamarin.Forms 内でのさまざまなカスタマイズ オプションの概要を説明します。オプションの詳細は[カスタム レンダラー](/xamarin/xamarin-forms/app-fundamentals/custom-renderer/)に関するページにあります。  
  
## <a name="deeper-dive-debugging-with-emulators"></a>詳細: エミュレーターでのデバッグ  

*10 分から 15 分*  
  
物理デバイスを使用せずにクロスプラットフォーム アプリをデバッグするには、ここで紹介したエミュレーターを使用する必要があります。  
  
### <a name="microsofts-android-emulator"></a>Microsoft の Android エミュレーター 

Microsoft の [Visual Studio Emulator for Android](~/cross-platform/visual-studio-emulator-for-android.md) の使用をお勧めします。これは Visual Studio と共にインストールされます。  [Visual Studio Emulator for Android](https://channel9.msdn.com/events/Visual-Studio/Connect-event-2015/711) ビデオ (Channel9、5 分 55 秒) は、概要とデモを提供します  
  
### <a name="apples-ios-simulator"></a>Apple の iOS シミュレーター

詳しくは、「 [iOS シミュレーター入門](https://developer.apple.com/library/prerelease/content/documentation/IDEs/Conceptual/iOS_Simulator_Guide/GettingStartedwithiOSSimulator/GettingStartedwithiOSSimulator.html#//apple_ref/doc/uid/TP40012848-CH5-SW1) 」(apple.com) をお読みください。  
  
### <a name="microsofts-windows-phone-emulator"></a>Microsoft の Windows Phone エミュレーター

詳細については、[Microsoft Emulator for Windows 10 Mobile を使用するテスト](/windows-uwp/windows-apps-src/debug-test-perf/test-with-the-emulator/)に関するページをお読みください。  
  
<a name="components" /> 

## <a name="deeper-dive-xamarin-components"></a>Deeper Dive: Xamarin Components  

*10 分*  
  
多くの拡張機能は、Xamarin コンポーネントをとおして、Xamarin アプリで利用できます。 [http://components.xamarin.com/](http://components.xamarin.com/) でダウンロードできる完全なカタログを見つけることができます。それには、追加の UI コントロール、認証、Microsoft Azure などのさまざまなクラウド サービス、その他多数のコンポーネントが含まれます。