---
title: Visual Studio での Roslyn アナライザー |Microsoft ドキュメント
ms.date: 03/26/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 35b052c795ae10b7d7c4f96c8c4fce72ecbee839
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET コンパイラ プラットフォーム アナライザーの概要

Visual Studio 2017 には、一連組み込みを入力すると、c# または Visual Basic コードを分析する .NET コンパイラ プラットフォーム アナライザーにはが含まれています。 NuGet パッケージとして、Visual Studio 拡張機能として、またはプロジェクトごとの単位で追加のアナライザーをインストールできます。 アナライザーは、コード スタイル、コードの品質と保守容易性、コードの設計、およびその他の問題になります。

それらが報告される規則違反が見つかった場合、アナライザーによって、コード エディターで、両方、*波*、害のあるコードの下と、**エラー一覧**です。

多数のアナライザー ルールまたは*診断*、1 つ以上の関連がある*コード修正*の問題が解決に適用することできます。 各 Visual Studio に組み込まれているアナライザー診断では、関連付けられているコードの修正プログラムがあります。 電球のアイコン メニューで、他の種類のと共にコード修正が示すように*クイック アクション*です。 これらのコードの修正プログラムについては、次を参照してください。[一般的なクイック アクション](../ide/common-quick-actions.md)です。

![クイック アクション コードを修正してアナライザー違反](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>静的コード分析と Roslyn アナライザー

.NET コンパイラ プラットフォーム ("Roslyn") のアナライザーが最終的に置き換える[静的コード分析](../code-quality/code-analysis-for-managed-code-overview.md)マネージ コード用です。 静的コード分析ルールの多くは、Roslyn アナライザー診断として書き換えられたが既にです。

静的コード分析規則違反に表示される Roslyn アナライザー違反、**エラー一覧**です。 さらに、Roslyn アナライザー違反にも表示、コード エディターとして*波形*害のあるコードの下。 波の色が異なります、[の重大度設定](../code-quality/use-roslyn-analyzers.md#rule-severity)ルールのです。 次のスクリーン ショットは、次の 3 つの違反を示しています。&mdash;赤、緑、および 1 つのグレー。

![コード エディターで波形](media/diagnostics-severity-colors.png)

Roslyn アナライザーは、静的コード分析が有効になっていてもライブ入力した場合と同様に、ビルド時にコードを分析します。 Roslyn アナライザーが有効にした場合に、エディターで開かれていないコード ファイルのデザイン時の分析を提供できますも[完全ソリューション解析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)です。

> [!NOTE]
> ビルド時エラーと警告 Roslyn アナライザーからは、表示のみ、アナライザーが NuGet パッケージとしてインストールされているかどうか。

Roslyn アナライザーは同じ種類の静的コード分析は、問題をレポートだけでなく、によって、1 つまたはすべてのファイルまたはプロジェクトで違反の修正が容易です。 これらのアクションが呼び出されます*コード修正*です。 コードの修正プログラムは IDE に固有です。Visual Studio で、として実装される[クイック アクション](../ide/quick-actions.md)です。 すべてのアナライザー診断では、関連付けられているコードの修正プログラムがあります。

> [!NOTE]
> メニュー オプション**分析** > **コード分析を実行**のみに静的コード分析機能を適用します。 プロジェクトの さらに、**コード分析**プロパティ ページで、**ビルドに対するコード分析を有効にする**と**生成されたコードから結果を表示しない**のチェック ボックスにのみ適用されます静的コード分析します。 これら Roslyn アナライザーに影響を与えるありません。

Roslyn アナライザーから違反と静的コード分析の間で区別するために、**エラー一覧**を見て、**ツール**列です。 アナライザーのアセンブリは、のいずれかのツール値に一致するかどうかは**ソリューション エクスプ ローラー**、たとえば**Microsoft.CodeQuality.Analyzers**違反は、Roslyn アナライザーから取得します。 それ以外の場合、静的コード分析から、違反が発生します。

![エラー一覧 にツールの列](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-vs-extension"></a>拡張機能と NuGet パッケージ

アナライザーは、.NET コンパイラ プラットフォームには、Visual Studio 拡張機能としての NuGet パッケージ、または Visual Studio 全体を使用してプロジェクト単位がインストールされています。 これら 2 つの方法の場合は、いくつかキーの動作に違いがある[アナライザーをインストールする](../code-quality/install-roslyn-analyzers.md)です。

### <a name="scope"></a>スコープ

場合は、Visual Studio 拡張機能としてアナライザーをインストールすると、Visual Studio のすべてのインスタンスにソリューション レベルで適用されます。 推奨される方法には、NuGet パッケージとして、アナライザーをインストールする場合、NuGet パッケージがインストールされているプロジェクトにのみ適用されます。 NuGet パッケージとしてインストールされているアナライザーは、チームの環境のスコープ内*すべて開発者*そのプロジェクトで作業します。

### <a name="build-errors"></a>ビルド エラー

などコマンドラインを使用して継続的インテグレーションの一部として (CI) ビルドのビルド時に適用される規則には、NuGet パッケージとして、アナライザーをインストールします。 アナライザーの警告とエラーに表示されないのビルド レポート拡張機能として、アナライザーをインストールする場合。

次のスクリーン ショットは、アナライザー規則違反を含むプロジェクトのビルドからのコマンド ライン ビルド出力を示しています。

![ルール違反に MSBuild 出力](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>ルールの重要度

Visual Studio 拡張機能としてインストールされているアナライザーからルールの重大度を設定することはできません。 構成する[ルールの重大度](../code-quality/use-roslyn-analyzers.md#rule-severity)、NuGet パッケージとして、アナライザーをインストールします。

## <a name="next-steps"></a>次の手順

- [Visual Studio での Roslyn アナライザーをインストールします。](../code-quality/install-roslyn-analyzers.md)
- [Visual Studio での Roslyn アナライザーを使用します。](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>関連項目

- [Visual Studio でのクイック操作](../ide/quick-actions.md)
- [独自の Roslyn アナライザーを書き込む](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET コンパイラ プラットフォーム SDK](/dotnet/csharp/roslyn-sdk/)