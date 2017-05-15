---
title: "Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID | Microsoft Docs"
description: "Visual Studio のワークロード ID とコンポーネント ID を使用して Windows ベースのクラシック アプリケーションを構築する"
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
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.sourcegitcommit: 054126ddbdc9f0144983a1ef21fa43875699cbee
ms.openlocfilehash: 1147438d12d754233f6205de4a5d37920cb5b66a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

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
Microsoft.VisualStudio.Component.CoreBuildTools | Visual Studio Build Tools のコア | 15.0.26228.0 | 必須
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# および Visual Basic Roslyn コンパイラ | 15.0.26208.0 | 必須


## <a name="visual-c-build-tools"></a>Visual C++ Build Tools

**ID:** Microsoft.VisualStudio.Workload.VCTools

**説明:** Visual C++ ツールセットの機能、ATL、および MFC や C++/CLI などのオプション機能を使用して従来の Windows ベースのアプリケーションをビルドします。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Visual C++ Build Tools のコア機能 | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.Windows10SDK | Windows ユニバーサル C ランタイム | 15.0.26208.0 | 必須
Microsoft.VisualStudio.Component.VC.CMake.Project | CMake の Visual C++ ツール | 15.0.26208.0 | 推奨
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | デスクトップ C++ x86 および x64 用 Windows 10 SDK (10.0.15063.0) | 15.0.26403.0 | 推奨
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Optional
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Static.Analysis.Tools | スタティック分析ツール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATL | Visual C++ ATL のサポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ATLMFC | MFC と ATL のサポート (x86 と x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (試験的) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI サポート | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.CoreIde | Visual Studio C++ コア機能 | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | 標準ライブラリ モジュール | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | VC++ 2017 v141 ツールセット (x86、x64) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Optional
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Optional
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK と UCRT SDK | 15.0.26208.0 | Optional


## <a name="web-development-build-tools"></a>Web 開発ビルド ツール

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**説明:** Web アプリケーションを構築するための MSBuild のタスクとターゲット。

### <a name="components-included-by-this-workload"></a>このワークロードに含まれるコンポーネント

コンポーネント ID | 名前 | バージョン | 依存関係の種類
--- | --- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Web 開発ビルド ツール | 15.0.26323.1 | 必須
## <a name="unaffiliated-components"></a>関連付けられていないコンポーネント

以下のコンポーネントはどのワークロードにも含まれていませんが、個別のコンポーネントとして選択できます。

コンポーネント ID | 名前 | バージョン
--- | --- | ---
適用なし | 該当なし | 適用なし


## <a name="see-also"></a>関連項目

* [Visual Studio のワークロードとコンポーネント ID](workload-and-component-ids.md)
* [Visual Studio 管理者ガイド](visual-studio-administrator-guide.md)
* [コマンド ライン パラメーターを使用して Visual Studio をインストールする](use-command-line-parameters-to-install-visual-studio.md)
  * [コマンド ライン パラメーターの例](command-line-parameter-examples.md)
* [Visual Studio のオフライン インストールを作成する](create-an-offline-installation-of-visual-studio.md)

