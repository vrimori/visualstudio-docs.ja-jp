---
title: マネージ コードのセキュリティ規則のルールの設定 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d41f005109960b1384471483e7279c60e92c4b4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49266514"
---
# <a name="security-rules-rule-set-for-managed-code"></a>マネージド コードの "セキュリティ規則" 規則セット
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft のセキュリティ規則ルールが報告される潜在的なセキュリティの問題の数を最大化するセットを含める必要があります。  
  
|ルール|説明|  
|----------|-----------------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL クエリのセキュリティの脆弱性を確認します。|  
|[CA 2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|汎用ハンドラーで非 CLSCompliant の例外をキャッチします。|  
|[CA 2103](../code-quality/ca2103-review-imperative-security.md)|強制セキュリティを確認してください。|  
|[CA 2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|読み取りのみ変更可能な参照型を宣言しません|  
|[CA 2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|配列フィールドいない読み取り専用にします。|  
|[CA 2106](../code-quality/ca2106-secure-asserts.md)|セキュリティで保護されたアサートします。|  
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Deny し、permitonly の用法|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型で宣言型セキュリティを確認してください。|  
|[CA 2109](../code-quality/ca2109-review-visible-event-handlers.md)|表示するイベント ハンドラーをレビューします|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターを表示することはできません。|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開する必要があります。|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッドのセキュリティの種類のスーパー セットである必要があります。|  
|[CA 2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|GC を呼び出します。KeepAlive ネイティブ リソースを使用する場合|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出す必要があります。|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型のみを拡張する必要があります。|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute の使用法の確認|  
|[CA 2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|プライベート インターフェイスを満たすメソッドをシールします|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|セキュリティで保護されたシリアル化コンス トラクター|  
|[CA 2121](../code-quality/ca2121-static-constructors-should-be-private.md)|静的コンス トラクターはプライベートでなければなりません|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク確認要求でメソッドを間接的に公開できません。|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク確認要求は基本同一である必要があります。|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|ラップの脆弱性のある finally 句の外側を try します。|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|型のリンク要求には、継承要求が必要です。|  
|[CA 2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|セキュリティ上重要な定数は透過的にする必要があります。|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティ クリティカルな型は型の等価性に参加できません。|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンス トラクターは、少なくとも基本型の既定のコンス トラクターと同程度に重要である必要があります。|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは透過性の整合メソッドにバインドする必要があります。|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|メソッドは基本メソッドをオーバーライドするときに透過性の整合性を保つ必要があります。|  
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|レベル 2 のアセンブリは Linkdemand を含めることはできません。|  
|[CA 2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|メンバーには、透過性注釈の競合はありません。|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透過的メソッドは、検証可能な IL のみを含める必要があります。|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出す必要がありますいません。|  
|[CA 2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用可能性があります。|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードは、セキュリティ上重要な項目を参照する必要があります。|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは、Linkdemand を満たしていませんする必要があります。|  
|[CA 2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|LinkDemands を透過的なコードを保護する必要がありません。|  
|[CA 2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透過的メソッドは、セキュリティ要求を使用しないでください。|  
|[CA 2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透過的なコードは、バイト配列からアセンブリを読み込めません|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透過的なメソッドが、SuppressUnmanagedCodeSecurityAttribute で修飾されていない必要があります。|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|種類は、少なくとも、基本型およびインターフェイスと同程度に重要である必要があります。|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドは、セキュリティを使用しない可能性がありますアサート|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透過的メソッドはネイティブ コードを呼び出す必要がありますいません。|  
|[CA 2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|アセンブリが有効な厳密な名前|



