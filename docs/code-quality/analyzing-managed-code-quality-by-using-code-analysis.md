---
title: "コード分析を使用したマネージ コードの品質の分析 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード分析、マネージ コード"
  - "マネージ コード分析"
ms.assetid: 68510a55-da51-4381-81a5-0feba76b8b4f
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# コード分析を使用したマネージ コードの品質の分析
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio のコード分析ツールを使用すると、安全ではないデータ アクセス、使用法違反、デザイン上の問題など、コード内の潜在的な問題を検出できます。  コード分析の動作環境は、.NET Framework、ネイティブ \(C と C\+\+\)、およびデータベース アプリケーションです。  マネージ コードのコード分析では、特定のコードの問題を対象にした規則が*規則セット*にまとめられます。  
  
## 一般的なタスク  
  
|一般的なタスク|関連する参照先|  
|-------------|-------------|  
|**実習を行う:** 単純な .NET Framework アプリケーションの問題を修正することで、コード分析の基礎を学習します。|-   [チュートリアル: マネージ コードの分析によるコード障害の検出](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)|  
|**プロジェクトに対してコード分析を構成する:** マネージ コード用の規則は、セキュリティ、デザインなどの特定の分野を対象とする規則セットにまとめられます。  Microsoft の標準の規則セットの 1 つを使用することも、独自のセットを作成することもできます。|-   [マネージ コードに対するコード分析の概要](../code-quality/code-analysis-for-managed-code-overview.md)<br />-   [規則セットを使用したコード分析規則のグループ化](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)<br />-   [SuppressMessage 属性を使用した警告の抑制](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md)|  
|**コード分析を実行する:** プロジェクトの構成がビルドされるたびにコード分析が自動的に実行されるように指定することも、プロジェクトに対して手動でコード分析を実行することもできます。|-   [方法: 自動コード分析を有効\/無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Automatic%20Code%20Analysis%20for%20Managed%20Code.md)<br />-   [方法: 手動でコード分析を実行する](../code-quality/how-to-run-code-analysis-manually-for-managed-code.md)|  
|**コード分析結果を分析する:** コード分析の警告とエラーは、\[コード分析\] ウィンドウに一覧表示されます。  警告またはエラーのタイトルを選択すると、警告に関する追加情報を表示し、規則を発動したソース コード行を表示および強調表示することができます。  警告 ID を選択すると、問題の解決方法に関する情報と例が含まれた、MSDN ライブラリの詳細情報を表示できます。|-   [方法 : マネージ コードの障害を表示する](../code-quality/how-to-view-managed-code-defects.md)<br />-   [マネージ コードの警告に対応するコードの解析](../code-quality/code-analysis-for-managed-code-warnings.md)<br />-   [警告 \(CheckId 別\)](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)<br />-   [匿名メソッドとコード分析](../code-quality/anonymous-methods-and-code-analysis.md)|  
|**コード分析を開発ライフサイクルと統合する:** [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)]のチェックイン ポリシーにより、開発チームは、すべてのコード チェックインがコード分析標準の共通セットに対応していることを確認できます。  コード分析規則違反の作業項目は、\[エラー一覧\] ウィンドウで簡単な手順により作成できます。|-   [チーム プロジェクト チェックイン ポリシーによるコード品質の向上](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)<br />-   [方法: コード プロジェクト規則セットをチーム プロジェクトのチェックイン ポリシーと同期させる](../code-quality/how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy.md)<br />-   [方法: マネージ コードの障害に対する作業項目を作成する](../code-quality/how-to-create-a-work-item-for-a-managed-code-defect.md)|