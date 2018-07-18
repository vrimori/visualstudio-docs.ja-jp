---
title: Visual Studio for Mac ツアー
description: Visual Studio for Mac は、iOS、Android、Mac、Xamarin.Forms 用に、ASP.NET Core Web サイトや Xamarin プロジェクトなどの .NET アプリケーションを macOS 上で構築する統合開発環境 (IDE) として利用できます。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: 024e58c1c217652c489ad9fe9e568cd21f687ae8
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34453990"
---
# <a name="visual-studio-for-mac-tour"></a>Visual Studio for Mac ツアー

Visual Studio for Mac は、Xamarin のモバイルを中心とした IDE である Xamarin Studio を、Mac 上のモバイル優先、クラウド優先の開発環境へと進化させました。 この開発者向けツールから .NET の機能を使用して、対象ユーザーに必要なすべてのプラットフォーム用アプリケーションを作成できます。

Visual Studio for Mac のユーザー エクスペリエンス (UX) は Windows 版と似ていますが、ネイティブ macOS の操作感もあります。 Windows で Visual Studio を使用したことがあれば、使い慣れた方法でアプリの作成、起動、開発を行うことができます。 また、Visual Studio for Mac は、Windows 版を強力な IDE にしている強力なツールの多くを採用しています。 Roslyn コンパイラ プラットフォームは、リファクタリングと IntelliSense に使用されます。 そのプロジェクト システムとビルド エンジンは MSBuild を使用し、ソース エディターは TextMate バンドルをサポートしています。 Xamarin アプリと .NET Core アプリに同じデバッグ エンジンを使用し、Xamarin.iOS と Xamarin.Android に同じデザイナーを使用しています。

この記事では、Visual Studio for Mac の多様なセクションについて説明し、クロスプラットフォーム アプリケーションを作成する場合に強力なツールになる機能の一部を紹介します。

## <a name="ide-tour"></a>IDE ツアー

Visual Studio for Mac は、アプリケーションのファイルと設定の管理、アプリケーション ノードの作成、およびデバッグのセクションに分かれています。

## <a name="welcome-screen"></a>ようこそ画面

Visual Studio for Mac を起動すると、*ようこそ画面*が表示されます。

![ようこそ画面](media/ide-tour-image1.png)

ようこそ画面には次のセクションが含まれています。

- **ツールバー** - 検索バーにすばやくアクセスできます。 ソリューションを読み込むときに、ツールバーを使用して、アプリ構成の設定、デバッグ、およびエラーの表示を行います。
- **はじめに** - Visual Studio for Mac を初めて使用する開発者に役立つトピックにすばやくアクセスできます。
- **最近のソリューション** - 最近開いたソリューションにすばやくアクセスできます。また、プロジェクトを開いたり作成したりできる便利なボタンも表示されます。
- **開発者向け情報** - Microsoft 開発者向けの最新情報を提供するニュース フィードです。

## <a name="solutions-and-projects"></a>ソリューションおよびプロジェクト

次の図は、アプリケーションが読み込まれた Visual Studio for Mac を示しています。

![アプリケーションが読み込まれた Visual Studio for Mac](media/ide-tour-image17.png)

以下のセクションでは、Visual Studio for Mac の主な領域について概要を説明します。

## <a name="solution-pad"></a>Solution Pad

Solution Pad では、ソリューション内のプロジェクトが整理されています。

![Solution Pad に整理されているプロジェクト](media/ide-tour-image18.png)

これは、ソース コード、リソース、ユーザー インターフェイス、および依存関係のファイルが、プラットフォーム固有のプロジェクトに整理されている場所です。

Visual Studio for Mac でプロジェクトとソリューションを使用する方法の詳細については、「[プロジェクトおよびソリューション](projects-and-solutions.md)」を参照してください。

## <a name="assembly-references"></a>アセンブリ参照
 
各プロジェクトのアセンブリ参照は、[参照] フォルダーの下に表示されます。

![Solution Pad の [参照] フォルダー](media/ide-tour-image19.png)

その他の参照は、**[参照の編集]** ダイアログを使用して追加されます。このダイアログを表示するには、[参照] フォルダーをダブルクリックするか、コンテキスト メニュー操作で **[参照の編集]** を選択します。
 
![[参照の編集] ダイアログ](media/ide-tour-image20.png)

Visual Studio for Mac で参照を使用する方法については、「[プロジェクト内の参照の管理](managing-references-in-a-project.md)」を参照してください。

## <a name="dependencies--packages"></a>依存関係/パッケージ

アプリで使用されるすべての外部依存関係は、[依存関係] フォルダーまたは [パッケージ] フォルダーに格納されます。格納される場所は、.NET Core プロジェクトか Xamarin.iOS/Xamarin.Android プロジェクトかによって変わります。 通常、NuGet の形式で提供されます。

NuGet は、.NET 開発用の最も人気のあるパッケージ マネージャーです。 Visual Studio は NuGet をサポートしているので、簡単にパッケージを検索し、プロジェクトをアプリケーションに追加できます。

依存関係をアプリケーションに追加するには、[依存関係]/[パッケージ] フォルダーを右クリックし、**[パッケージの追加]** を選択します。

![NuGet パッケージの追加](media/ide-tour-image21.png)

アプリケーションで NuGet パッケージを使用する方法については、「[プロジェクトに NuGet パッケージを含める](nuget-walkthrough.md)」を参照してください。

## <a name="refactoring"></a>リファクタリング

Visual Studio for Mac には、コンテキスト アクションとソース分析という、コードをリファクターする 2 つの便利な方法があります。 詳細については、「[リファクタリング](refactoring.md)」を参照してください。

## <a name="debugging"></a>デバッグ

Visual Studio for Mac には、Xamarin.iOS、Xamarin.Mac、Xamarin.Android アプリケーションのデバッグをサポートするネイティブ デバッガーが備わっています。 Visual Studio for Mac では、IDE ですべてのプラットフォームでマネージ コードをデバッグするために、Mono ランタイムに実装されている Mono Soft Debugger を使用しています。 デバッグの詳細については、「[Xamarin を使ったデバッグ](debugging.md)」を参照してください。

デバッガーには、文字列、色、URL だけでなく、サイズ、座標、ベジエ曲線などの特殊な種類の高機能なビジュアライザーが含まれています。

デバッガーのデータの視覚化の詳細については、「[データの視覚化](data-visualizations.md)」を参照してください。

## <a name="version-control"></a>バージョン コントロール

Visual Studio for Mac は、Git と Subversion ソース管理システムと統合されています。 ソース管理下にあるプロジェクトは、ソリューション名の横にブランチとして一覧表示されます。 

![ソース管理下にあるプロジェクトを示すブランチ名](media/ide-tour-image22.png)

コミットされていない変更があるファイルは、次の図に示すように、ソリューション ウィンドウにアイコンで示されます。

![Solution Pad のコミットされていないファイル](media/ide-tour-image23.png)

Visual Studio でバージョン管理を使用する方法については、「[バージョン管理](version-control.md)」を参照してください。