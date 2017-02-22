---
title: "コード分析規則セットの参照 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コード分析、規則セット"
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 43
caps.handback.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# コード分析規則セットの参照
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)]、[!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]、または [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)] でマネージ コード プロジェクトのコード分析を構成するときに、組み込みの*規則セット*の一覧が示されます。  いずれかの標準規則セットを使用することも、プロジェクト要件を満たすように規則セットをカスタマイズすることもできます。  
  
## 使用できる規則セット  
 既定の規則セット一覧を次の表に示します。  
  
|||  
|-|-|  
|["すべての規則" 規則セット](../code-quality/all-rules-rule-set.md)|この規則セットにはすべての規則が含まれます。  この規則セットを実行すると、多数の警告が報告される可能性があります。  この規則セットは、コード内のすべての問題を全体的に把握する場合に使用してください。  これは、用途を絞った各規則セットのうち、どれがプロジェクトに対して最も適切かを判断するのに役立ちます。|  
|[マネージ コードの "基本正確性規則" 規則セット](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|これらの規則は、フレームワーク API の使用の際の論理エラー、およびよくある失敗に関するものです。  この規則セットは、最小推奨規則で報告された警告の一覧から、さらに詳しい情報へと掘り下げる必要がある場合に使用してください。|  
|[マネージ コードの "基本デザイン ガイドライン規則" 規則セット](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|これらの規則は、コードをわかりやすく、また使いやすくするためのベスト プラクティスに関するものです。  この規則セットは、プロジェクトにライブラリ コードが含まれる場合や、コードをメンテナンスしやすくするためにべスト プラクティスを適用する場合に使用してください。|  
|[マネージ コードの "拡張正確性規則" 規則セット](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|これらの規則は、正確性に関する基本的な規則をさらに掘り下げて、論理エラーやフレームワーク使用エラーの検出範囲を最大化するためのものです。  COM 相互運用機能やモバイル アプリケーションなど、特定のシナリオに重点が置かれています。  これらのシナリオのいずれかに該当するプロジェクトがある場合や、プロジェクト内の問題をさらに細かく探す必要がある場合には、この規則セットの使用を検討してください。|  
|[マネージ コードの "拡張デザイン ガイドライン規則" 規則セット](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|これらの規則は、基本デザイン ガイドライン規則をさらに掘り下げて、使用可能性と保守容易性に関する問題の検出範囲を最大化するためのものです。  特に、命名に関するガイドラインに重点が置かれています。  プロジェクトにライブラリ コードが含まれる場合や、コード記述の方法に最高レベルの基準を適用してメンテナンスを容易にするには、この規則セットの使用を検討してください。|  
|[マネージ コードの "グローバリゼーション規則" 規則セット](../code-quality/globalization-rules-rule-set-for-managed-code.md)|これらの規則は、複数の言語、ロケール、およびカルチャが使用される環境において、データの正しい表示を妨げる問題に対処する規則です。  アプリケーションをローカライズまたはグローバル化する場合には、この規則セットを使用してください。|  
|[マネージ コードの "マネージ最小規則" 規則セット](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|これらの規則は、コード分析が最も厳密に行われる、コードの最も重大な問題に関するものです。規則は少数で、限られた Visual Studio エディションだけで使用されることが意図されています。他の Visual Studio エディションでは、MinimumRecommendedRules.ruleset を使用してください。|  
|[マネージ コードの "マネージ推奨規則" 規則セット](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|これらの規則は、セキュリティ ホール、アプリケーション クラッシュ、その他の重要な論理エラーやデザイン エラーなど、コードに含まれる最も重要な問題に関するものです。  プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。|  
|["混合最小規則" 規則セット](../code-quality/mixed-minimum-rules-rule-set.md)|これらの規則は、共通言語ランタイムをサポートする C\+\+ プロジェクトの最も重大な問題 \(潜在的なセキュリティ ホールやアプリケーションのクラッシュなど\) に関するものです。  共通言語ランタイムをサポートする C\+\+ プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。|  
|["混合推奨規則" 規則セット](../code-quality/mixed-recommended-rules-rule-set.md)|これらの規則は、共通言語ランタイムをサポートする C\+\+ プロジェクトの最も一般的で重大な問題 \(潜在的なセキュリティ ホールやアプリケーションのクラッシュ、その他の重要な論理エラーや設計エラーなど\) に関するものです。  共通言語ランタイムをサポートする C\+\+ プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。この規則セットは、Visual Studio Professional Edition 以上で構成するように設計されています。|  
|["ネイティブ最小規則" 規則セット](../code-quality/native-minimum-rules-rule-set.md)|これらの規則は、ネイティブ コードの最も重大な問題 \(潜在的なセキュリティ ホールやアプリケーションのクラッシュなど\) に関するものです。  ネイティブ プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。|  
|["ネイティブ推奨規則" 規則セット](../code-quality/native-recommended-rules-rule-set.md)|これらの規則は、ネイティブ コードで最も重大で一般的な問題 \(潜在的なセキュリティ ホールやアプリケーションのクラッシュなど\) に関するものです。ネイティブ プロジェクトにカスタムの規則セットを作成する場合は、必ずこの規則セットを含める必要があります。この規則セットは、Visual Studio Professional Edition 以上で動作するように設計されています。|  
|[マネージ コードの "セキュリティ規則" 規則セット](../code-quality/security-rules-rule-set-for-managed-code.md)|この規則セットには、Microsoft のセキュリティ規則がすべて含まれます。  セキュリティ問題の検出範囲を最大化するには、この規則セットを使用してください。|