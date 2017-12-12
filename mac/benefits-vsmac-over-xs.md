---
title: "Xamarin Studio 上の Visual Studio for Mac の利点 | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 6ACF5FD4-D5C1-4050-95E3-467C753F25F1
ms.openlocfilehash: 08e693e92d6d07da21f8230f9c1de49f071c05e5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="benefits-of-visual-studio-for-mac-over-xamarin-studio"></a>Xamarin Studio 上の Visual Studio for Mac の利点 
 
Mac の全機能搭載 IDE として Xamarin Studio に取って代わったのが Visual Studio for Mac です。 Web アプリケーションとサービス、プラットフォームに依存しないモバイル/デスクトップ アプリ、ゲームの開発するための機能を提供します。 また、Azure と簡単に統合できます。Azure に発行するのも、Azure Functions を作成するのも簡単です。 現代の IDE に求められるすべてが備わっています。全機能搭載のソース エディター、強力なデバッガー、カスタマイズ可能なワークスペース、Git 統合、豊富な機能を持つ拡張システムなどです。すべてが Mac ネイティブとして設計されています。 

その他の機能: 

* Roslyn ベースの C# IntelliSense、リファクタリング、アナライザー、コード修正 
* NuGet ベースのパッケージ管理 
* Visual Studio 互換のプロジェクト形式 
* MSBuild ビルド エンジン 
* 統合単体試験 
* すぐに F# を利用可能 

このガイドに記載されている利点で**プレビュー**の印が付いているものは、[アルファ チャネル](https://docs.microsoft.com/visualstudio/mac/update#Changing_the_Updater_channel)のみで利用できます。 

## <a name="language-support"></a>言語サポート 

Mac で C# 7 コードを記述できるのは、Visual Studio for Mac だけです。

## <a name="net-core"></a>.NET Core  

[.NET Core](https://www.microsoft.com/net/core#macos) は、Windows、Linux、Mac で実行されるアプリケーションを作成するためのプラットフォームです。 Visual Studio for Mac では、.NET Core プロジェクトを読み込み、作成し、実行し、デバッグできます。 

.NET Core は Visual Studio for Mac と共にインストールされ、すぐに利用できます。

.NET Core サポート: 

* C# と F# の IntelliSense。 
* コンソール、ライブラリ、Web アプリケーションのための .NET Core プロジェクト テンプレート。 
* ブレークポイント、コール スタック、ウォッチ ウィンドウなど、完全なデバッグ サポート。 
* NuGet パッケージ参照と MSBuild ベースの復元。 
* .NET Core SDK に含まれる Visual Studio テスト プラットフォームでテストを実行し、デバッグするための統合単体テスト サポート。 
* 以前の project.json 形式からの以降。 
* .NET 標準プロジェクト サポート。

## <a name="web-development"></a>Web 開発  

### <a name="aspnet-core"></a>ASP.NET Core 

Visual Studio for Mac には、MVC プロジェクトと Web API プロジェクト用の ASP.NET Core テンプレートが含まれています。面倒な設定なしですぐに利用できます。
 
![HTML IntelliSense](media/benefits-vsmac-over-xs-image3.png)

Visual Studio for Mac では、HTML、CSS、JSON ファイルのための新しい Web ツール サポートも追加されています。 

### <a name="html"></a>HTML 

* 新しい HTML テンプレート。 
* 強化されたスマート インデントと書式設定。 
* 強化された色づけ。 
* 強化された IntelliSense。 
* コードの折りたたみ (有効にする必要があります)。 
* コマンドのアンミニファイ。 
* 強化されたコード テンプレート (スニペット)。 
* `<div>` を使用して選択範囲を囲む。 
* 上/下オプションで、選択したテキストを上下に移動する。 

### <a name="css"></a>CSS 

* 強化されたスマート インデントと書式設定。 
* 強化された色づけ。 
* 強化された IntelliSense。 
* コード折りたたみ。 
* さまざまなコード テンプレート (スニペット)。 
* 上/下オプションで、選択したテキストを上下に移動する。 

### <a name="json"></a>JSON 
* schemastore.org へのアクセスを利用したスキーマ選択。 
* スキーマからの検証。 
* スキーマからの IntelliSense。 
* 強化されたスマート インデントと書式設定。 
* 強化された色づけ。 
* コメント化/コメント解除。 
* 引用の挿入と中かっこの一致。 
* 上/下オプションで、選択したテキストを上下に移動する。 

## <a name="publishing-to-azure"></a>Azure への発行

Visual Studio for Mac では、ASP.NET Core の Web アプリ/サービスを Azure App Service に発行できます。 

![Azure に発行する](media/benefits-vsmac-over-xs-image1.png)

### <a name="azure-functions-preview"></a>Azure Functions (**プレビュー**)

Azure Functions を使用すると、クラウドで小さなコードの集まりまたは関数を簡単に実行できます。 Visual Studio for Mac では、Azure Functions をコード化し、ローカルでデバッグできます。 始めるには、[新しいプロジェクト] ダイアログの [クラウド] で [Azure Functions] を探してください。 

### <a name="docker-support-preview"></a>Docker サポート (**プレビュー**)

ASP.NET Core アプリを Docker コンテナーに発行し、Azure App Service から実行できるようになりました。 

プロジェクトで Docker サポートを有効にするには、ASP.NET Core Web アプリを右クリックし、**[追加]、[Add Docker Support]\(Docker サポートの追加\)** の順に選択します。 

Docker コンテナーに Web アプリを発行するには、**[発行]、[Azure に発行する]** の順に選択します。これは Visual Studio for Mac で導入されたワークフローです。

## <a name="source-editor-improvements"></a>ソース エディターの改善 

Roslyn ベースの C# IntelliSense、リファクタリング、アナライザー、コード修正に加え、Visual Studio for Mac ソース エディターは次の点で Xamarin Studio より機能強化されています。 

### <a name="language-bundles"></a>言語バンドル 

Visual Studio for Mac は TextMate (`.tmBundle`) 言語バンドルと sublime 3 (`.sublime`) 言語バンドルに対応しています。これを利用して次のものを追加できます。 

* エディターの配色テーマ 
* コード スニペット 
* 新しい言語の文法、強調表示、基本 IntelliSense 

バンドルは **[ユーザー設定]、[テキスト エディター]、[言語バンドル]** で追加できます。 

### <a name="color-theme-support"></a>配色テーマのサポート 

Visual Studio for Mac では、次の配色テーマ形式がサポートされています。 

* Visual Studio (`.vssettings`) 
* Xamarin Studio (`.json`) 
* TextMate (`tmTheme`) 

## <a name="unity"></a>Unity 

[Unity](https://unity3d.com/) はゲーム開発ツールです。あらゆる主要プラットフォーム (モバイル、デスクトップ、コンソール、AR デバイス、VR デバイス、Web) でプラットフォームに依存しない高品質の 2D ゲームと 3D ゲームを開発できます。 

Unity 5.6.1 以降で、Visual Studio for Mac を利用して Unity ゲームを開発し、デバッグできます。 始めに、Visual Studio を Unity の 5.6.1 スクリプト エディターに設定します。 

Tools for Unity の内容: 

* C# で記述されたスクリプトのサポート。 
* Unity ソリューション パッド。 
* Unity Editor のワンクリック デバッグ。 
* Unity メッセージ用の IntelliSense。 
* Unity シェーダーのコード配色。 
* Unity ドキュメントへのアクセス。 

## <a name="xamarin"></a>Xamarin 

Xamarin のプラットフォームに依存しない機能は、常に、Xamarin Studio の最上の機能でありましたが、Visual Studio for Mac でしか利用できない Xamarin 機能があります 

### <a name="android"></a>Android 

* [Android SDK manager](https://developer.xamarin.com/guides/android/application_fundamentals/using-the-sdk-manager/)  
* Android O は Visual Studio for Mac でのみサポートされています。Xamarin Studio ではサポートされていません。 

### <a name="ios-and-mac"></a>iOS と Mac 

* [iOS 署名ワークフロー更新 ](https://developer.xamarin.com/guides/cross-platform/macios/apple-account-management/) 
    * 署名 ID を作成し、ローカル キーチェーンにインストールします。 
    * プロビジョニング プロファイルを作成します。 
    * 署名 ID を既存のプロファイルに追加します。
    *  プロビジョニング デバイス: Apple Developer Portal でデバイスを登録し、プロビジョニング プロファイルに追加します。
* iOS 11、watchOS 4、tvOS 2 は Visual Studio for Mac でのみサポートされています。Xamarin Studio ではサポートされていません。 
* MacOS High Sierra は Visual Studio for Mac でのみサポートされています。Xamarin Studio ではサポートされていません。 

### <a name="cross-platform"></a>クロス プラットフォーム 

* [Xamarin Live Player](https://developer.xamarin.com/guides/cross-platform/live/) (**プレビュー**) 
* [Xamarin IoT](https://developer.xamarin.com/guides/cross-platform/iot/) (**プレビュー**) 
 