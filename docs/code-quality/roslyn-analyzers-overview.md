---
title: Visual Studio で Roslyn アナライザー
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: overview
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3d5836c0522ef97a634f44799934aab2750b3a45
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511423"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET コンパイラ プラットフォームのアナライザーの概要

Visual Studio 2017 には、一連組み込みを入力すると、c# または Visual Basic のコードを分析する .NET コンパイラ プラットフォームのアナライザーにはが含まれています。 NuGet パッケージとして、Visual Studio 拡張機能として、またはプロジェクトごとにその他のアナライザーをインストールできます。 アナライザーは、コード スタイル、コードの品質と保守容易性、コードの設計、およびその他の問題を確認します。

規則違反が見つかった場合、アナライザーによって、それらが報告される両方としてコード エディターで、*波線*問題のあるコード、および、**エラー一覧**します。

多くのアナライザー ルールまたは*診断*、1 つ以上の関連がある*コード修正*問題を解決に適用できます。 各 Visual Studio に組み込まれているアナライザー診断では、関連付けられているコードの修正プログラムがあります。 コード修正は電球アイコン メニューの他の種類のと共にに示した*クイック アクション*します。 これらのコード修正プログラムの詳細については、次を参照してください。[共通のクイック アクション](../ide/common-quick-actions.md)します。

![アナライザーの違反とコード修正のクイック アクション](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>静的コード分析と Roslyn アナライザー

.NET コンパイラ プラットフォーム ("Roslyn") のアナライザーを入れ替えよう[静的コード分析](../code-quality/code-analysis-for-managed-code-overview.md)マネージ コード用。 静的コード分析ルールの多くに Roslyn アナライザーの診断として既に書き換えること。

表示する Roslyn アナライザーの違反、静的コード分析ルール違反のように、**エラー一覧**します。 さらに、Roslyn アナライザーの違反も表示としてコード エディターで*波形*問題のあるコードです。 に応じて、波線の色、[の重大度設定](../code-quality/use-roslyn-analyzers.md#rule-severity)ルールの。 次のスクリーン ショットは、次の 3 つの違反を示しています。&mdash;1 つの赤、緑、および 1 つの灰色。

![コード エディターで波形](media/diagnostics-severity-colors.png)

有効になっていてもライブ入力すると場合、静的コード分析などのビルド時にコードを分析する Roslyn アナライザーです。 Roslyn アナライザーでは有効にした場合にエディターで開かれていないコード ファイルのデザイン時の分析を提供できますも[完全ソリューション解析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)します。

> [!NOTE]
> Roslyn アナライザーからビルド時のエラーと警告は表示のみ、アナライザーは、NuGet パッケージとしてインストールされているかどうか。

Roslyn アナライザーは同じ種類の静的コード分析では、問題を報告できるだけでなく、によって、1 つまたはすべての出現回数、ファイルまたはプロジェクトで、違反の修正が簡単します。 これらのアクションが呼び出されます*コード修正*します。 コード修正は IDE に固有です。Visual Studio で、として実装されて[クイック アクション](../ide/quick-actions.md)します。 すべてのアナライザー診断では、関連付けられているコードの修正プログラムがあります。

> [!NOTE]
> メニュー オプション**分析** > **コード分析を実行**のみに静的コード分析を適用します。 さらに、プロジェクトの **コード分析**プロパティ ページで、**ビルドに対するコード分析を有効にする**と**結果生成されたコードを表示しない**のチェック ボックスはのみに適用されます静的コード分析します。 Roslyn アナライザーへの影響があるはありません。

Roslyn アナライザーから違反と静的コード分析で区別する、**エラー一覧**を見て、**ツール**列。 ツールの値が、アナライザーのアセンブリのいずれかと一致するかどうか**ソリューション エクスプ ローラー**、たとえば**Microsoft.CodeQuality.Analyzers**違反に由来する Roslyn アナライザーです。 それ以外の場合、違反は、静的コード分析から発生します。

![エラー一覧内の列のツール](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>VSIX 拡張機能と NuGet パッケージ

アナライザーは、.NET コンパイラ プラットフォームには、Visual Studio 拡張機能としての NuGet パッケージ、または Visual Studio 全体を使用して、プロジェクトごとがインストールされています。 これら 2 つのメソッドの間でキーの動作の違いがある[アナライザーをインストールする](../code-quality/install-roslyn-analyzers.md)します。

### <a name="scope"></a>スコープ

Visual Studio 拡張機能としてアナライザーをインストールする場合に適用ソリューション レベルでは、Visual Studio のすべてのインスタンス。 推奨される方法には、NuGet パッケージとして、アナライザーをインストールする場合は、NuGet パッケージがインストールされているプロジェクトにのみ適用されます。 チーム環境で、NuGet パッケージとしてインストールされているアナライザーがのスコープでは*すべて開発者*そのプロジェクトで作業します。

### <a name="build-errors"></a>ビルド エラー

(CI) ビルドでは、コマンドラインを使用して、または継続的インテグレーションの一部としてを含め、ビルド時に適用される規則には、NuGet パッケージとして、アナライザーをインストールします。 アナライザーの警告とエラーに表示されない、ビルド レポートの拡張機能として、アナライザーをインストールする場合。

次のスクリーン ショットは、アナライザーの規則違反を含むプロジェクトをビルドしてからコマンド ライン ビルドの出力を示しています。

![ルール違反で MSBuild 出力](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>ルールの重要度

Visual Studio 拡張機能としてインストールされたアナライザーからルールの重大度を設定することはできません。 構成する[規則の重要度](../code-quality/use-roslyn-analyzers.md#rule-severity)アナライザーを NuGet パッケージとしてインストールします。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Visual Studio で Roslyn アナライザーをインストールします。](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio で Roslyn アナライザーを使用します。](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>関連項目

- [Visual Studio でのクイック アクション](../ide/quick-actions.md)
- [独自の Roslyn アナライザーを作成します。](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)