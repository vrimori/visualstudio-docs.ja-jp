---
title: コード分析をマネージ コードの概要の |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f48bb0e1832ef92a4d03a775123a062090936090
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592958"
---
# <a name="code-analysis-for-managed-code-overview"></a>マネージド コードに対するコード分析の概要
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[マネージ コードの概要のコード分析](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-for-managed-code-overview)します。  
  
マネージド コードのコード分析を使用すると、マネージド アセンブリを分析し、Microsoft .NET Framework デザイン ガイドラインに規定されたプログラミングやデザインに関する規則違反など、アセンブリに関する情報をレポートとして得ることができます。  
  
 分析ツールは、分析中に実行するチェック項目を警告メッセージとして表示します。 警告メッセージは、プログラミングやデザイン上の問題を識別し、可能であれば問題の解決方法を提供します。  
  
## <a name="ide-integrated-development-environment-integration"></a>IDE (統合開発環境) の統合  
 開発者は、プロジェクトに対してコード分析を自動的に実行できるだけでなく、手動で実行することもできます。  
  
 選択したプロジェクトをビルドするたびにコード分析を実行する**を有効にするビルドに対するコード分析 (CODE_ANALYSIS 定数を定義します)** プロジェクトのプロパティ ページ。 詳細については、次を参照してください。[方法: 有効にすると、自動コード分析を無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)します。  
  
 プロジェクトでコード分析を手動で実行する、**分析** メニューのをクリックして**でコード分析を実行**_ProjectName_します。 詳細については、次を参照してください。[方法: 有効にすると、自動コード分析を無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)します。  
  
## <a name="rule-sets"></a>規則セット  
 マネージ コードのコード分析規則にグループ化*ルール セット*します。 Microsoft の標準の規則セットのいずれかを使用するか、特定のニーズを満たす独自の規則セットを作成することができます。 詳細については、次を参照してください。[ルール セットのコード分析規則のグループを使用して](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)します。  
  
## <a name="in-source-suppression"></a>ソース内抑制  
 警告が適用されないことを示すと役に立つことがよくあります。 これによって、開発者や、そのコードを後でレビューする担当者は、その警告が既に調査済みであり、抑制されるのかまたは無視されるのかがわかります。  
  
 警告のソース内抑制は、カスタム属性を使用して実装します。 警告を抑制するには、次の例のように、属性 `SuppressMessage` をソース コードに追加します。  
  
 `[System.Diagnosis.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 `Public class MyClass`  
  
 `{`  
  
 `// code`  
  
 `}`  
  
 詳細については、次を参照してください。 [SuppressMessage 属性使用での警告を抑制する](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)します。  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>チェックイン ポリシーの一部としてのコード分析の実行  
 組織的な取り決めとして、チェックインされるすべてのコードが、特定のポリシーを満たしていることが必要な場合があります。 たとえば、次のようなポリシーが考えられます。  
  
-   チェックイン対象のコードにビルド エラーが存在しないこと。  
  
-   最近のビルドでコード分析が実行されていること。  
  
 これは、チェックイン ポリシーを指定することにより実現できます。 詳細については、次を参照してください。[チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)します。  
  
## <a name="team-build-integration"></a>チーム ビルドの統合  
 ビルド システムの統合機能を使用すると、分析ツールをビルド プロセスの一環として実行できます。 詳細については、「[アプリケーションのビルド](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [コード分析規則のグループに規則を使用して設定します。](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [方法: 自動コード分析を有効/無効にする](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)



