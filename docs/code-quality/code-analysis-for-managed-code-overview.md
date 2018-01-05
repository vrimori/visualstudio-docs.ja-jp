---
title: "コード分析の概要についてはマネージ コード |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b705abb680276faf9d4311cd21cae1b103c4a09d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>マネージ コードの概要のコード分析

マネージ コードのコード分析を使用すると、マネージ アセンブリを分析し、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、アセンブリに関する情報をレポートとして得ることができます。

分析ツールは、分析中に実行するチェック項目を警告メッセージとして表示します。 警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。

## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合

手動または自動では、プロジェクトでコード分析を実行できます。

分析を実行するコード プロジェクトをビルドするたびに、**ビルドに対するコード分析を有効にする**プロジェクトのプロパティ ページ。 詳細については、次を参照してください。[する方法: 有効化と自動コード分析の無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)です。

プロジェクトを手動でコード分析を実行するメニュー バーから選択**分析** > **コード分析を実行** > **でコード分析を実行<project>** . 詳細については、次を参照してください。[する方法: 有効化と自動コード分析の無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)です。

## <a name="rule-sets"></a>規則セット

マネージ コードのコード分析規則がまとめられて*ルール セット*です。 Microsoft の標準の規則セットのいずれかを使用するか、特定のニーズを満たす独自の規則セットを作成することができます。 詳細については、次を参照してください。[ルール セットのコード分析規則のグループを使用して](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)です。

## <a name="in-source-suppression"></a>ソース内抑制

警告が適用されないことを示すと役に立つことがよくあります。 これによって、開発者や、そのコードを後でレビューする担当者は、その警告が既に調査済みであり、抑制されるのかまたは無視されるのかがわかります。

ソース内の警告の抑制は、カスタム属性を介して実装されます。 警告を抑制するには、次の例のように、属性 `SuppressMessage` をソース コードに追加します。

```csharp
[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

詳細については、次を参照してください。[抑制する状況の警告を使用して、SuppressMessage 属性](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)です。

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部としてのコード分析の実行

組織的な取り決めとして、チェックインされるすべてのコードが、特定のポリシーを満たしていることが必要な場合があります。 たとえば、次のようなポリシーが考えられます。

- チェックインされているコードでは、ビルド エラーはありません。

- コード分析は、最新のビルドの一部として実行されます。

これは、チェックイン ポリシーを指定することにより実現できます。 詳細については、次を参照してください。[チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)です。

## <a name="team-build-integration"></a>チーム ビルドの統合

ビルド システムの統合機能を使用すると、分析ツールをビルド プロセスの一環として実行できます。 詳細については、次を参照してください。[ビルドとリリースの (VSTS)](/vsts/build-release/index)です。

## <a name="see-also"></a>関連項目

[コード分析規則のグループ設定ルールを使用して](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
[方法: を有効にして、自動コード分析を無効にします。](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)