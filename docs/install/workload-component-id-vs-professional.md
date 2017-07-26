---
title: "Visual Studio Professional 2017 のワークロードとコンポーネント ID | Microsoft Docs"
description: "ワークロードとコンポーネント ID は、コマンド ラインを使用して Visual Studio をインストールするか、または VSIX マニフェストで依存関係として指定するために使用します"
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 05/10/2017
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
ms.assetid: 5719032b-2c2e-416e-a281-a4573ec74e38
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 96a1fa1ef10a02ea85940dd8a0745f1c1d10c326
ms.contentlocale: ja-jp
ms.lasthandoff: 05/13/2017

---

## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2017"></a>Visual Studio のコア エディター (Visual Studio Professional 2017 に付属)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**説明:** 構文認識コード編集機能、ソース コード管理、作業項目管理などの Visual Studio の基本的なシェル エクスペリエンス。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | 必須


## <a name="azure-development"></a>Azure の開発

**ID:** Microsoft.VisualStudio.Workload.Azure

**説明:** クラウド アプリの開発とリソースの作成のための Azure SDK、ツール、およびプロジェクト。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Component.NetFX.Core.Runtime | .NET Core ランタイム | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Azure 開発の前提条件 | 15.0.26323.1 | 必須
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 推奨
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 15.0.26208.0 | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 推奨
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure コンピューティング エミュレーター | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Azure Resource Manager コア ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Service Fabric Tools | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage エミュレーター | 15.0.26424.2 | 推奨
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services コア ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 推奨
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Azure Cloud Services ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Azure Resource Manager ツール | 15.0.26323.1 | 推奨
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | 省略可能
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26419.1 | 省略可能
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | Azure Storage AzCopy | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell ツール | 3.0.427 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Optional


## <a name="data-storage-and-processing"></a>データ ストレージとデータ処理

**ID:** Microsoft.VisualStudio.Workload.Data

**説明:** SQL Server、Azure Data Lake、Hadoop、または Azure ML を使用してデータ ソリューションの接続、開発、テストを行います。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | 1.13.22.3147 | 推奨
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | 7.4.1.767 | 推奨
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | 2.3.10.1131 | 推奨
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 推奨
Microsoft.Component.Azure.DataLake.Tools | Azure Data Lake Tools | 15.0.26208.0 | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 推奨
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 推奨
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure コンピューティング エミュレーター | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage エミュレーター | 15.0.26424.2 | 推奨
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services コア ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 推奨
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 推奨
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 15.0.26208.0 | 省略可能


## <a name="data-science-and-analytical-applications"></a>データ サイエンスと分析のアプリケーション

**ID:** Microsoft.VisualStudio.Workload.DataScience

**説明:** Python、R、F# など、データ サイエンス アプリケーションを作成するための言語とツール。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.Anaconda3.x64 | Anaconda3 64 ビット (4.3.0.1) | 4.3.0.2 | 推奨
Microsoft.Component.CookiecutterTools | cookiecutter テンプレートのサポート | 15.0.26419.1 | 推奨
Microsoft.Component.PythonTools | Python 言語サポート | 15.0.26419.1 | 推奨
Microsoft.Component.PythonTools.Web | Python Web サポート | 15.0.26419.1 | 推奨
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 推奨
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.R.Open | Microsoft R クライアント (3.3.2) | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.RHost | R 開発ツールのランタイム サポート | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.RTools | R 言語サポート | 15.0.26419.1 | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | 推奨
Component.Anaconda2.x64 | Anaconda2 64 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.Anaconda2.x86 | Anaconda2 32 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.Anaconda3.x86 | Anaconda3 32 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python ネイティブ開発ツール | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3 v140 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional


## <a name="net-desktop-development"></a>.NET デスクトップ開発

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**説明:** .NET Framework を使用して、WPF、Windows フォーム、コンソール アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET デスクトップ開発ツール | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26208.0 | 推奨
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | 省略可能
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26419.1 | 省略可能
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.0.26419.1 | 省略可能
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 15.0.26208.0 | Optional
Microsoft.NetCore.ComponentGroup.DevelopmentTools | .NET Core 1.0 - 1.1 開発ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャおよび分析ツール | 15.0.26208.0 | Optional


## <a name="game-development-with-unity"></a>Unity でのゲーム開発

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**説明:** 高機能なクロスプラットフォーム開発環境である Unity を使用して、2D と 3D のゲームを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools for Unity | 15.0.26323.1 | 必須
Component.UnityEngine | Unity 5.6 エディター | 15.0.26430.4 | 推奨


## <a name="linux-development-with-c"></a>C++ による Linux 開発

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**説明:** Linux 環境で実行するアプリケーションを作成およびデバッグします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.MDD.Linux | Visual C++ for Linux Development | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26208.0 | 必須


## <a name="desktop-development-with-c"></a>C++ によるデスクトップ開発

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**説明:** Visual C++ ツールセットの機能、ATL、および MFC や C++/CLI などのオプション機能を使用して従来の Windows ベースのアプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | C++ 用のアーキテクチャ ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Visual C++ コア デスクトップ機能 | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.CMake.Project | CMake の Visual C++ ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | デスクトップ C++ x86 および x64 用 Windows 10 SDK (10.0.15063.0) | 15.0.26403.0 | 推奨
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3 v140 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (試験的) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準ライブラリ モジュール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.WinXP | C++ に関する Windows XP サポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | C++ に関する Windows XP サポート | 15.0.26208.0 | Optional


## <a name="game-development-with-c"></a>C++ によるゲーム開発

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**説明:** C++ を最大限に活用して、DirectX、Unreal、Cocos2d を利用した本格的なゲームをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | デスクトップ C++ x86 および x64 用 Windows 10 SDK (10.0.15063.0) | 15.0.26403.0 | 推奨
Component.Cocos | Cocos | 15.0.26323.1 | Optional
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Optional
Component.Unreal | Unreal Engine のインストーラー | 15.0.26323.1 | Optional
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | 15.0.26208.0 | Optional


## <a name="mobile-development-with-c"></a>C++ でのモバイル開発

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**説明:** C++ を使用して iOS、Android、または Windows 向けのクロスプラットフォーム アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 必須
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | 推奨
Component.Android.SDK19 | Android SDK セットアップ (API レベル 19 および 21) | 15.0.26208.0 | 推奨
Component.Android.SDK22 | Android SDK セットアップ (API レベル 22) | 15.0.26208.0 | 推奨
Component.Ant | Apache Ant (1.9.3) | 1.9.3.7 | 推奨
Component.MDD.Android | C++ Android 開発ツール | 15.0.26208.0 | 推奨
Component.Android.NDK.R11C | Android NDK (R11C) | 11.3.13 | Optional
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 ビット) | 11.3.14 | Optional
Component.Android.NDK.R12B | Android NDK (R12B) | 12.1.9 | Optional
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (32 ビット) | 12.1.9 | Optional
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (32 ビット) | 13.1.6 | Optional
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | 15.0.26208.0 | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | 15.0.26208.0 | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | Optional
Component.Incredibuild | IncrediBuild | 15.0.26228.0 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Optional
Component.MDD.IOS | C++ iOS 開発ツール | 15.0.26208.0 | Optional


## <a name="net-core-cross-platform-development"></a>.NET Core クロスプラットフォームの開発

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**説明:** .NET Core、ASP.NET Core、HTML、JavaScript、CSS を使ったクロスプラットフォーム アプリケーションをビルドします

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.DockerTools | コンテナー開発ツール | 15.0.26323.1 | 推奨


## <a name="mobile-development-with-net"></a>.NET によるモバイル開発

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**説明:** Xamarin を使用して iOS、Android、または Windows 向けのクロスプラットフォーム アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Component.Android.NDK.R13B | Android NDK (R13B) | 13.1.6 | 推奨
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | 15.0.26208.0 | 推奨
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | 15.0.26208.0 | 推奨
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | 推奨
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | 推奨
Component.Xamarin | Xamarin | 15.0.26424.2 | 推奨
Component.Xamarin.Inspector | Xamarin Workbooks | 15.0.26228.0 | 推奨
Component.Xamarin.Profiler | Xamarin Profiler | 15.0.26228.0 | 推奨
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | 15.0.26228.0 | 推奨
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 推奨
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | イメージ エディターと 3D モデル エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile エミュレーター (Creators Update) | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャおよび分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Xamarin 用ユニバーサル Windows プラットフォーム ツール | 15.0.26403.0 | Optional


## <a name="aspnet-and-web-development"></a>ASP.NET と Web 開発

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**説明:** ASP.NET、ASP.NET Core、HTML、JavaScript、CSS を使った Web アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.Net.Core.Component.SDK | .NET Core 1.0.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.NetCore.ComponentGroup.Web | .NET Core 1.0 - 1.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | 推奨
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DockerTools | コンテナー開発ツール | 15.0.26323.1 | 推奨
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 Tools | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | 推奨
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.7.SDK | .NET Framework 4.7 SDK | 15.0.26419.1 | 省略可能
Microsoft.Net.Component.4.7.TargetingPack | .NET Framework 4.7 Targeting Pack | 15.0.26419.1 | 省略可能
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | .NET Framework 4.6.2 開発ツール | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.4.7.DeveloperTools | .NET Framework 4.7 開発ツール | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.FSharp | F# 言語サポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャおよび分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | 15.0.26208.0 | Optional


## <a name="nodejs-development"></a>Node.js 開発

**ID:** Microsoft.VisualStudio.Workload.Node

**説明:** Node.js (非同期イベント ドリブン JavaScript ランタイム) を使用してスケーラブルなネットワーク アプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.Node.Tools | Node.js サポート | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 推奨
Microsoft.VisualStudio.Component.Git | Git for Windows | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | Optional


## <a name="officesharepoint-development"></a>Office/SharePoint 開発

**ID:** Microsoft.VisualStudio.Workload.Office

**説明:** C#、VB、JavaScript を使用して、Office アドイン、SharePoint アドイン、SharePoint ソリューション、VSTO アドインを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 必須
Microsoft.VisualStudio.Component.Debugger.JustInTime | Just-In-Time デバッガー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 必須
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | .NET デスクトップ開発ツール | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools for Visual Studio | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools for Office (VSTO) | 15.0.26228.0 | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 省略可能


## <a name="python-development"></a>Python 開発

**ID:** Microsoft.VisualStudio.Workload.Python

**説明:** Python の編集、デバッグ、対話型開発、ソース管理。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.CPython3.x64 | Python 3 64 ビット (3.6.0) | 3.6.0 | 推奨
Microsoft.Component.CookiecutterTools | cookiecutter テンプレートのサポート | 15.0.26419.1 | 推奨
Microsoft.Component.PythonTools | Python 言語サポート | 15.0.26419.1 | 推奨
Microsoft.Component.PythonTools.Web | Python Web サポート | 15.0.26419.1 | 推奨
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Common.Azure.Tools | 接続および発行ツール | 1.9.170119.3 | 推奨
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.WebDeploy | Web 配置 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | 推奨
Component.Anaconda2.x64 | Anaconda2 64 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.Anaconda2.x86 | Anaconda2 32 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.Anaconda3.x64 | Anaconda3 64 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.Anaconda3.x86 | Anaconda3 32 ビット (4.3.0.1) | 4.3.0.2 | 省略可能
Component.CPython2.x64 | Python 2 64 ビット (2.7.13) | 2.7.13 | 省略可能
Component.CPython2.x86 | Python 2 32 ビット (2.7.13) | 2.7.13 | 省略可能
Component.CPython3.x86 | Python 3 32 ビット (3.6.0) | 3.6.0.1 | 省略可能
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 省略可能
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 省略可能
Microsoft.Component.PythonTools.UWP | Python IoT サポート | 15.0.26419.1 | 省略可能
Microsoft.ComponentGroup.PythonTools.NativeDevelopment | Python ネイティブ開発ツール | 15.0.26419.1 | 省略可能
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | Optional
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 - 4.6 開発ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 省略可能
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Azure Authoring Tools | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.Azure.ClientLibs | .NET 用 Azure ライブラリ | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Azure コンピューティング エミュレーター | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Azure Storage エミュレーター | 15.0.26424.2 | 省略可能
Microsoft.VisualStudio.Component.Azure.Waverton | Azure Cloud Services コア ツール | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio のコア エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | イメージ エディターと 3D モデル エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 省略可能
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Managed Desktop Workload コア | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL ランタイム | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server コマンド ライン ユーティリティ | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server サポートのためのデータ ソース | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 省略可能
Microsoft.VisualStudio.Component.VC.140 | VC++ 2015.3 v140 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.VC.DiagnosticTools | C++ のプロファイル ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | 省略可能
Microsoft.VisualStudio.Component.Web | ASP.NET と Web の開発ツール | 15.0.26323.1 | 省略可能
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional


## <a name="universal-windows-platform-development"></a>ユニバーサル Windows プラットフォーム開発

**ID:** Microsoft.VisualStudio.Workload.Universal

**説明:** C#、VB、JavaScript、または C++ (オプション) を使ってユニバーサル Windows プラットフォームのアプリケーションを作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | 必須
Microsoft.ComponentGroup.Blend | Blend for Visual Studio | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Graphics | イメージ エディターと 3D モデル エディター | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Microsoft.VisualStudio.Component.UWP.Support | ユニバーサル Windows プラットフォーム ツール | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.0.26419.1 | 必須
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Cordova 用ユニバーサル Windows プラットフォーム ツール | 15.0.26403.0 | 必須
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Xamarin 用ユニバーサル Windows プラットフォーム ツール | 15.0.26403.0 | 必須
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 推奨
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Tools | DirectX 用グラフィックス デバッガーおよび GPU プロファイラー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics.Win81 | グラフィックス ツール Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile エミュレーター (Creators Update) | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM 用 Visual C++ コンパイラとライブラリ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP.Native | UWP 用 Windows 10 SDK (10.0.15063.0): C++ | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャおよび分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.UWP.VC | C++ ユニバーサル Windows プラットフォーム ツール | 15.0.26403.0 | Optional


## <a name="visual-studio-extension-development"></a>Visual Studio 拡張機能の開発

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**説明:** Visual Studio 用のアドオンや拡張機能 (新しいコマンド、コード アナライザー、ツール ウィンドウを含む) を作成します。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | 必須
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | 必須
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 開発ツール | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.NuGet | NuGet パッケージ マネージャー | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.PortableLibrary | .NET ポータブル ライブラリ Targeting Pack | 15.0.26208.0 | 必須
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Visual Studio 拡張機能の開発の前提条件 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.CodeClone | コード クローン | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.CodeMap | コード マップ | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | ライブ依存関係検証 | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.GraphDocument | DGML エディター | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | [IntelliTrace] | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | アーキテクチャおよび分析ツール | 15.0.26208.0 | 推奨
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | 15.0.26208.0 | Optional
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Optional
Microsoft.Component.VC.Runtime.OSSupport | UWP 用の Visual C++ ランタイム | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Optional
Microsoft.VisualStudio.Component.ClassDesigner | クラス デザイナー | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# および Visual Basic | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.TextTemplating | テキスト テンプレート変換 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | 15.0.26208.0 | Optional


## <a name="mobile-development-with-javascript"></a>JavaScript でのモバイル開発

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**説明:** Tools for Apache Cordova を使用して Android、iOS、UWP 向けのアプリをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Component.CordovaToolset.6.3.1 | Cordova 6.3.1 ツールセット | 15.0.26323.1 | 必須
Component.WebSocket | WebSocket4Net | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Cordova | JavaScript でのモバイル開発のコア機能 | 15.0.26323.1 | 必須
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | JavaScript 診断 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.JavaScript.TypeScript | JavaScript および TypeScript の言語サポート | 15.0.26412.1 | 必須
Microsoft.VisualStudio.Component.TypeScript.2.2 | TypeScript 2.2 SDK | 15.0.26430.1 | 必須
Component.Android.SDK23 | Android SDK セットアップ (API レベル 23) | 15.0.26208.0 | Optional
Component.Google.Android.Emulator.API23.V2 | Google Android エミュレーター (API レベル 23) | 15.0.26208.0 | Optional
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | 15.0.26208.0 | Optional
Component.JavaJDK | Java SE Development Kit (8.0.1120.15) | 15.0.26403.0 | Optional
Microsoft.Component.ClickOnce | ClickOnce Publishing | 15.0.26208.0 | Optional
Microsoft.Component.NetFX.Native | .NET Native | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | 15.0.26323.1 | Optional
Microsoft.VisualStudio.Component.DiagnosticTools | プロファイリング ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Git | Git for Windows | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Graphics | イメージ エディターと 3D モデル エディター | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Phone.Emulator.15063 | Windows 10 Mobile エミュレーター (Creators Update) | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server の CLR データ型 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VisualStudioData | データソースとサービス参照 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.15063.UWP | UWP 用 Windows 10 SDK (10.0.15063.0): C#、VB、JS | 15.0.26419.1 | 省略可能
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Cordova 用ユニバーサル Windows プラットフォーム ツール | 15.0.26403.0 | Optional
## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | 名前 | バージョン
--- | --- | ---
Component.Android.Emulator | Visual Studio Emulator for Android | 15.0.26430.1
Component.GitHub.VisualStudio | Visual Studio 用の GitHub 拡張機能 | 2.2.0.10
Microsoft.Component.Blend.SDK.WPF | Blend for Visual Studio SDK for .NET | 15.0.26208.0
Microsoft.Component.HelpViewer | ヘルプ ビューアー | 15.0.26208.0
Microsoft.Net.Component.3.5.DeveloperTools | .NET Framework 3.5 開発ツール | 15.0.26208.0
Microsoft.VisualStudio.Component.DependencyValidation.Community | 依存関係検証 | 15.0.26208.0
Microsoft.VisualStudio.Component.LinqToSql | LINQ to SQL ツール | 15.0.26208.0
Microsoft.VisualStudio.Component.Phone.Emulator | Windows 10 Mobile エミュレーター (Anniversary Edition) | 15.0.26208.0
Microsoft.VisualStudio.Component.TestTools.Core | テスト ツールのコア機能 | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK | 15.0.26208.0
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | 15.0.26208.0

## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)

