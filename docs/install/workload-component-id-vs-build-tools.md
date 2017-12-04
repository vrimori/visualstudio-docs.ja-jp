---
title: "Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID | Microsoft Docs"
description: "Visual Studio のワークロード ID とコンポーネント ID を使用して Windows ベースのクラシック アプリケーションを構築する"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 10/09/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: 
ms.technology: vs-acquisition
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.openlocfilehash: 4409ca641d35a6276cdbcf48137d48b71b85f58e
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio Build Tools 2017 のコンポーネント ディレクトリ

このページの表では、コマンドラインを使用して Visual Studio をインストールするために使用できる ID の一覧を示します。 Visual Studio の更新プログラムがリリースされる際には、さらにコンポーネントが追加される予定です。

また、このページに関して以下の点に注意してください。

* 各ワークロードに個別のセクションがあり、ワークロード ID と、そのワークロードで利用できるコンポーネントの表が示されています。
* 既定では、ワークロードをインストールすると**必須**コンポーネントがインストールされます。 選択した場合は、**推奨**コンポーネントと**オプション** コンポーネントもインストールできます。
* どのワークロードにも関連付けられていない追加のコンポーネントの一覧を示したセクションも追加しました。

これらの ID の使用方法の詳細については、「[Use Command-Line Parameters to Install Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)」(コマンドライン パラメーターを使用して Visual Studio 2017 をインストールする) をご覧ください。 その他の製品のワークロードとコンポーネント ID の一覧については、「[Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md)」(Visual Studio 2017 のワークロード ID とコンポーネント ID) をご覧ください。

## <a name="msbuild-tools"></a>MSBuild Tools

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**説明:** MSBuild ベースのアプリケーションを構築するために必要なツールを提供します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools のコア | 15.0.26711.1 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# コンパイラ | 15.0.26606.0 | Optional

## <a name="net-core-build-tools"></a>.NET Core ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**説明:** .NET Core アプリケーションを構築するためのツールです。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | .NET Core 1.0 - 1.1 開発ツール | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 デスクトップ用開発ツール | 15.0.26919.1 | Optional

## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**説明:** Visual C++ ツールセットの機能、ATL、および MFC や C++/CLI などのオプション機能を使用して従来の Windows ベースのアプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools のコア機能 | 15.0.26823.1 | 必須
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 再頒布可能パッケージ Update | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26621.2 | 必須
Component.Microsoft.VisualStudio.RazorExtension | Razor 言語サービス | 15.0.26720.2 | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26711.1 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.CMake.Project | CMake の Visual C++ ツール | 15.0.27004.2002 | 推奨
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26823.1 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | デスクトップ用 Windows 10 SDK (10.0.16299.0) C++ [x86 および x64] | 15.0.27004.2002 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP 用 Windows 10 SDK (10.0.16299.0): C#、VB、JS | 15.0.27004.2002 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | UWP 用 Windows 10 SDK (10.0.16299.0): C++ | 15.0.27004.2002 | 推奨
Microsoft.VisualStudio.ComponentGroup.WebToolsExtensions | ASP.NET と Web 開発 | 15.0.26606.0 | 推奨
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.140 | デスクトップ用 VC++ 2015.3 v140 ツールセット (x86、x64) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (試験的) | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | 15.0.26823.1 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準ライブラリ用モジュール (試験段階) | 15.0.26720.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | デスクトップ用 Windows 10 SDK (10.0.15063.0) C++ [x86 および x64] | 15.0.26929.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | UWP 用 Windows 10 SDK (10.0.15063.0): C++ | 15.0.26621.2 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop.arm | デスクトップ用 Windows 10 SDK (10.0.16299.0) C++ [ARM および ARM64] | 15.0.27004.2002 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | 15.0.26208.0 | Optional

## <a name="web-development-build-tools"></a>Web 開発ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**説明:** Web アプリケーションを構築するための MSBuild のタスクとターゲット。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26621.2 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26621.2 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26606.0 | 必須
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 開発ビルド ツール | 15.0.26323.1 | 必須
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26621.2 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26621.2 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26621.2 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26621.2 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26621.2 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 15.0.26606.0 | 推奨
Microsoft.Net.Core.Component.SDK | .NET Core 1.0 - 1.1 開発ツール | 15.0.26606.0 | 推奨
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 推奨
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール | 15.0.26621.2 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | 省略可能
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.0.26621.2 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.0.26606.0 | Optional

## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | 名前 | Version
--- | --- | ---
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | 15.0.26906.1
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64 用 Visual C++ コンパイラとライブラリ | 15.0.26906.1

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
