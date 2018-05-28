---
title: Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID
description: Visual Studio のワークロード ID とコンポーネント ID を使用して Windows ベースのクラシック アプリケーションを構築する
keywords: ''
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 05/07/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.service: ''
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
ms.workload:
- multiple
ms.openlocfilehash: 8634017862a12b3a399f003d6f16c9689b7aaa20
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="visual-studio-build-tools-2017-component-directory"></a>Visual Studio Build Tools 2017 のコンポーネント ディレクトリ

このページの表では、コマンド ラインを使用して Visual Studio をインストールするか、VSIX マニフェストで依存関係として指定するために使用できる ID の一覧を示します。 Visual Studio の更新プログラムがリリースされる際には、さらにコンポーネントが追加される予定です。

また、このページに関して以下の点に注意してください。

* 各ワークロードに個別のセクションがあり、ワークロード ID と、そのワークロードで利用できるコンポーネントの表が示されています。
* 既定では、ワークロードをインストールすると**必須**コンポーネントがインストールされます。
* 選択した場合は、**推奨**コンポーネントと**オプション** コンポーネントもインストールできます。
* どのワークロードにも関連付けられていない追加のコンポーネントの一覧を示したセクションも追加しました。

VSIX マニフェストで依存関係を設定するときは、コンポーネント ID のみを指定する必要があります。 このページの表を使用して、コンポーネントの最小の依存関係を確認してください。 シナリオによって、1 つのワークロードの 1 つのコンポーネントだけを指定する場合もあれば、 1 つのワークロードの複数のコンポーネントを指定したり、複数のワークロードの複数のコンポーネントを指定したりする場合もあります。 詳しくは、「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (機能拡張プロジェクトを Visual Studio 2017 に移行する方法) をご覧ください。

これらの ID の使用方法の詳細については、「[Use Command-Line Parameters to Install Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)」(コマンドライン パラメーターを使用して Visual Studio 2017 をインストールする) をご覧ください。 その他の製品のワークロードとコンポーネント ID の一覧については、「[Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md)」(Visual Studio 2017 のワークロード ID とコンポーネント ID) をご覧ください。

## <a name="azure-development-build-tools"></a>Azure 開発ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.AzureBuildTools

**説明:** Azure アプリケーションを構築するための MSBuild のタスクとターゲット。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.7.27520.0 | 必須
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.0.26621.2 | 必須
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Azure.Waverton.BuildTools | Azure Cloud Services ビルド ツール | 15.7.27617.1 | 必須
Microsoft.VisualStudio.Component.DockerTools.BuildTools | コンテナーの開発ツール - Build Tools | 15.7.27617.1 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 開発ビルド ツール | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 開発ビルド ツール | 15.7.27604.0 | 必須
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 15.6.27406.0 | 推奨
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開発ツール | 15.6.27406.0 | 推奨
Microsoft.VisualStudio.Component.AspNet45 | 高度な ASP.NET 機能 | 15.7.27625.0 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | 推奨
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.6.27406.0 | Optional

## <a name="net-desktop-build-tools"></a>.NET デスクトップ ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools

**説明:** C#、Visual Basic、F# を使用して、WPF、Windows フォーム、コンソール アプリケーションをビルドするためのツール。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.6.27309.0 | 必須
Microsoft.Component.ClickOnce.MSBuild | ClickOnce ビルド ツール | 15.7.27617.1 | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 15.6.27406.0 | 推奨
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開発ツール | 15.6.27406.0 | 推奨
Microsoft.VisualStudio.Component.TestTools.BuildTools | ツールのコア機能のテスト - Build Tools | 15.7.27625.0 | 推奨
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 開発ビルド ツール | 15.6.27309.0 | 推奨
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開発ツール | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.FSharp.MSBuild | F# コンパイラ | 15.7.27604.0 | Optional

## <a name="msbuild-tools"></a>MSBuild Tools

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**説明:** MSBuild ベースのアプリケーションを構築するために必要なツールを提供します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必須
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools のコア | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.6.27309.0 | 必須

## <a name="net-core-build-tools"></a>.NET Core ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.NetCoreBuildTools

**説明:** .NET Core、ASP.NET Core、HTML/JavaScript、コンテナーを使用してアプリケーションをビルドするためのツール。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開発ツール | 15.6.27406.0 | 必須
Microsoft.NetCore.BuildTools.ComponentGroup | .NET Core ビルド ツール | 15.7.27617.1 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開発ツール | 15.6.27406.0 | Optional

## <a name="nodejs-build-tools"></a>Node.js ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.NodeBuildTools

**説明:** Node.js (非同期イベント ドリブン JavaScript ランタイム) を使用してスケーラブルなネットワーク アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Node.Build | Node.js サポート | 15.6.27406.0 | 必須

## <a name="officesharepoint-build-tools"></a>Office/SharePoint ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.OfficeBuildTools

**説明:** Office アドイン、SharePoint アドイン、VSTO アドインをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.ClickOnce.MSBuild | ClickOnce ビルド ツール | 15.7.27617.1 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.7.27520.0 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Component.Sharepoint.BuildTools | Office/SharePoint 開発ビルド ツール | 15.7.27617.1 | 必須
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 開発ビルド ツール | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 開発ビルド ツール | 15.7.27604.0 | 必須
Microsoft.VisualStudio.Component.TeamOffice.BuildTools | Visual Studio Tools for Office (VSTO) ビルド ツール | 15.7.27617.1 | 推奨
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.6.27406.0 | Optional

## <a name="universal-windows-platform-build-tools"></a>ユニバーサル Windows プラットフォーム ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.UniversalBuildTools

**説明:** ユニバーサル Windows プラットフォーム アプリケーションをビルドするために必要なツールを提供します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必須
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 必須
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.6.27309.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 バージョン 15.7 v14.14 最新の v141 ツール | 15.7.27625.0 | 必須
Microsoft.VisualStudio.ComponentGroup.UWP.BuildTools | ユニバーサル Windows プラットフォーム ビルドの前提条件 | 15.7.27703.1 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP 用 Windows 10 SDK (10.0.16299.0): C#、VB、JS | 15.6.27406.0 | Optional

## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**説明:** Microsoft C++ ツールセット、ATL、MFC を使用して Windows のデスクトップ アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools のコア機能 | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.VC.Redist.14.Latest | Visual C++ 2017 再頒布可能パッケージ Update | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 バージョン 15.7 v14.14 最新の v141 ツール | 15.7.27625.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.TestTools.BuildTools | ツールのコア機能のテスト - Build Tools | 15.7.27625.0 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK (10.0.17134.0) | 15.7.27703.1 | 推奨
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.6.27309.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | デスクトップ用 VC++ 2015.3 v14.00 (v140) ツールセット | 15.7.27617.1 | Optional
Microsoft.VisualStudio.Component.VC.ATL | x86 用と x64 用の Visual C++ ATL | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | x86 用と x64 用の Visual C++ MFC | 15.7.27625.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準ライブラリ用モジュール (試験段階) | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64 用 Visual C++ コンパイラとライブラリ | 15.6.27309.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | デスクトップ用 Windows 10 SDK (10.0.15063.0) C++ [x86 および x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | UWP 用 Windows 10 SDK (10.0.15063.0): C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.Desktop | デスクトップ用 Windows 10 SDK (10.0.16299.0) C++ [x86 および x64] | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP | UWP 用 Windows 10 SDK (10.0.16299.0): C#、VB、JS | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.16299.UWP.Native | UWP 用 Windows 10 SDK (10.0.16299.0): C++ | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.Component.WinXP | C++ に関する Windows XP サポート | 15.7.27703.1 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | 15.6.27406.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | C++ に関する Windows XP サポート | 15.7.27703.1 | Optional

## <a name="web-development-build-tools"></a>Web 開発ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**説明:** Web アプリケーションを構築するための MSBuild のタスクとターゲット。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.7.27520.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 開発ビルド ツール | 15.7.27604.0 | 必須
Microsoft.Component.ClickOnce.MSBuild | ClickOnce ビルド ツール | 15.7.27617.1 | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.6.27406.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 15.6.27406.0 | 推奨
Microsoft.Net.Core.Component.SDK | .NET Core 2.0 開発ツール | 15.6.27406.0 | 推奨
Microsoft.VisualStudio.Component.AspNet45 | 高度な ASP.NET 機能 | 15.7.27625.0 | 推奨
Microsoft.VisualStudio.Component.DockerTools.BuildTools | コンテナーの開発ツール - Build Tools | 15.7.27617.1 | 推奨
Microsoft.VisualStudio.Component.TestTools.BuildTools | ツールのコア機能のテスト - Build Tools | 15.7.27625.0 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.8 | TypeScript 2.8 SDK | 15.0.27617.1 | 推奨
Microsoft.VisualStudio.Wcf.BuildTools.ComponentGroup | WCF 開発ビルド ツール | 15.6.27309.0 | 推奨
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.SDK | .NET Framework 4.7.1 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.1.TargetingPack | .NET Framework 4.7.1 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.6.27406.0 | Optional
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.1.DeveloperTools | .NET Framework 4.7.1 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.6.27406.0 | Optional
Microsoft.Net.Core.Component.SDK.1x | .NET Core 1.0 - 1.1 開発ツール | 15.6.27406.0 | Optional

## <a name="mobile-development-with-net"></a>.NET によるモバイル開発

**ID:** Microsoft.VisualStudio.Workload.XamarinBuildTools

**説明:** C# および F# を使用して iOS、Android、Windows のクロスプラットフォーム アプリケーションをビルドするためのツール。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | name | Version | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.6.27406.0 | 必須
Microsoft.VisualStudio.Component.NuGet.BuildTools | NuGet ターゲットとビルド タスク | 15.0.26919.1 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.6.27309.0 | 必須
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.6.27406.0 | 推奨
Component.Android.SDK25 | Android SDK セットアップ (API レベル 25) | 15.6.27413.0 | Optional

## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | name | Version
--- | --- | ---
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.3 | TypeScript 2.3 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.5 | TypeScript 2.5 SDK | 15.6.27406.0
Microsoft.VisualStudio.Component.TypeScript.2.6 | TypeScript 2.6 SDK | 15.0.27520.0
Microsoft.VisualStudio.Component.VC.ATL.ARM | ARM 用 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM.Spectre | Spectre の軽減策を含む ARM 用 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64 | ARM64 用 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.ARM64.Spectre | Spectre の軽減策を含む ARM64 用 Visual C++ ATL | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATL.Spectre | Spectre の軽減策を含む Visual C++ ATL (x86 または x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ATLMFC.Spectre | Spectre の軽減策を含む x86 または x64 用 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (試験的) | 15.7.27520.0
Microsoft.VisualStudio.Component.VC.MFC.ARM | ARM 用 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM.Spectre | Spectre の軽減策を含む ARM 用 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64 | ARM64 用 Visual C++ MFC | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.MFC.ARM64.Spectre | Spectre の軽減策を含む ARM64 用 Visual C++ MFC サポート | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM.Spectre | VC++ 2017 バージョン 15.7 v14.14 Spectre 用ライブラリ (ARM) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.ARM64.Spectre | VC++ 2017 バージョン 15.7 v14.14 Spectre 用ライブラリ (ARM64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Runtimes.x86.x64.Spectre | VC++ 2017 バージョン 15.7 v14.14 Spectre 用ライブラリ (x86 および x64) | 15.7.27625.0
Microsoft.VisualStudio.Component.VC.Tools.14.11 | VC++ 2017 バージョン 15.4 v14.11 ツールセット | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.12 | VC++ 2017 バージョン 15.5 v14.12 ツールセット | 15.0.27406.0
Microsoft.VisualStudio.Component.VC.Tools.14.13 | VC++ 2017 バージョン 15.6 v14.13 ツールセット | 15.0.27625.0

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)
