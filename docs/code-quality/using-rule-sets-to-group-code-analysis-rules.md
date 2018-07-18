---
title: Visual Studio でコード分析ルールを設定します。
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
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923056"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>コード分析規則のグループに規則を使用を設定します。

Visual Studio でコード分析を構成するときに、組み込みの一覧から選択できます*ルール セット*です。 規則セットは、プロジェクトに適用され、コードのグループを対象となる問題とそのプロジェクトで特定の条件を識別する分析ルールです。 パブリックに公開されている Api のコードをスキャンするように設計された規則セットを適用するなど、だけの最小推奨規則です。 すべてのルールを含んだ規則セットを適用することもできます。

ルール セットを追加または削除、ルールまたはルールの重大度を変更することで警告やエラーのいずれかとして表示をカスタマイズすることができます、**エラー一覧**です。 カスタマイズした規則セットで、特定の開発環境の要件を満たすことができます。 規則セットをカスタマイズするときに、規則セット エディターは、検索とフィルター処理に役立つツールを提供します。

## <a name="rule-set-format"></a>ルール セットの形式

XML 形式で指定したルール セット、 *.ruleset*ファイル。 ID で構成された規則と*アクション*、アナライザー ID および名前空間、ファイル内でグループ化します。

XML の内容、 *.ruleset*ファイルは次のようになります。

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
> 容易になります[ルール セットの編集](../code-quality/working-in-the-code-analysis-rule-set-editor.md)グラフィック**ルール セット エディター**より手動でします。

規則セットによって、プロジェクトを指定、 `CodeAnalysisRuleSet` Visual Studio プロジェクト ファイルのプロパティです。 例えば:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>関連項目

- [コード分析規則セットの参照](../code-quality/rule-set-reference.md)
