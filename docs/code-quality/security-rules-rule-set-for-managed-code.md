---
title: マネージ コードの "セキュリティ規則" 規則セット
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6712454fad2acaf57b3cb4d8f1740366a396ec6e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="security-rules-rule-set-for-managed-code"></a>マネージ コードの "セキュリティ規則" 規則セット
Microsoft のセキュリティ規則規則が報告された潜在的なセキュリティ問題の数を最大化するセットを含める必要があります。

|ルール|説明|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|セキュリティの脆弱性について、SQL クエリを確認します。|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|非 CLSCompliant の例外ハンドラーでキャッチ全般|
|[CA 2103](../code-quality/ca2103-review-imperative-security.md)|命令型のセキュリティをレビュー|
|[CA 2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|読み取りのみ変更可能な参照型を宣言しません|
|[CA 2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|配列フィールドいない読み取り専用にします。|
|[CA 2106](../code-quality/ca2106-secure-asserts.md)|セキュリティで保護されたアサートします。|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Deny し、permitonly の用法をレビュー|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型で宣言型セキュリティを再確認します|
|[CA 2109](../code-quality/ca2109-review-visible-event-handlers.md)|表示するイベント ハンドラーを確認します|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターを表示することはできません。|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開する必要があります。|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッドのセキュリティは、型のスーパー セットをする必要があります。|
|[CA 2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|GC を呼び出します。KeepAlive ネイティブ リソースを使用する場合|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出す必要があります。|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型を拡張する必要がありますのみ|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute の使用法の確認|
|[CA 2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|プライベート インターフェイスを満たすメソッドをシールします|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|セキュリティで保護されたシリアル化コンス トラクター|
|[CA 2121](../code-quality/ca2121-static-constructors-should-be-private.md)|静的コンス トラクターはプライベートでなければなりません|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク確認要求を持つメソッドを間接的に公開しません|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク要求をベースと同一にする必要があります。|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|脆弱なラップ finally 句の外側 try します。|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|型のリンク要求には、継承要求が必要です。|
|[CA 2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|セキュリティ上重要な定数は透過的にする必要があります。|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティ クリティカルな型は型の等価性に参加できません。|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンス トラクターは、少なくとも基本データ型の既定のコンス トラクターとしてほど重要である必要があります。|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは透過性の整合メソッドにバインドする必要があります。|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|基本メソッドをオーバーライドする場合、メソッドは透過性の整合性を保つ必要があります。|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|レベル 2 のアセンブリは Linkdemand を含めることはできません。|
|[CA 2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|メンバーには透過性注釈の競合することはできません。|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|透過的メソッドは検証可能な IL のみを含める必要があります。|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出さないでください。|
|[CA 2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|透過的メソッドは、HandleProcessCorruptingExceptions 属性を使用しない場合があります。|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードは、セキュリティ上重要な項目を参照しないでください。|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは、Linkdemand を満たしていない必要があります。|
|[CA 2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透過的なコードが Linkdemand で保護されていない必要があります。|
|[CA 2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|透過的メソッドは、セキュリティ確認要求を使用しないでください。|
|[CA 2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透過的なコードは、バイト配列からアセンブリを読み込めません|
|[CA 2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透過的メソッドを SuppressUnmanagedCodeSecurityAttribute で修飾いない必要があります。|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|種類は、少なくともほど重要で、基本型およびインターフェイスである必要があります。|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドは、セキュリティを使用しない場合がありますアサート|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|ネイティブ コードに透過的なメソッドを呼び出してはなりません。|
|[CA 2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|アセンブリは有効な厳密な名前である必要があります。|