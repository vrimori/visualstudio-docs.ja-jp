---
title: コード分析を使用してマネージ コードの品質の分析 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis,managed code
- managed code analyis
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e034db6fc7383ea5f944900713dffe1cc3e78473
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263902"
---
# <a name="analyzing-managed-code-quality-by-using-code-analysis"></a>コード分析を使用したマネージド コードの品質の分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio のコード分析ツールを使用すると、安全ではないデータ アクセス、使用法違反、デザイン上の問題など、コード内の潜在的な問題を検出できます。 コード分析の動作環境は、.NET Framework、ネイティブ (C と C++)、およびデータベース アプリケーションです。 マネージ コードのコード分析で規則を整理する*ルール セット*を対象とするコーディングの問題を特定します。  
  
## <a name="common-tasks"></a>一般的なタスク  
  
|一般的なタスク|関連する参照先|  
|------------------|------------------------|  
|**実習を行う:** 単純な .NET Framework アプリケーションの欠陥を修正することによってコード分析の基礎を学習します。|-   [チュートリアル: マネージ コードを分析によるコード障害の検出](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**プロジェクトのコード分析を構成する:** 管理用の規則はコードは、セキュリティ、デザインなど、特定の分野を対象とする規則セットに分類されます。 Microsoft の標準の規則セットの 1 つを使用することも、独自のセットを作成することもできます。|-   [マネージ コードの概要のコード分析](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [コード分析規則のグループに規則を使用して設定します。](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [SuppressMessage 属性を使用して警告を抑制します。](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**コード分析を実行します。** プロジェクトの構成がビルドされるたびに自動的に実行されるコード分析を指定すると、プロジェクトに手動でコード分析を実行することができます。|-   [方法: 有効にして、自動コード分析を無効にします。](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)<br />-   [方法: コード分析を手動で実行](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**コード分析の結果の分析:** コード分析の警告とエラーは、コード分析 ウィンドウに一覧表示します。 警告またはエラーのタイトルを選択すると、警告に関する追加情報を表示し、規則を発動したソース コード行を表示および強調表示することができます。 警告 ID を選択すると、問題の解決方法に関する情報と例が含まれた、MSDN ライブラリの詳細情報を表示できます。|-   [方法: マネージ コードの障害を表示](../code-quality/how-to-view-managed-code-defects.md)<br />-   [マネージ コードの警告のコード分析](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [警告を checkid 別](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名メソッドとコード分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**コード分析、開発ライフ サイクルと統合:** でチェックイン ポリシー[!INCLUDE[esprscc](../includes/esprscc-md.md)]開発チームが有効にするすべてのコードのチェックインがあるかどうかを確認するコード分析標準の共通セットに対応します。 コード分析規則違反の作業項目は、[エラー一覧] ウィンドウで簡単な手順により作成できます。|-   [チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [方法: チーム プロジェクト チェックイン ポリシーとコード プロジェクト規則セットを同期](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [方法: マネージ コードの障害に対する作業項目の作成](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|



