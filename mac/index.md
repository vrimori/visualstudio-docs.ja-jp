---
title: "Visual Studio for Mac の概要"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 3A130EC1-DD8C-4125-9034-B08D7AF7EA65
ms.translationtype: HT
ms.sourcegitcommit: f6c7e290f0abc2c32456e076420a7695ae868ba6
ms.openlocfilehash: ffbd08a4a6765c2cc38329325e91f4aed12d88d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---

# <a name="introducing-visual-studio-for-mac"></a>Visual Studio for Mac の概要

Visual Studio for Mac は、モバイル、デスクトップ、および Web アプリケーションを作成するときに役立つ多くの機能が搭載された最新の高度な IDE です。 次の開発をサポートしています。

* モバイルと .NET: Android、iOS、tvOS、watchOS
* Mac デスクトップ アプリ
* .NET Core アプリケーション
* ASP.NET Core Web アプリケーション
* クロスプラットフォーム Unity ゲーム

リッチ エディター、デバッグ、iOS、Mac、および Android とのネイティブ プラットフォーム統合、統合ソース制御などを含む、多数の機能があります。

このトピックでは、Visual Studio for Mac の多様なセクションについて説明し、クロスプラットフォーム アプリケーションを作成する場合に強力なツールになる機能の一部を紹介します。

## <a name="installation"></a>インストール

[インストール](~/installation.md) ガイドの手順に従って Visual Studio for Mac をダウンロードしてインストールします。

## <a name="language-support"></a>言語サポート

Visual Studio for Mac は、既定で C# と F# での開発をサポートしています。

### <a name="c"></a>C#

Visual Studio for Mac でクロスプラットフォーム アプリケーションを作成する場合、C# が最もよく使用される言語です。 すべての C# 7 機能の完全なサポートが含まれています。

### <a name="f"></a>F#

F# は、.NET 上で実行するように設計されている、厳密に型指定されたプログラミング言語です。 Android、Mac、および iOS 上の Visual Studio for Mac ユーザーがプログラミング言語として使用できます。 F# の使用方法と F# で作成されたサンプルについては、[F#](https://developer.xamarin.com/guides/cross-platform/fsharp/) ガイドを参照してください。

## <a name="platform-support"></a>プラットフォームのサポート

## <a name="net-core"></a>.NET Core

[.NET Core](https://www.microsoft.com/net/core#macos) は、Windows、Linux、Mac で実行されるアプリケーションを作成するためのプラットフォームです。 Visual Studio for Mac では、.NET Core プロジェクトを読み込み、作成し、実行し、デバッグできます。

.NET Core プロジェクトを実行するには、.NET Core SDK をダウンロードし、インストールする必要があります。

.NET Core サポート:

* C# と F# の IntelliSense。
* コンソール、ライブラリ、Web アプリケーションのための .NET Core プロジェクト テンプレート。
* ブレークポイント、コール スタック、ウォッチ ウィンドウなど、完全なデバッグ サポート。
* NuGet PackageReferences と MSBuild ベースの復元。
* .NET Core SDK に含まれる Visual Studio テスト プラットフォームでテストを実行し、デバッグするための統合単体テスト サポート。
* 以前の project.json 形式からの以降。

まず ASP.NET Core Web アプリの[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started)を確認してください。

## <a name="xamarin"></a>Xamarin

[Xamarin](https://developer.xamarin.com/) のファーストクラス サポートにより、Android、macOS、iOS、tvOS、watchOS のために機能が豊富なネイティブ エクスペリエンスを開発できます。 Xamarin.Forms のクロスプラットフォーム アプリケーションにより、ネイティブ機能へのアクセスを制限することなく、Android、iOS、macOS 間で XAML ベースの UI コードを共有できます。

まずモバイル アプリの[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs/tree/master/Mobile/Getting-Started)を確認してください。

### <a name="android"></a>Android

Visual Studio には、独自の統合 Android SDK マネージャーがあります。

Android アプリケーションの場合、Visual Studio for Mac には独自のデザイナーがあり、Android の `.axml` ファイルと連携してユーザー インターフェイスを視覚的に構築できます。 Visual Studio for Mac は次のように Android デザイナーでこれらのファイルを開きます。

![](media/intro-image31.png)

Android デザイナーの詳細については、「[Designer Overview](https://developer.xamarin.com/Android/Guides/User_Interface/Designer_Overview)」(デザイナーの概要) ドキュメントを参照してください。

### <a name="ios"></a>iOS

iOS Designer は Visual Studio for Mac と完全に統合されているので、.xib およびストーリーボード ファイルを視覚的に編集し、iOS、tvOS、および watchOS の UI と遷移を作成できます。 ツールボックスとデザイン サーフェイス間でドラッグ アンド ドロップ機能を使用してユーザー インターフェイス全体を構築できるだけでなく、直感的な方法でイベントを処理できます。 iOS Designer は、デザイン時のレンダリングにさらに役立つ[カスタム コントロール](https://developer.xamarin.com/guides/ios/user_interface/designer/ios_designable_controls_overview/)もサポートしています。

![](media/intro-image30.png)

iOS Designer の使用方法については、[Designer](https://developer.xamarin.com/guides/ios/user_interface/designer) のドキュメントを参照してください。

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

Xamarin Inspector は、対話型 C# コンソールとツールをユーザーに提供しています。 ライブ アプリケーションを調査するときのデバッグまたは診断支援として、教育ツール、ドキュメント作成ツール、または実験ツールとして使用できます。

![](media/intro-inspector.png)

多様なプログラミング プラットフォーム (Android、iOS、Mac、および Windows) を対象にすることができる高機能な C# コンソールを提供するスタンドアロン アプリケーションと、IDE のデバッグ ワークフローへの統合から構成されます。

詳細については、[Xamarin Inspector](https://developer.xamarin.com/guides/cross-platform/inspector/) のガイドを参照してください。

## <a name="next-steps"></a>次のステップ

* **全体像の把握** - Visual Studio for Mac の数多くの主要な機能の概要について、[IDE ツアー](~/ide-tour.md)を参照してください。
* **セットアップ** - Visual Studio をダウンロードしてインストールする方法については、「[インストール](~/installation.md)」ガイドを参照してください。
* **Xamarin チュートリアル** - Xamarin を使用してコードを開発する詳細な方法については、Xamarin の [Developer Center](https://developer.xamarin.com) を参照してください。
* **ビデオ** - Visual Studio for Mac の他の機能や側面の詳細については、[Xamarin University](https://university.xamarin.com) Web サイトのビデオをご覧ください。
* **ハンズオン ラボ** - Visual Studio for Mac に含まれている多様なワークロードの基本的な使用方法については、[ハンズオン ラボ](https://github.com/Microsoft/vs4mac-labs)を参照してください。
