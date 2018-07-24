---
title: コード分析規則セット
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa287570213e6238d0a8dffc9f6e70367b133591
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204428"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>コード分析規則のグループに規則を使用を設定します。

Visual Studio でコード分析を構成するときに、組み込みの一覧から選択することができます*ルール セット*します。 規則セットは、プロジェクトに適用され、コードのグループを対象となる問題とそのプロジェクトで特定の条件を識別する分析規則は。 たとえば、パブリックに利用可能な Api は、コードをスキャンするように設計された規則セットを適用することができます。 またはだけの最小推奨規則。 すべてのルールを含む規則セットを適用することもできます。

ルール セットを追加または削除、ルールまたはルールの重大度を変更することで警告またはエラーのいずれかとして表示をカスタマイズすることができます、**エラー一覧**します。 カスタマイズした規則セットで、特定の開発環境の要件を満たすことができます。 規則セットをカスタマイズするときに、ルール セット エディターは、検索とフィルター処理、プロセスに役立つツールを提供します。

規則セットがある[マネージ コードのスタティック分析](how-to-configure-code-analysis-for-a-managed-code-project.md)、 [C++ コードの分析](using-rule-sets-to-specify-the-cpp-rules-to-run.md)、および[Roslyn アナライザー](analyzer-rule-sets.md)します。

## <a name="rule-set-format"></a>ルール セットの形式

ルールのセットに XML 形式で指定した、 *.ruleset*ファイル。 ルールは、ID から構成されると、*アクション*、アナライザー ID と、ファイルの名前空間ごとに分類されます。

内容を *.ruleset*ファイルはこの xml のようになります。

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> やすく[ルール セットの編集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)、グラフィカル**ルール セット エディター**よりを手動でします。

ルール セットによって、プロジェクトが指定された、 **CodeAnalysisRuleSet** Visual Studio プロジェクト ファイルのプロパティ。 例えば:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>関連項目

- [コード分析規則セットの参照](../code-quality/rule-set-reference.md)