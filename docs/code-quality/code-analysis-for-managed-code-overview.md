---
title: Visual Studio でマネージ コードのコード分析
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b7b992dadb703cf1c4f73830324e9934d7525645
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920458"
---
# <a name="overview-of-code-analysis-for-managed-code"></a>マネージ コードに対するコード分析の概要

Visual Studio 2017 が 2 つの方法でマネージ コードを分析して: legacy *FxCop* .NET コンパイラ プラットフォームと、マネージ アセンブリの静的分析*アナライザー*です。 このトピックでは、FxCop の静的コード分析について説明します。 .NET コンパイラ プラットフォーム アナライザーを使用して、コードの分析の詳細については、次を参照してください。[概要 Roslyn のアナライザー](../code-quality/roslyn-analyzers-overview.md)です。

マネージ コードのコード分析を使用すると、マネージ アセンブリを分析し、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、アセンブリに関する情報をレポートとして得ることができます。

分析ツールは、分析中に実行するチェック項目を警告メッセージとして表示します。 警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。

## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合

手動または自動では、プロジェクトでコード分析を実行できます。

分析を実行するコード プロジェクトをビルドするたびに、**ビルドに対するコード分析を有効にする**プロジェクトのプロパティ ページ。 詳細については、次を参照してください。[する方法: 有効化と自動コード分析の無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)です。

プロジェクトを手動でコード分析を実行するメニュー バーから選択**分析** > **コード分析を実行** > **でコード分析を実行\<プロジェクト>** です。

## <a name="rule-sets"></a>規則セット

マネージ コードのコード分析規則がまとめられて[ルール セット](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)です。 Microsoft の標準規則セットのいずれかを使用することもできます[カスタム規則セットを作成する](../code-quality/how-to-create-a-custom-rule-set.md)特定のニーズを満たすためにします。

## <a name="suppress-warnings"></a>[警告の表示なし]

警告が適用されないことを示すと役に立つことがよくあります。 これによって、開発者や、そのコードを後でレビューする担当者は、その警告が既に調査済みであり、抑制されるのかまたは無視されるのかがわかります。

警告のソース内抑制は、カスタム属性を介して実装されます。 警告を抑制するには、次の例のように、属性 `SuppressMessage` をソース コードに追加します。

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

詳細については、次を参照してください。[警告を抑制する](../code-quality/in-source-suppression-overview.md)です。

> [!NOTE]
> Visual Studio 2017 にプロジェクトを移行する場合に、コード分析の警告の数が多いが直面突然可能性があります。 場合は、警告を修正し、すぐに生産性を向上する場合ができていない、*基準*プロジェクトの分析の状態。 **分析**メニューの**コード分析を実行し、アクティブな懸案事項の抑制**です。

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部としてのコード分析の実行

組織的な取り決めとして、チェックインされるすべてのコードが、特定のポリシーを満たしていることが必要な場合があります。 たとえば、次のようなポリシーが考えられます。

- チェックインされているコードでは、ビルド エラーはありません。

- コード分析は、最新のビルドの一部として実行されます。

これは、チェックイン ポリシーを指定することにより実現できます。 詳細については、次を参照してください。[チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)です。

## <a name="team-build-integration"></a>チーム ビルドの統合

ビルド システムの統合機能を使用すると、分析ツールをビルド プロセスの一環として実行できます。 詳細については、次を参照してください。[ビルドとリリースの (VSTS)](/vsts/build-release/index)です。

## <a name="see-also"></a>関連項目

- [Roslyn アナライザーの概要](../code-quality/roslyn-analyzers-overview.md)
- [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [方法: を有効にして、自動コード分析を無効にします。](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
