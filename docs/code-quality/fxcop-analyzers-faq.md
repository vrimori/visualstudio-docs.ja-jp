---
title: FxCop コード分析および FxCop アナライザー
ms.date: 09/06/2018
ms.prod: visual-studio-dev15
ms.topic: overview
helpviewer_keywords:
- code analysis FAQ
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 52d28289d1a449ddf44be7d660bf60e9b3877c8c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026220"
---
# <a name="frequently-asked-questions-about-fxcop-and-fxcop-analyzers"></a>FxCop および FxCop アナライザーに関してよく寄せられる質問

従来の FxCop と FxCop アナライザー間の違いは、少し理解しにくい場合があります。 この記事は、ユーザーの方々がお持ちの質問を解決することを意図しています。

## <a name="whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers"></a>従来の FxCop と FxCop アナライザー間の違いは何ですか?

従来の FxCop は、コンパイル済みのアセンブリ上でビルド後の分析を実行します。 これは、**FxCopCmd.exe** という別の実行可能ファイルとして実行されます。 FxCopCmd.exe はコンパイル済みのアセンブリを読み込み、コード分析を実行し、結果 (または*診断*) を報告します。

FxCop アナライザーは .NET Compiler Platform ("Roslyn") に基づいています。 これは、ユーザーがプロジェクトまたはソリューションで参照する [NuGet パッケージとしてインストール](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-nuget-package)します。 FxCop アナライザーは、コンパイラーの実行中にソースコードに基づく分析を実行します。 FxCop アナライザーは、**csc.exe** または **vbc.exe** のコンパイラーのプロセス内にホストされ、プロジェクトの構築時に分析を実行します。 アナライザーの結果は、コンパイラーの結果と共に報告されます。

> [!NOTE]
> [FxCop アナライザーは、Visual Studio の拡張機能としてインストールする](install-fxcop-analyzers.md#to-install-fxcop-analyzers-as-a-vsix)ことも可能です。 この場合、コード エディターに入力を行うとアナライザーが実行されます。ビルド時には実行されません。 継続的インテグレーション (CI) の一環として FxCop を実行する場合、代わりに NuGet パッケージとしてインストールします。

## <a name="does-the-run-code-analysis-command-run-fxcop-analyzers"></a>[コード分析の実行] コマンドで FxCop アナライザーを実行できますか?

いいえ。 Visual Studio 2017 で **[分析]** > **[コード分析の実行]** を選択すると、スタティック コード分析または従来の FxCop が実行されます。 **[コード分析の実行]** は、Roslyn ベースの FxCop アナライザーを含む Roslyn ベースのアナライザーには何の影響もありません。

## <a name="does-the-runcodeanalysis-msbuild-project-property-run-analyzers"></a>RunCodeAnalysis msbuild プロジェクト プロパティはアナライザーを実行しますか?

いいえ。 (たとえば *.csproj* の) プロジェクト ファイル内の **RunCodeAnalysis** プロパティは、従来の FxCop を実行するためのみに使用します。 これは、**FxCopCmd.exe** を起動するビルド後の msbuild タスクを実行します。 これは、Visual Studio で **[分析]** > **[コード分析の実行]** を選択するのと同等です。

## <a name="so-how-do-i-run-fxcop-analyzers-then"></a>では FxCop アナライザーはどのように実行するのですか?

FxCop アナライザーを実行するには、まずそれ用に [NuGet パッケージをインストール](install-fxcop-analyzers.md)します。 次いでプロジェクトまたはソリューションを Visual Studio または msbuild を使用してビルドします。 FxCop アナライザーが生成する警告やエラーは、**[エラー一覧]** またはコマンド ウィンドウに表示されます。

## <a name="see-also"></a>関連項目

- [.NET Compiler Platform アナライザーの概要](roslyn-analyzers-overview.md)
- [アナライザーの概要](fxcop-analyzers.yml)
- [FxCop アナライザーのインストール](install-fxcop-analyzers.md)
