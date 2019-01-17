---
title: Visual Studio for Mac の概要
description: この記事では Visual Studio for Mac の機能を紹介します
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.openlocfilehash: 59e349b1d784e68c3ef6842834d875ce5d1917bb
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2019
ms.locfileid: "54315554"
---
# <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Visual Studio for Mac は、モバイル、デスクトップ、Web アプリケーションを作成するときに役立つ多くの機能が搭載された最新の高度な IDE です。 次の種類の開発がサポートされています。

- .NET を使用したモバイル:Android、iOS、tvOS、watchOS
- Mac デスクトップ アプリ
- .NET Core アプリケーション
- ASP.NET Core Web アプリケーション
- クロスプラットフォーム Unity ゲーム

リッチ エディター、デバッグ、iOS、Mac、Android とのネイティブ プラットフォーム統合、統合ソース制御などの機能があります。

この記事では、Visual Studio for Mac の持つさまざまな面を概説し、クロスプラットフォーム アプリケーションを作成する場合に強力なツールとなる機能を紹介します。

> [!TIP]
> **Visual Studio 2019 for Mac プレビュー**がテストできるようになりました。 これらの[インストールの指示](/visualstudio/mac/installation/?view=vsmac-2019)に従い、[2019 IDE ツアー](/visualstudio/mac/ide-tour/?view=vsmac-2019)を確認します。

## <a name="installation"></a>インストール

[インストール](install-preview.md) ガイドの手順に従って Visual Studio for Mac をダウンロードしてインストールします。

## <a name="language-support"></a>言語サポート

Visual Studio for Mac は、既定で C# と F# での開発をサポートしています。

### <a name="c"></a>C#

Visual Studio for Mac でクロスプラットフォーム アプリケーションを作成する場合、最もよく使用される言語は C# です。 IDE は C# 7 のすべての機能を完全にサポートしています。

### <a name="f"></a>F#

F# は、.NET 上で実行するように設計されている、厳密に型指定されたプログラミング言語です。 Visual Studio for Mac ユーザーが Android、Mac、および iOS で使用するプログラミング言語として提供されています。F# の使用方法と F# で作成されたサンプルについては、[F#](https://developer.xamarin.com/guides/cross-platform/fsharp/) ガイドを参照してください。

## <a name="platform-support"></a>プラットフォームのサポート

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) は、Windows、Linux、Mac で実行されるアプリケーションを作成するためのプラットフォームです。 Visual Studio for Mac は .NET Core プロジェクトの読み込み、作成、実行、デバッグをサポートしています。 

.NET Core プロジェクトを実行するには、.NET Core SDK をダウンロードし、インストールする必要があります。

.NET Core サポート:

- C# と F# の IntelliSense。
- コンソール、ライブラリ、Web アプリケーションのための .NET Core プロジェクト テンプレート。
- ブレークポイント、コール スタック、ウォッチ ウィンドウなど、完全なデバッグ サポート。
- NuGet PackageReferences と MSBuild ベースの復元。
- .NET Core SDK に含まれる Visual Studio テスト プラットフォームでテストを実行し、デバッグするための統合単体テスト サポート。
- 以前の project.json 形式からの以降。

まず ASP.NET Core Web アプリの[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)を確認してください。

## <a name="xamarin-mobile-app-development"></a>Xamarin のモバイル アプリ開発

[Xamarin](https://developer.xamarin.com/) のファーストクラス サポートにより、Android、macOS、iOS、tvOS、watchOS のために機能が豊富なネイティブ エクスペリエンスを開発できます。 Xamarin.Forms のクロスプラットフォーム アプリケーションにより、ネイティブ機能へのアクセスを制限することなく、Android、iOS、macOS 間で XAML ベースの UI コードを共有できます。

まずモバイル アプリの[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started)を確認してください。

### <a name="android"></a>Android

Visual Studio には、独自の統合 Android SDK マネージャーがあります。

Android アプリケーションの場合、Visual Studio for Mac には独自のデザイナーがあり、Android の `.axml` ファイルと連携してユーザー インターフェイスを視覚的に構築できます。 Visual Studio for Mac は次の画像のように Android Designer でこれらのファイルを開きます。

![Android UI デザイナー](media/intro-image31.png)

Android Designer の詳細については、[Designer の概要](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview)に関するドキュメントを参照してください。

### <a name="ios"></a>iOS

iOS Designer は Visual Studio for Mac と完全に統合されているので、.xib およびストーリーボード ファイルを視覚的に編集し、iOS、tvOS、および watchOS の UI と遷移を作成できます。 ツールボックスとデザイン サーフェイス間でドラッグ アンド ドロップ機能を使用してユーザー インターフェイス全体を構築できるだけでなく、直感的な方法でイベントを処理できます。 iOS Designer は、デザイン時のレンダリングにさらに役立つ[カスタム コントロール](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/)もサポートしています。

![iOS Storyboard デザイナー](media/intro-image30.png)

iOS Designer の使用方法については、[Designer](https://developer.xamarin.com/guides/ios/user_interface/designer) に関するドキュメントを参照してください。

### <a name="mac"></a>Mac

Xamarin にはネイティブの Mac API バインディングが用意されているので、見栄えのよい Mac アプリケーションを作成できます。

Visual Studio for Mac で Mac アプリケーションを作成する方法の詳細については、[Xamarin.Mac](https://developer.xamarin.com/guides/#mac) ドキュメントを参照してください。

## <a name="gaming"></a>ゲーム

Visual Studio for Mac は、Unity 5.6.1 を使用したクロスプラットフォーム ゲーム開発のサポートを提供しています。

まず Unity の[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Unity/Getting-Started)を確認してください。

## <a name="enterprise-features"></a>エンタープライズ機能

> [!Note]
> これらの製品は、Visual Studio Enterprise サブスクリプションでのみ使用できます。

### <a name="profiler"></a>プロファイラー

Xamarin Profiler には、プロファイルに使用できる 3 つのツールがあります。 「[Introduction to the Xamarin Profiler](https://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/xamarin-profiler/)」(Xamarin プロファイラー) ガイドでは、これらのインストルメントで測定する内容、アプリケーションの分析方法、各画面に表示されるデータの意味について説明します。

### <a name="inspector"></a>Inspector

Xamarin Inspector は、対話型 C# コンソールをユーザー ツールで提供しています。 ライブ アプリケーションを調査するときのデバッグまたは診断支援として、教育ツール、ドキュメント作成ツール、または実験ツールとして使用できます。

![Xamarin Inspector](media/intro-inspector.png)

多様なプログラミング プラットフォーム (Android、iOS、Mac、および Windows) を対象にすることができ、お使いの IDE のデバッグ ワークフローに統合できる高機能な C# コンソールを提供するスタンドアロン アプリケーションから構成されます。 

詳細については、「[Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/)」のガイドを参照してください。

## <a name="next-steps"></a>次の手順

- **全体像の把握** - Visual Studio for Mac の数多くの主要な機能の概要について、[IDE ツアー](/visualstudio/mac/ide-tour/)を参照してください。
- **セットアップ** - Visual Studio 2017 for Mac をダウンロードしてインストールする方法については、[インストール](/visualstudio/mac/installation/?view=vsmac-2017)に関するガイドを参照してください。
- **Xamarin チュートリアル** - Xamarin を使用してコードを開発する詳細な方法については、Xamarin の [Developer Center](https://developer.xamarin.com) を参照してください。
- **ビデオ** - Visual Studio for Mac の他の機能や側面の詳細については、[Xamarin University](https://university.xamarin.com) Web サイトのビデオをご覧ください。
- **ハンズオン ラボ** - Visual Studio for Mac に含まれている多様なワークロードの基本的な使用方法については、[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs)を参照してください。
