---
title:
- "Visual Studio Community 2017 のワークロード ID とコンポーネント ID | Microsoft Docs"
description: "ワークロード ID とコンポーネント ID を使用して、コマンドラインを使用して Visual Studio をインストールするか、VSIX マニフェストで依存関係として指定します。"
keywords: 
author:
- TerryGLee
ms.author:
- tglee
manager:
- ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 58494fc3-12de-4761-bd4a-74b54f72bfb3
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 9055f1352cce133d853d73d378933ddf8b7e3d78
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-community-2017-workload-and-component-ids"></a>Visual Studio Community 2017 のワークロード ID とコンポーネント ID

このページの表には、コマンドラインを使用して Visual Studio をインストールまたは VSIX マニフェストで依存関係として指定できる、ID の一覧が表示されています。 Visual Studio の更新をリリースするたびに追加コンポーネントを追加します。

また、このページに関して次の点に注意してください。

* ワークロードごとにセクションが分かれており、ワークロード ID と、そのワークロードの使用可能なコンポーネントの表が含まれています。
* 既定では、ワークロードのインストール時に**必須**コンポーネントがインストールされます。 選択した場合は、**推奨**コンポーネントと**オプション** コンポーネントもインストールできます。
* ワークロードに関連付けられていない追加コンポーネントを一覧表示したセクションも追加しました。

VSIX マニフェストで依存関係を設定する際は、コンポーネント ID のみを指定する必要があります。 このページの表を使用して、最小限のコンポーネント依存関係を確認してください。 たとえば、一部のシナリオでは&1; つのワークロードから&1; つのコンポーネントを指定しますが、 他のシナリオでは&1; つのワークロードから複数のコンポーネントを指定したり、複数のワークロードから複数のコンポーネントを指定したりする場合があります。 詳しくは、「[How to: Migrate Extensibility Projects to Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)」 (機能拡張プロジェクトを Visual Studio 2017 に移行する方法) をご覧ください。

これらの ID の使用方法について詳しくは、「[コマンドライン パラメーターを使用して Visual Studio 2017 をインストールする](use-command-line-parameters-to-install-visual-studio.md)」をご覧ください。 その他の製品のワークロードとコンポーネント ID の一覧については、「[Visual Studio 2017 Workload and Component IDs](workload-and-component-ids.md)」(Visual Studio 2017 のワークロード ID とコンポーネント ID) をご覧ください。


## <a name="visual-studio-core-editor-included-with-visual-studio-community-2017"></a>Visual Studio のコア エディター (Visual Studio Community 2017 に付属)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**説明:** 構文認識コード編集機能、ソース コード管理、作業項目管理などの Visual Studio の基本的なシェル エクスペリエンス。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 必須


## <a name="azure-development"></a>Azure の開発

**ID:** Microsoft.VisualStudio.Workload.Azure

**説明:** クラウド アプリの開発とリソースの作成のための Azure SDK、ツール、およびプロジェクト。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.Component.NetFX.Core.Runtime | .NET Core ランタイム | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 必須
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 必須
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 開発の前提条件 | 必須
Component.WebSocket | WebSocket4Net | 推奨
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 推奨
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 推奨
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 推奨
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure コンピューティング エミュレーター | 推奨
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 推奨
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager コア ツール | 推奨
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric Tools | 推奨
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage エミュレーター | 推奨
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services コア ツール | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 推奨
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 推奨
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 推奨
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 推奨
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 推奨
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 推奨
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 推奨
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 推奨
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 推奨
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 推奨
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services ツール | 推奨
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager ツール | 推奨
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | Optional
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell ツール | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional


## <a name="data-storage-and-processing"></a>データ ストレージとデータ処理

**ID:** Microsoft.VisualStudio.Workload.Data

**説明:** SQL Server、Azure Data Lake、Hadoop、または Azure ML を使用してデータ ソリューションの接続、開発、テストを行います。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | 推奨
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | 推奨
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 推奨
Component.WebSocket | WebSocket4Net | 推奨
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | 推奨
Microsoft.Component.MSBuild | MSBuild | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 推奨
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 推奨
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 推奨
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 推奨
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 推奨
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 推奨
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 推奨
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure コンピューティング エミュレーター | 推奨
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage エミュレーター | 推奨
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services コア ツール | 推奨
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 推奨
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 推奨
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 推奨
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 推奨
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 推奨
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 推奨
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 推奨
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 推奨
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 推奨
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 推奨
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 推奨
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 推奨
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 推奨
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 推奨
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | Optional


## <a name="net-desktop-development"></a>.NET デスクトップ開発

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**説明:** .NET Framework を使用して、WPF、Windows フォーム、コンソール アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET デスクトップ開発ツール | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 必須
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 推奨
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 推奨
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 推奨
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | Optional
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 1.0 - 1.1 開発ツール | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャと分析ツール | Optional


## <a name="game-development-with-unity"></a>Unity でのゲーム開発

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**説明:** 高機能なクロスプラットフォーム開発環境である Unity を使用して 2D と 3D のゲームを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 必須
Component.UnityEngine | Unity エディター | 推奨


## <a name="linux-development-with-c"></a>C++ による Linux 開発

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**説明:** Linux 環境で実行するアプリケーションを作成およびデバッグします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.MDD.Linux | Visual C++ for Linux Development | 必須
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 必須
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 必須


## <a name="desktop-development-with-c"></a>C++ によるデスクトップ開発

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**説明:** Visual C++ ツールセットの機能、ATL、および MFC や C++/CLI などのオプション機能を使用して従来の Windows ベースのアプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | 必須
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 必須
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 必須
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 必須
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | C++ 用のアーキテクチャ ツール | 必須
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ コア デスクトップ機能 | 必須
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 推奨
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 推奨
Microsoft.VisualStudio.Component.VC.CMake.Project | CMake の Visual C++ ツール | 推奨
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 推奨
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 推奨
Component.Incredibuild | IncrediBuild | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3 v140 ツールセット (x86、x64) | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (試験的) | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準ライブラリ モジュール | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.WinXP | C++ に関する Windows XP サポート | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | C++ に関する Windows XP サポート | Optional


## <a name="game-development-with-c"></a>C++ によるゲーム開発

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**説明:** C++ を最大限に活用して、DirectX、Unreal、Cocos2d を利用した本格的なゲームをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 必須
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 推奨
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 推奨
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 推奨
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 推奨
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 推奨
Component.Cocos | Cocos | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.Unreal | Unreal Engine のインストーラー | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | Optional


## <a name="mobile-development-with-c"></a>C++ でのモバイル開発

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**説明:** C++ を使用して iOS、Android、または Windows 向けのクロスプラットフォーム アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 必須
Component.Android.NDK.R13B | Android NDK (R13B) | 推奨
Component.Android.SDK19 | Android SDK セットアップ (API レベル 19 および 21) | 推奨
Component.Android.SDK22 | Android SDK セットアップ (API レベル 22) | 推奨
Component.Ant | Apache Ant (1.9.3) | 推奨
Component.MDD.Android | C++ Android 開発ツール | 推奨
Component.Android.Emulator | Visual Studio Emulator for Android | Optional
Component.Android.NDK.R11C | Android NDK (R11C) | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 ビット) | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 ビット) | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 ビット) | Optional
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.Incredibuild | IncrediBuild | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Component.MDD.IOS | C++ iOS 開発ツール | Optional


## <a name="net-core-cross-platform-development"></a>.NET Core クロスプラットフォームの開発

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**説明:** .NET Core、ASP.NET Core、HTML、JavaScript、CSS を使ったクロスプラットフォーム アプリケーションをビルドします

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 必須
Microsoft.VisualStudio.Component.DockerTools | コンテナー開発ツール | 推奨


## <a name="mobile-development-with-net"></a>.NET によるモバイル開発

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**説明:** Xamarin を使用して iOS、Android、または Windows 向けのクロスプラットフォーム アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Component.Android.NDK.R13B | Android NDK (R13B) | 推奨
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | 推奨
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | 推奨
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 推奨
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | 推奨
Component.Xamarin | Xamarin | 推奨
Component.Xamarin.Inspector | Xamarin Workbooks | 推奨
Component.Xamarin.Profiler | Xamarin Profiler | 推奨
Component.Xamarin.RemotedSimulator | Xamarin リモート シミュレーター | 推奨
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 推奨
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | Optional
Microsoft.VisualStudio.Component.Graphics | 画像と 3D モデルのエディター | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile エミュレーター (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャと分析ツール | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Xamarin 用ユニバーサル Windows プラットフォーム ツール (2.0) | Optional


## <a name="aspnet-and-web-development"></a>ASP.NET と Web 開発

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**説明:** ASP.NET、ASP.NET Core、HTML、JavaScript、CSS を使った Web アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 必須
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 開発ツール | 推奨
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 推奨
Microsoft.VisualStudio.Component.DockerTools | コンテナー開発ツール | 推奨
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 推奨
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 推奨
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 推奨
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Optional
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | Optional
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャと分析ツール | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Optional


## <a name="nodejs-development"></a>Node.js 開発

**ID:** Microsoft.VisualStudio.Workload.Node

**説明:** Node.js (非同期イベント ドリブン JavaScript ランタイム) を使用してスケーラブルなネットワーク アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.Node.Tools | Node.js サポート | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 推奨
Microsoft.VisualStudio.Component.Git | Git for Windows | 推奨
Component.WebSocket | WebSocket4Net | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | Optional
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | Optional


## <a name="officesharepoint-development"></a>Office/SharePoint 開発

**ID:** Microsoft.VisualStudio.Workload.Office

**説明:** C#、VB、JavaScript を使用して、Office アドイン、SharePoint アドイン、SharePoint ソリューション、VSTO アドインを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Component.MSBuild | MSBuild | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET デスクトップ開発ツール | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 必須
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 必須
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 必須
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | Optional


## <a name="universal-windows-platform-development"></a>ユニバーサル Windows プラットフォーム開発

**ID:** Microsoft.VisualStudio.Workload.Universal

**説明:** C#、VB、JavaScript、または C++ (オプション) を使ってユニバーサル Windows プラットフォームのアプリケーションを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.WebSocket | WebSocket4Net | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Component.NetFX.Native | .NET Native | 必須
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 必須
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 必須
Microsoft.VisualStudio.Component.Graphics | 画像と 3D モデルのエディター | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Microsoft.VisualStudio.Component.UWP.Support | ユニバーサル Windows プラットフォーム ツール (2.0) | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 必須
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Cordova 用ユニバーサル Windows プラットフォーム ツール (2.0) | 必須
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Xamarin 用ユニバーサル Windows プラットフォーム ツール (2.0) | 必須
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 推奨
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile エミュレーター (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャと分析ツール | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ ユニバーサル Windows プラットフォーム ツール | Optional


## <a name="visual-studio-extension-development"></a>Visual Studio 拡張機能の開発

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**説明:** Visual Studio 用のアドオンや拡張機能 (新しいコマンド、コード アナライザー、ツール ウィンドウを含みます) を作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Publishing | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 必須
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 拡張機能の開発の前提条件 | 必須
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 推奨
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 推奨
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 推奨
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 推奨
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャと分析ツール | 推奨
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Optional
Microsoft.Component.MSBuild | MSBuild | Optional
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | Optional
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | Optional
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | Optional


## <a name="mobile-development-with-javascript"></a>JavaScript でのモバイル開発

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**説明:** Tools for Apache Cordova を使用して Android、iOS、UWP 向けのアプリをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | 依存関係の種類
--- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1 ツールセット | 必須
Component.WebSocket | WebSocket4Net | 必須
Microsoft.VisualStudio.Component.Cordova | JavaScript でのモバイル開発のコア機能 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 必須
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 必須
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Optional
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Optional
Microsoft.Component.ClickOnce | ClickOnce Publishing | Optional
Microsoft.Component.NetFX.Native | .NET Native | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | Optional
Microsoft.VisualStudio.Component.Git | Git for Windows | Optional
Microsoft.VisualStudio.Component.Graphics | 画像と 3D モデルのエディター | Optional
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile エミュレーター (Anniversary Edition) | Optional
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Cordova 用ユニバーサル Windows プラットフォーム ツール (2.0) | Optional
## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはワークロードに含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | 名前
--- | ---
Component.GitHub.VisualStudio | Visual Studio 用の GitHub 拡張機能
Microsoft.Component.Blend.SDK.WPF | Blend for Visual Studio SDK for .NET
Microsoft.Component.HelpViewer | ヘルプ ビューアー
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール
Microsoft.VisualStudio.Component.DependencyValidation.Community | 依存関係検証
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL ツール
Microsoft.VisualStudio.Component.TestTools.Core | テスト ツールのコア機能
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)

