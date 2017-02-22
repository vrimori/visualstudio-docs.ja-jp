---
title: "規則セットを使用したコード分析規則のグループ化 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.rulesets.learnmore"
helpviewer_keywords: 
  - "コード分析, ルール セット"
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 36
caps.handback.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 規則セットを使用したコード分析規則のグループ化
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、または [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] でコード分析を構成するとき、Microsoft の組み込みの*規則セット*の一覧から選択できます。  規則セットは、対象の問題および特定の条件を識別するコード分析規則の論理的なグループです。  たとえば、一般に公開されている API 用のコードをスキャンするように設計された規則セットを適用したり、最小推奨規則のみが含まれた規則セットを適用したりできます。  また、すべての規則が含まれた規則セットを適用することもできます。  
  
 規則を追加または削除したり変更してカスタマイズした規則セットを、警告またはエラーとして **\[エラー一覧\]** ウィンドウに表示できます。  カスタマイズした規則セットで、特定の開発環境の要件を満たすことができます。  規則セットをカスタマイズする場合、処理に役立つ検索ツールおよびフィルター処理ツールが規則セットのページに表示されます。  
  
## 一般的なタスク  
  
|タスク|関連するコンテンツ|  
|---------|---------------|  
|**実習を行う:** コード分析ツールを使用してカスタム規則セットを指定し、単純な .NET Framework アプリケーションの問題を検出して修正します。|-   [チュートリアル: カスタム規則セットの構成と使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**プロジェクト用のコード分析を構成する:** プロジェクト、Web サイト、またはソリューション用の既存の規則セットを選択します。|-   [方法: マネージ コード プロジェクトのコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [規則セットを使用した実行対象の C\+\+ 規則の指定](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [方法: ASP.NET Web アプリケーション用にコード分析を構成する](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [方法: ソリューション内の複数のプロジェクトに対して規則セットを指定する](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**規則セットをカスタマイズする:** プロジェクトに適用する規則を指定します。|-   [カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**組み込みの規則セットを理解する:** 組み込みの規則セットを構成するコード分析規則を表示します。|-   [コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)|  
|**コード分析を Team Foundation Server と統合する:**  [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] のチェックイン ポリシーにより、開発チームは、すべてのコード チェックインがコード分析標準の共通セットに対応していることを確認できます。|-   [方法: コード プロジェクト規則セットをチーム プロジェクトのチェックイン ポリシーと同期させる](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|