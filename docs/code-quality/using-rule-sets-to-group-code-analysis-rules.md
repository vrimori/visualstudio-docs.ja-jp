---
title: "コード分析規則のグループ設定ルールを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.rulesets.learnmore
helpviewer_keywords: code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: "36"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 51b282cb86ca83ecf2ace1e4b12c8444928b15e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>規則セットを使用したコード分析規則のグループ化
コード分析を構成するとき[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、 [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、または[!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]、Microsoft の組み込みの一覧から選択できます*ルール セット*です。 規則セットは、対象の問題および特定の条件を識別するコード分析規則の論理的なグループです。 パブリックに公開されている Api のコードをスキャンするように設計された規則セットを適用するを最小推奨規則のみを含む規則セットを適用することができます。 すべてのルールを含んだ規則セットを適用することもできます。  
  
 ルール セットを追加または削除の規則または規則を変更することでの表示をカスタマイズすることができます、**エラー一覧**ウィンドウに、警告またはエラーとして。 カスタマイズした規則セットで、特定の開発環境の要件を満たすことができます。 規則セットをカスタマイズする場合、処理に役立つ検索ツールおよびフィルター処理ツールが規則セットのページに表示されます。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**実践的な経験を取得します。**を見つけて、単純な .NET Framework アプリケーションでの問題を修正するカスタム ルールを指定するコード分析ツールのセットを使用します。|-   [チュートリアル: 構成とカスタム規則セットの使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**プロジェクトのコード分析を構成する:**プロジェクト、Web サイト、またはソリューションを設定、既存のルールを選択します。|-   [方法: マネージ コード プロジェクトのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [規則セットを使用して実行するように C++ の規則を指定するには](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [方法: ASP.NET Web アプリケーションのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [方法: ソリューション内の複数のプロジェクトに対して規則セットを指定します。](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**規則セットをカスタマイズ:**プロジェクトに適用する規則を指定します。|-   [カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**組み込みの規則セットを理解する:**組み込みの規則セットを構成するコード分析規則を表示します。|-   [コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)|  
|**コード分析を Team Foundation Server と統合:** [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]チェックイン ポリシーにより、開発チームをすべてコード チェックインがコード分析の標準の共通セットを満たしているかどうかを確認します。|-   [方法: コード プロジェクト規則セットをチーム プロジェクト チェックイン ポリシーと同期](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|