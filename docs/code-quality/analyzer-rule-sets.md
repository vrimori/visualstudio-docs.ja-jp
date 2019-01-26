---
title: アナライザーの規則セット
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5a8b082de0d22e75bf1e31751e788324c863524
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038631"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Roslyn アナライザーの規則セットします。

定義済みの規則セットは、いくつかの NuGet アナライザー パッケージに含まれています。 含まれている規則セットなど、 [Microsoft.CodeAnalysis.FxCopAnalyzers NuGet アナライザー パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)(バージョン 2.6.2 で開始) を有効または名前付け、セキュリティなどのカテゴリに基づくルールを無効にするか、パフォーマンス。 規則セットを使用して簡単にすばやく規則の特定のカテゴリに関連する規則違反のみを参照してください。

Roslyn アナライザーを従来の"FxCop"静的コード分析から移行する場合は、引き続き、以前に使用した同じ規則の構成を使用してこれらのルール セットが有効にします。

## <a name="use-analyzer-rule-sets"></a>アナライザーの規則セットを使用して、

したら[NuGet アナライザー パッケージをインストール](install-roslyn-analyzers.md)、定義済みの規則で設定を探してその*ruleset*ディレクトリ、たとえば *%userprofile%\\.nuget\packages\microsoft.codequality.analyzers\<バージョン > \rulesets*します。 そこから、ドラッグし削除、またはコピーして貼り付けるには、1 つまたは複数の Visual Studio プロジェクトにルール セットの**ソリューション エクスプ ローラー**します。

プロジェクトを右クリックしてルールの分析の設定のアクティブなルールを設定するために、**ソリューション エクスプ ローラー**選択**プロパティ**します。 プロジェクトのプロパティ ページで、選択、**コード分析**タブ。**この規則セットを実行**を選択します**参照**、プロジェクト ディレクトリにコピーした目的の規則セットを選択します。 選択したルール セットで有効になっているこれらの規則に規則違反のみ表示されます。

できます[定義済みの規則セットをカスタマイズする](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set)をカスタマイズします。 違反がエラーまたは警告として表示されるように、1 つまたは複数のルールの重大度を変更するなど、**エラー一覧**します。

## <a name="available-rule-sets"></a>使用可能なルール セット

定義済みアナライザーの規則セットは、パッケージ内のすべてのルールに影響する次の 3 つのルール セットを含める&mdash;すべてできるようにする 1 つをすべてを無効にする、各ルールの既定の重大度と有効化の設定を重視します。

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

また、特定のパフォーマンスやセキュリティなど、パッケージ内のルールのカテゴリごとに 2 つの規則セットが使用されます。 1 つの規則セットは、カテゴリのすべての規則をでき、1 つの規則セットは、カテゴリ内の各ルールの既定の重大度と有効化の設定を優先します。

 [Microsoft.CodeAnalysis.FxCopAnalyzers NuGet アナライザー パッケージ](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)従来の"FxCop"静的コード分析の使用可能なルール セットを一致するように、次のカテゴリの規則セットが含まれています。

- デザイン
- ドキュメント
- 保守性
- 名前付け
- パフォーマンス
- 信頼性
- セキュリティ
- 使い方

## <a name="see-also"></a>関連項目

- [.NET Compiler Platform アナライザーの概要](roslyn-analyzers-overview.md)
- [.NET コンパイラ プラットフォームのアナライザーをインストールします。](install-roslyn-analyzers.md)
- [構成し、Roslyn アナライザーの規則を使用](use-roslyn-analyzers.md)
- [コード分析規則のグループに規則を使用を設定します。](using-rule-sets-to-group-code-analysis-rules.md)