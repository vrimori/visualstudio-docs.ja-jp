---
title: コード分析規則のグループに規則を使用して設定 |Microsoft Docs
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
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: ed0f3a2a-1516-42e2-92de-b8986dc75d42
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ae7374ae6b713fe7fa1911cdcce3effa600482b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547956"
---
# <a name="using-rule-sets-to-group-code-analysis-rules"></a>規則セットを使用したコード分析規則のグループ化
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ルール セットのコード分析規則のグループを使用して](https://docs.microsoft.com/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules)します。  
  
コード分析を構成するとき[!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]、 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]、または[!INCLUDE[vsPro](../includes/vspro-md.md)]、Microsoft の組み込みの一覧から選択できます*ルール セット*します。 規則セットは、対象の問題および特定の条件を識別するコード分析規則の論理的なグループです。 たとえば、パブリックに利用可能な Api は、コードをスキャンするように設計された規則セットを適用することができます。 または最小推奨規則のみを含む規則セットを適用することができます。 すべてのルールを含む規則セットを適用することもできます。  
  
 表示されるを追加または削除、ルールまたはルールを変更することでの設定ルールをカスタマイズすることができます、**エラー一覧**警告またはエラーのいずれかのウィンドウ。 カスタマイズした規則セットで、特定の開発環境の要件を満たすことができます。 規則セットをカスタマイズする場合、処理に役立つ検索ツールおよびフィルター処理ツールが規則セットのページに表示されます。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|タスク|関連するコンテンツ|  
|----------|---------------------|  
|**実習を行う:** 検索、単純な .NET Framework アプリケーションで問題を修正して、カスタム ルールを指定するコード分析ツールのセットを使用します。|-   [チュートリアル: 構成とカスタム規則セットの使用](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)|  
|**プロジェクトのコード分析を構成する:** プロジェクト、Web サイト、またはソリューションの設定の既存規則を選択します。|-   [方法: マネージ コード プロジェクトのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)<br />-   [規則セットを使用して、実行対象の C++ 規則を指定するには](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)<br />-   [方法: ASP.NET Web アプリケーションのコード分析を構成します。](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)<br />-   [方法: ソリューション内の複数のプロジェクトに対して規則セットを指定します。](../code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution.md)|  
|**規則セットをカスタマイズ:** プロジェクトに適用する規則を指定します。|-   [カスタム規則セットの作成](../code-quality/creating-custom-code-analysis-rule-sets.md)|  
|**組み込みの規則セットを理解する:** 組み込みの規則セットを構成するコード分析規則を表示します。|-   [コード分析規則セットの参照](../code-quality/code-analysis-rule-set-reference.md)|  
|**Team Foundation Server でのコード分析の統合:** [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]チェックイン ポリシーにより、開発チームのすべてのコード チェックインがコード分析標準の共通セットを満たしていることを確認します。|-   [方法: チーム プロジェクト チェックイン ポリシーとコード プロジェクト規則セットを同期](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)|



