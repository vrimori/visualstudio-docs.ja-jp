---
title: Roslyn アナライザーを使用したコード分析
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 3f3f0307a8081cbff73dd39bba67fbbc2e5fa7b6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864856"
---
# <a name="overview-of-net-compiler-platform-analyzers"></a>.NET Compiler Platform アナライザーの概要

Visual Studio 2017 には、入力したときに C# や Visual Basic のコードを分析する、組み込みの .NET Compiler Platform アナライザーのセットが含まれています。 アナライザーでは、コード スタイル、コードの品質と保守性、コード設計、およびその他の問題が確認されます。 Visual Studio 拡張機能として、または NuGet パッケージとしてプロジェクトごとに、追加のアナライザーをインストールできます。

アナライザーでルール違反が見つかった場合は、コード エディターで問題のあるコードの下に*波線* として報告され、**[エラー一覧]** でも報告されます。

多くのアナライザー ルール (*診断*) には、1 つ以上の*コード修正*が関連付けられており、これを適用して問題を修正できます。 Visual Studio に組み込まれているアナライザー診断には、それぞれコード修正が関連付けられています。 コード修正は電球アイコン メニューに、他の種類の*クイック アクション* と共に示されます。 これらのコード修正については、「[共通のクイック アクション](../ide/common-quick-actions.md)」を参照してください。

![アナライザーの違反とクイック アクションのコード修正](../code-quality/media/built-in-analyzer-code-fix.png)

## <a name="roslyn-analyzers-vs-static-code-analysis"></a>Roslyn アナライザーとスタティック コード分析

.NET Compiler Platform ("Roslyn") アナライザーは最終的に、マネージド コード用の[スタティック コード分析](../code-quality/code-analysis-for-managed-code-overview.md)に置き換えられます。 スタティック コード分析ルールの多くは、既に Roslyn アナライザー診断として書き換えられています。

スタティック コード分析のルール違反と同様、Roslyn アナライザーの違反は **[エラー一覧]** に表示されます。 さらに、Roslyn アナライザーの違反は、コード エディターで問題のあるコードの下に*波線* としても示されます。 波線の色は、ルールの[重要度設定](../code-quality/use-roslyn-analyzers.md#rule-severity)によって異なります。 次のスクリーンショットには、3 つの違反 (赤色、緑色、灰色が 1 つずつ) が示されています。

![コード エディターの波線](media/diagnostics-severity-colors.png)

有効になっている場合はスタティック コード分析と同様、Roslyn アナライザーでビルド時にコードが分析されますが、入力中もライブ状態になります。 Roslyn アナライザーではエディターで開かれていないコード ファイルを設計時に分析することもできます ([完全ソリューション解析](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md#to-toggle-full-solution-analysis)を有効にした場合)。

> [!NOTE]
> Roslyn アナライザーからのビルド時のエラーと警告が表示されるのは、アナライザーが NuGet パッケージとしてインストールされている場合のみです。

Roslyn アナライザーでは、スタティック コード分析で報告されるものと同じ種類の問題が報告されるだけでなく、ファイルやプロジェクトで発生した違反の 1 つ、またはすべてを簡単に修正することができます。 これらのアクションを*コード修正*と呼びます。 コード修正は IDE に固有のものです。Visual Studio では、[クイック アクション](../ide/quick-actions.md)として実装されます。 すべてのアナライザー診断にコード修正が関連付けられているわけではありません。

> [!NOTE]
> メニュー オプションの **[分析]** > **[コード分析の実行]** は、スタティック コード分析にのみ適用されます。 さらに、プロジェクトの **[コード分析]** プロパティ ページでは、**[ビルドに対するコード分析の有効化]** および **[生成されたコードから結果を表示しない]** チェック ボックスはスタティック コード分析にのみ適用されます。 Roslyn アナライザーには影響しません。

**[エラー一覧]** で Roslyn アナライザーとスタティック コード分析からの違反を区別するには、**[ツール]** 列を確認します。 **ソリューション エクスプローラー**のアナライザー アセンブリのいずれかが [ツール] の値 (**Microsoft.CodeQuality.Analyzers** など) と一致する場合、違反は Roslyn アナライザーからのものです。 それ以外の場合、違反はスタティック コード分析からのものです。

![[エラー一覧] の [ツール] 列](media/code-analysis-tool-in-error-list.png)

## <a name="nuget-package-versus-vsix-extension"></a>NuGet パッケージと VSIX 拡張機能

.NET Compiler Platform アナライザーは、NuGet パッケージを介してプロジェクトごとに、または Visual Studio 拡張機能として Visual Studio 全体にインストールすることができます。 [アナライザーをインストールする](../code-quality/install-roslyn-analyzers.md)これら 2 つの方法には、主な動作の違いがいくつかあります。

### <a name="scope"></a>スコープ

Visual Studio 拡張機能としてアナライザーをインストールする場合、ソリューション レベルで Visual Studio のすべてのインスタンスに適用されます。 NuGet パッケージとしてアナライザーをインストールする (推奨される方法) 場合、NuGet パッケージがインストールされたプロジェクトにのみ適用されます。 チーム環境では、NuGet パッケージとしてインストールされたアナライザーは、そのプロジェクトで作業する*すべての開発者* のスコープ内にあります。

### <a name="build-errors"></a>ビルド エラー

継続的インテグレーション (CI) ビルドの一部として、あるいはコマンド ラインを使用するなどして、ビルド時にルールを適用するには、NuGet パッケージとしてアナライザーをインストールします。 拡張機能としてアナライザーをインストールする場合、アナライザーの警告とエラーはビルド レポートに示されません。

次のスクリーンショットは、アナライザー ルール違反を含むプロジェクトのビルドからのコマンドライン ビルド出力を示しています。

![ルール違反を示す MSBuild 出力](media/command-line-build-analyzers.png)

### <a name="rule-severity"></a>ルールの重要度

Visual Studio 拡張機能としてインストールされたアナライザーからルールの重要度を設定することはできません。 [ルールの重要度](../code-quality/use-roslyn-analyzers.md#rule-severity)を構成するには、NuGet パッケージとしてアナライザーをインストールします。

## <a name="next-steps"></a>次の手順

> [!div class="nextstepaction"]
> [Visual Studio で Roslyn アナライザーをインストールする](../code-quality/install-roslyn-analyzers.md)

> [!div class="nextstepaction"]
> [Visual Studio で Roslyn アナライザーを使用する](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>関連項目

- [Visual Studio のクイック アクション](../ide/quick-actions.md)
- [独自の Roslyn アナライザーを作成する](../extensibility/getting-started-with-roslyn-analyzers.md)
- [.NET Compiler Platform SDK](/dotnet/csharp/roslyn-sdk/)