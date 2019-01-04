---
title: CA2117:APTCA 型は APTCA 基本型のみを拡張することができます
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bc2086038187093397d53e80b1a26f2006c32c80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873354"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117:APTCA 型は APTCA 基本型のみを拡張することができます

|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

パブリックまたはプロテクト型を持つアセンブリ、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性は、属性を持たないアセンブリで宣言された型から継承します。

## <a name="rule-description"></a>規則の説明

既定では、厳密な名前付きアセンブリのパブリックまたはプロテクト型は暗黙的にによって保護、 [InheritanceDemand](xref:System.Security.Permissions.SecurityAction#System_Security_Permissions_SecurityAction_InheritanceDemand)完全な信頼。 アセンブリの厳密な名前が付いて、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、継承確認要求が無効にします。 継承確認要求なしにアセンブリに宣言されている公開されている型は完全な信頼がない型で継承します。

APTCA 属性が完全に信頼されたアセンブリにあり、アセンブリの型が部分的に信頼された呼び出し元が許可されない型から継承、セキュリティ上の弱点になります。 2 つの型の場合`T1`と`T2`次の条件を満たしている、悪意のある呼び出し元は、型を使用できる`T1`を保護する完全な信頼の暗黙的な継承確認要求をバイパスする`T2`:

- `T1` パブリック型は APTCA 属性を持つ完全に信頼されたアセンブリで宣言されます。

- `T1` 型から継承`T2`そのアセンブリの外部にします。

- `T2`アセンブリは、APTCA 属性がないと、そのため、することはできません部分的に信頼されたアセンブリ内の型によって継承可能な。

部分的に信頼された型`X`から継承できます`T1`、それにアクセスで宣言されている継承されたメンバー`T2`します。 `T2` APTCA 属性、その直接の派生型がありません (`T1`) は完全な信頼の継承確認要求を満たす必要があります`T1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ リスクは`X`を保護する継承確認要求を満たすに関与しません`T2`信頼されていないサブクラス化からします。 このため、APTCA 属性型は、属性がない型を拡張する必要があります。

別のセキュリティ問題と一般的な 1 つではおそらく、派生型です (`T1`)、プログラマのエラーからメンバーを公開する保護された完全な信頼を必要とする型から (`T2`)。 この問題が発生すると、信頼されていない呼び出し元によって完全に信頼された型にのみ使用可能な必要のある情報へのアクセスが増えます。

## <a name="how-to-fix-violations"></a>違反の修正方法

APTCA 属性を必要としないアセンブリ内の違反によって報告された型の場合は、それを削除します。

APTCA 属性が必要な場合は、型に完全な信頼の継承確認要求を追加します。 継承確認要求は、信頼されていない型を継承から保護します。

APTCA 属性違反によって報告された基本型のアセンブリを追加して、違反を修正することになります。 最初の実行、アセンブリ内のすべてのコードと、アセンブリに依存するすべてのコードの集中的なセキュリティ レビューをしなくてもこれを行う操作を行います。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

この規則による警告を安全に抑制するには、型によって公開されている保護されたメンバーは許可しないこと直接的または間接的に呼び出し元が信頼されていない機密情報、操作、または、破壊的な方法で使用できるリソースにアクセスすることを確認する必要があります。

## <a name="example"></a>例

次の例では、2 つのアセンブリとテスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは、APTCA 属性がないと、部分的に信頼された型からは継承できません (によって表される`T2`上記の説明で)。

[!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]

表される 2 つ目のアセンブリは、`T1`上記の説明では、完全に信頼された、部分的に信頼された呼び出し元を許可します。

[!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]

テストの種類によって表される`X`上記の説明では、部分的に信頼されたアセンブリ。

[!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]

この例を実行すると、次の出力が生成されます。

```txt
Meet at the shady glen 2/22/2003 12:00:00 AM!
From Test: sunny meadow
Meet at the sunny meadow 2/22/2003 12:00:00 AM!
```

## <a name="related-rules"></a>関連するルール

[CA2116:APTCA メソッドは APTCA メソッドのみを呼び出す必要があります。](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)
- [部分信頼コードからのライブラリの使用](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
