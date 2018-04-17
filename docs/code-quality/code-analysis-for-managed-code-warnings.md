---
title: コード分析のマネージ コードの警告の |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d6c1cb3658d1c1f896a94bd2b1c89c5e28a5118a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="code-analysis-for-managed-code-warnings"></a>マネージ コードの警告に対応するコードの解析
マネージ コード分析ツールには、マネージ コード ライブラリの規則違反を示す警告機能があります。 警告は、デザイン、ローカリゼーション、パフォーマンス、セキュリティなどの規則の区分に分類されています。 個々の警告によって、マネージ コード分析規則の違反がわかります。 ここでは、マネージ コード分析の各警告について、詳細な説明と例を紹介します。  
  
 次の表に、各警告で示される情報の種類を示しています。  
  
|アイテム|説明|  
|----------|-----------------|  
|型|規則の TypeName。|  
|CheckId|規則の一意の識別子。 CheckId とカテゴリは、ソース内で警告の省略表記として使用されます。|  
|カテゴリ|警告のカテゴリ。|  
|互換性に影響する変更点|規則違反を修正することが、互換性に影響する変更点かどうかを示します。 互換性に影響する変更点とは、違反の原因となった対象に対して依存関係を持つアセンブリが、新たに修正したバージョンで再コンパイルされないこと、または変更によって実行時にエラーになる可能性があることを示します。 複数の修正を適用でき、互換性に影響する変更点があるものとないものがある場合、"あり" と "なし" を併記しています。|  
|原因|規則に従って警告が生成される原因になった特定のマネージ コード。|  
|説明|警告の背景にある問題について説明します。|  
|違反の修正方法|規則に適合し、警告が生成されないようにソース コードを変更する方法について説明します。|  
|警告を抑制する状況|規則による警告を抑制しても安全な場合について説明します。|  
|コード例|規則に違反する例と、規則に適合する修正した例を示します。|  
|関連する警告|関連する警告。|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|||  
|-|-|  
|[警告を Checkid 別](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|すべての警告を CheckId 別に一覧表示します。|  
|[暗号化警告](../code-quality/cryptography-warnings.md)|暗号化の適切な使用によって、より安全なライブラリとアプリケーションをサポートする警告です。|  
|[デザインの警告](../code-quality/design-warnings.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] デザイン ガイドラインで規定されている、適切なライブラリ デザインをサポートする警告です。|  
|[グローバリゼーションに関する警告](../code-quality/globalization-warnings.md)|国際対応ライブラリおよびアプリケーションをサポートする警告です。|  
|[相互運用性の警告](../code-quality/interoperability-warnings.md)|COM クライアントとの相互作用をサポートする警告です。|  
|[保守性の警告](../code-quality/maintainability-warnings.md)|ライブラリとアプリケーションの保守をサポートする警告です。|  
|[Mobility Warnings](../code-quality/mobility-warnings.md)|電力の効率的な使用をサポートする警告です。|  
|[名前付けに関する警告](../code-quality/naming-warnings.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] デザイン ガイドラインの名前付け規則の順守をサポートする警告です。|  
|[パフォーマンスに関する警告](../code-quality/performance-warnings.md)|高パフォーマンスのライブラリとアプリケーションをサポートする警告です。|  
|[Portability Warnings](../code-quality/portability-warnings.md)|異なるプラットフォーム間の移植性をサポートする警告です。|  
|[信頼性の警告](../code-quality/reliability-warnings.md)|メモリやスレッドの適切な使用など、ライブラリとアプリケーションの信頼性をサポートする警告です。|  
|[セキュリティの警告](../code-quality/security-warnings.md)|より安全なライブラリとアプリケーションをサポートする警告です。|  
|[使用法に関する警告](../code-quality/usage-warnings.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]の適切な使用をサポートする警告です。|  
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|チェックインにおいてコード分析ポリシーに適合しない場合に発生するエラーです。|