---
title: "マネージ コードの &quot;セキュリティ規則&quot; 規則セット | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# マネージ コードの &quot;セキュリティ規則&quot; 規則セット
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

潜在的なセキュリティ上の問題の検出件数を最大化するために、"Microsoft セキュリティ規則" 規則セットを使用してください。  
  
|規則|説明|  
|--------|--------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|SQL クエリのセキュリティ脆弱性を確認|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|汎用ハンドラーの CLSCompliant でない例外をキャッチします|  
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|命令型のセキュリティを確認します|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|読み取り専用の変更可能な参照型を宣言しません|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|配列フィールドを読み取り専用にすることはできません|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|アサートをセキュリティで保護します|  
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|拒否および許可のみの使用を確認します|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|値型での宣言セキュリティを確認します|  
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|表示するイベント ハンドラーを確認します|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|ポインターは参照可能にすることはできません|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|セキュリティで保護された型はフィールドを公開してはなりません|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|メソッド セキュリティは型のスーパーセットでなければなりません|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|ネイティブ リソースを使用しているときには GC.KeepAlive を呼び出します|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA メソッドは APTCA メソッドのみを呼び出すことができます|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型は APTCA 基本型のみを拡張することができます|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|SuppressUnmanagedCodeSecurityAttribute の使用法を確認してください|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|プライベート インターフェイスを満たすメソッドをシールします|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|シリアル化コンストラクターをセキュリティで保護します|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|静的コンストラクターはプライベートでなければなりません|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|リンク要求を含むメソッドを間接的に公開しません|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|オーバーライドのリンク確認要求はベースと同様です。|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|脆弱性のある finally 句を外側の try でラップします|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|型のリンク要求には継承要求が必要です|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|セキュリティが重要な定数は透過的です。|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|セキュリティが重要な型は型の等価性に参加しないことがあります。|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|既定のコンストラクターは、基本型の既定コンストラクターと同程度以上、重要であることが必要|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|デリゲートは、一貫した透過性でメソッドにバインドしなければなりません|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|メソッドと基本メソッドをオーバーライドする場合、一貫した透過性を保持する必要があります|  
|[CA2135](../Topic/CA2135:%20Level%202%20assemblies%20should%20not%20contain%20LinkDemands.md)|レベル 2 アセンブリは LinkDemands を含めることはできません。|  
|[CA2136](../Topic/CA2136:%20Members%20should%20not%20have%20conflicting%20transparency%20annotations.md)|メンバーが矛盾した透過性のある注釈を指定する必要はありません。|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透過的メソッドは、検証可能な IL だけです|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透過的メソッドが、SuppressUnmanagedCodeSecurity 属性のメソッドを呼び出すことはできません|  
|[CA2139](../Topic/CA2139:%20Transparent%20methods%20may%20not%20use%20the%20HandleProcessCorruptingExceptions%20attribute.md)|透過的メソッドは HandleProcessCorruptingExceptions 属性を使用できない場合もあります。|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透過的なコードではセキュリティが重要な重要項目を参照することはできません。|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透過的メソッドは LinkDemands を満たすことはできません|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透過的なコードでは、LinkDemand で保護することはできません。|  
|[CA2143](../Topic/CA2143:%20Transparent%20methods%20should%20not%20use%20security%20demands.md)|透過的メソッドが、セキュリティ確認要求を使用する必要があります。|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透過的なコードでは、バイト配列からアセンブリを読み込むことはできません。|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透過的セキュリティ メソッドは、SuppressUnmanagedCodeSecurityAttribute と修飾しないでください。|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型は、基本型およびインターフェイスと同程度以上、重要でなければならない|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透過的メソッドにはセキュリティ アサートを使用できない場合もあります。|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透過的メソッドは、ネイティブ コードを呼び出す必要があります|  
|[CA2210](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|アセンブリには有効な厳密な名前が必要です|