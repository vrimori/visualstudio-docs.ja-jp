---
title: '2117: APTCA 型は APTCA 基本型を拡張するのみ |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 409133c173f497b1f21b36c7d8c4c89561c0aa15
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171458"
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA 型は APTCA 基本型のみを拡張することができます
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|
|CheckId|CA2117|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型を持つアセンブリ、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性は、属性を持たないアセンブリで宣言された型から継承します。

## <a name="rule-description"></a>規則の説明
 既定では、厳密な名前付きアセンブリのパブリックまたはプロテクト型は暗黙的にによって保護、[継承確認要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)完全な信頼。 アセンブリの厳密な名前が付いて、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、継承確認要求が無効にします。 これにより、完全な信頼がない型で公開されている型継承可能なアセンブリで宣言します。

 APTCA 属性が完全に信頼されたアセンブリにあり、アセンブリの型が部分的に信頼された呼び出し元が許可されない型から継承、セキュリティ上の弱点になります。 2 つの型の場合`T1`と`T2`次の条件を満たしている、悪意のある呼び出し元は、型を使用できる`T1`を保護する完全な信頼の暗黙的な継承確認要求をバイパスする`T2`:

-   `T1` パブリック型は APTCA 属性を持つ完全に信頼されたアセンブリで宣言されます。

-   `T1` 型から継承`T2`そのアセンブリの外部にします。

-   `T2`アセンブリは、APTCA 属性がないと、そのため、することはできません部分的に信頼されたアセンブリ内の型によって継承可能な。

 部分的に信頼された型`X`から継承できます`T1`、それにアクセスで宣言されている継承されたメンバー`T2`します。 `T2` APTCA 属性、その直接の派生型がありません (`T1`) は完全な信頼の継承確認要求を満たす必要があります`T1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ リスクは`X`を保護する継承確認要求を満たすに関与しません`T2`信頼されていないサブクラス化からします。 このため、APTCA 属性型は、属性がない型を拡張する必要があります。

 別のセキュリティ問題と一般的な 1 つではおそらく、派生型です (`T1`)、プログラマのエラーからメンバーを公開する保護された完全な信頼を必要とする型から (`T2`)。 この場合、信頼されていない呼び出し元情報にアクセスが完全に信頼された型にのみ使用可能な場合があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 APTCA 属性を必要としないアセンブリ内の違反によって報告された型の場合は、それを削除します。

 APTCA 属性が必要な場合は、型に完全な信頼の継承確認要求を追加します。 これは、信頼されていない型を継承から保護します。

 APTCA 属性違反によって報告された基本型のアセンブリを追加して、違反を修正することになります。 最初の実行、アセンブリ内のすべてのコードと、アセンブリに依存するすべてのコードの集中的なセキュリティ レビューをしなくてもこれを行う操作を行います。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を安全に抑制するには、型によって公開されている保護されたメンバーは許可しないこと直接的または間接的に呼び出し元が信頼されていない機密情報、操作、または、破壊的な方法で使用できるリソースにアクセスすることを確認する必要があります。

## <a name="example"></a>例
 次の例では、2 つのアセンブリとテスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは、APTCA 属性がないと、部分的に信頼された型からは継承できません (によって表される`T2`上記の説明で)。

 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptcaInherit/cs/FxCop.Security.NoAptcaInherit.cs#1)]

## <a name="example"></a>例
 表される 2 つ目のアセンブリは、`T1`上記の説明では、完全に信頼された、部分的に信頼された呼び出し元を許可します。

 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptcaInherit/cs/FxCop.Security.YesAptcaInherit.cs#1)]

## <a name="example"></a>例
 テストの種類によって表される`X`上記の説明では、部分的に信頼されたアセンブリ。

 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaInherit/cs/FxCop.Security.TestAptcaInherit.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **満たす怪しいに 2003 年 2 月 22 12時 00分: 00 AM です。** 
**からテスト: sunny meadow**
**sunny meadow で 2003 年 2 月 22 12時 00分: 00 AM です。**
## <a name="related-rules"></a>関連規則
 [CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)

## <a name="see-also"></a>関連項目
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework アセンブリから呼び出すことで部分的に信頼されているコード](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d)[からライブラリを使用して部分的に信頼されているコード](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74)[継承確認要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)




