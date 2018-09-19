---
title: コード分析の FxCop と FxCop アナライザー
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e05dd0e01254bf1222a8a7de497b11ec2a808bfb
ms.sourcegitcommit: b9a32c3d94b19e7344f4872bc026efd3157cf220
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46136368"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop と FxCop についてよく寄せられる質問のアナライザー

従来の FxCop および FxCop の違いについて理解することは困難を少しアナライザーです。 この記事では、質問があるの一部に対処する目的としています。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>従来の FxCop と FxCop の違いはアナライザーですか?

レガシ FxCop はコンパイル済みアセンブリのビルド後の分析を実行します。 呼ばれる独立した実行可能ファイルとして実行される**FxCopCmd.exe**します。 FxCopCmd.exe のコンパイル済みのアセンブリを読み込み、コードの分析の実行、および結果をレポートします (または*診断*)。

FxCop アナライザーは、.NET コンパイラ プラットフォーム ("Roslyn") に基づいています。 [NuGet パッケージとしてインストール](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)プロジェクトまたはソリューションによって参照されます。 コンパイラの実行中に、ベースの分析を FxCop アナライザーをソース コードを実行します。 FxCop アナライザーがいずれかのコンパイラのプロセス内でホストされる**csc.exe**または**vbc.exe**、およびプロジェクトのビルド時に、分析を実行します。 アナライザーの結果は、コンパイラの結果と共に報告されます。

> [!NOTE]
> できます[FxCop アナライザーを Visual Studio 拡張機能としてインストール](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)します。 この場合、コード エディターで入力することがビルド時に実行しない同様に、アナライザーが実行されます。 継続的インテグレーション (CI) の一部として FxCop アナライザーを実行する場合は、代わりに、NuGet パッケージとしてインストールします。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>コード分析の実行コマンドは、FxCop アナライザーを実行しますか。

いいえ。 選択すると**分析** > **コード分析を実行**Visual Studio 2017 では、静的コード分析またはレガシ FxCop を実行します。 **コード分析を実行**Roslyn ベースの FxCop アナライザーを含む、Roslyn ベースのアナライザーの影響を与えません。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild プロジェクトのプロパティは、アナライザーを実行しますか。

いいえ。 **RunCodeAnalysis**プロジェクト ファイルのプロパティ (たとえば、 *.csproj*) はレガシ FxCop の実行にのみ使用します。 起動するビルド後の msbuild タスクを実行**FxCopCmd.exe**します。 選択するのと同じ**分析** > **コード分析を実行**Visual Studio でします。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>どのように実行 FxCop アナライザーからでしょうか。

FxCop アナライザーを最初に実行する[NuGet パッケージをインストール](install-fxcop-analyzers.md)にします。 Visual Studio または msbuild を使用してから、プロジェクトまたはソリューションをビルドします。 FxCop アナライザーによって生成されたエラーおよび警告が表示されます、**エラー一覧**またはコマンド ウィンドウ。

## <a name="see-also"></a>関連項目

- [.NET コンパイラ プラットフォームのアナライザーの概要](roslyn-analyzers-overview.md)
- [アナライザーを概要します。](fxcop-analyzers.yml)
- [FxCop アナライザーをインストールします。](install-fxcop-analyzers.md)
