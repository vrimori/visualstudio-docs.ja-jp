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
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d42d7c7a78d6bde2560f6e5cf5538a93585870b
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="code-analysis-for-managed-code-overview"></a>マネージ コードに対するコード分析の概要
マネージ コードのコード分析を使用すると、マネージ アセンブリを分析し、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、アセンブリに関する情報をレポートとして得ることができます。  
  
 分析ツールは、分析中に実行するチェック項目を警告メッセージとして表示します。 警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合  
 開発者は、プロジェクトに対してコード分析を自動的に実行できるだけでなく、手動で実行することもできます。  
  
 選択したプロジェクトをビルドするたびにコード分析の実行、**を有効にするビルドに対するコード分析 (定数 CODE_ANALYSIS を定義)**プロジェクトのプロパティ ページ。 詳細については、次を参照してください。[する方法: 有効化と自動コード分析の無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)です。  
  
 プロジェクトでコード分析を手動で実行する、**分析** メニューのをクリックして**でコード分析を実行***ProjectName*です。 詳細については、次を参照してください。[する方法: 有効化と自動コード分析の無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)です。  
  
## <a name="rule-sets"></a>規則セット  
 マネージ コードのコード分析規則がまとめられて*ルール セット*です。 Microsoft の標準の規則セットのいずれかを使用するか、特定のニーズを満たす独自の規則セットを作成することができます。 詳細については、次を参照してください。[ルール セットのコード分析規則のグループを使用して](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)です。  
  
## <a name="in-source-suppression"></a>ソース内抑制  
 警告が適用されないことを示すと役に立つことがよくあります。 これによって、開発者や、そのコードを後で確認する担当者は、その警告が既に調査済みであり、抑制されるのかまたは無視されるのかがわかります。  
  
 警告のソース内抑制は、カスタム属性を使用して実装します。 警告を抑制するには、次の例のように、属性 `SuppressMessage` をソース コードに追加します。  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 詳細については、次を参照してください。[抑制する状況の警告を使用して、SuppressMessage 属性](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)です。  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部としてのコード分析の実行  
 組織的な取り決めとして、チェックインされるすべてのコードが、特定のポリシーを満たしていることが必要な場合があります。 たとえば、次のようなポリシーが考えられます。  
  
-   チェックイン対象のコードにビルド エラーが存在しないこと。  
  
-   最近のビルドでコード分析が実行されていること。  
  
 これは、チェックイン ポリシーを指定することにより実現できます。 詳細については、次を参照してください。[チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)です。  
  
## <a name="team-build-integration"></a>チーム ビルドの統合  
 ビルド システムの統合機能を使用すると、分析ツールをビルド プロセスの一環として実行できます。 詳細については、次を参照してください。[ビルドとリリースの](/vsts/build-release/index)します。  
  
## <a name="see-also"></a>関連項目  
 [コード分析規則のグループ設定ルールを使用して](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [方法: を有効にして、自動コード分析を無効にします。](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)