---
title: "CA2117: APTCA 型は APTCA 基本型を拡張して必要があるだけ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2117
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
helpviewer_keywords:
- AptcaTypesShouldOnlyExtendAptcaBaseTypes
- CA2117
ms.assetid: c505b586-2f1e-47cb-98ee-a5afcbeda70f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 977f721ed45343e247f8639accc0fa5dc83263c6
ms.sourcegitcommit: f0ddee934713ea9126fa107018a57a94a05eafd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="ca2117-aptca-types-should-only-extend-aptca-base-types"></a>CA2117: APTCA 型は APTCA 基本型のみを拡張することができます
|||  
|-|-|  
|TypeName|AptcaTypesShouldOnlyExtendAptcaBaseTypes|  
|CheckId|CA2117|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型を持つアセンブリ、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性は、属性を持たないアセンブリで宣言された型から継承します。  
  
## <a name="rule-description"></a>規則の説明  
 既定では、厳密な名前付きアセンブリでパブリックまたはプロテクトの型は暗黙的にによって保護、<xref:System.Security.Permissions.SecurityAction.InheritanceDemand>完全な信頼。 マークされたアセンブリの厳密な名前、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、継承確認要求が無効にします。 これにより、完全な信頼がない型による継承可能なアセンブリで宣言された型の公開されています。  
  
 APTCA 属性が完全に信頼されたアセンブリでは、上に存在し、アセンブリの型が部分的に信頼された呼び出し元が許可されていない型から継承、セキュリティ上の弱点が可能性があります。 2 つの型する場合`T1`と`T2`、次の条件を満たしている、悪意のある呼び出し元は、型を使用できる`T1`を保護する暗黙的な完全信頼の継承確認要求を省略する`T2`:  
  
-   `T1`APTCA 属性を持つ完全に信頼されたアセンブリではパブリック型が宣言されます。  
  
-   `T1`型から継承`T2`アセンブリ外です。  
  
-   `T2`アセンブリは APTCA 属性がないと、そのため、することはできません部分的に信頼されたアセンブリ内の型によって継承可能な。  
  
 部分的に信頼される種類`X`から継承できます`T1`、それにアクセスで宣言されている継承されたメンバー`T2`です。 `T2` APTCA 属性、その直接の派生型がありません (`T1`) は完全な信頼の継承確認要求を満たす必要があります`T1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ上のリスクがあるため`X`を保護する継承確認要求を満たすには参加しません`T2`信頼されていないサブクラス化からします。 このため、APTCA 属性を持つ型は、属性がない型を拡張する必要があります。  
  
 別のセキュリティ問題、および一般的なものではおそらくは、派生型 (`T1`)、プログラマ エラーを通じてメンバーを公開する保護された完全な信頼を必要とする型から (`T2`)。 この場合、信頼されていない呼び出し元にアクセスについては、完全信頼の型でのみ使用可能にする必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 APTCA 属性が不要なアセンブリでの違反によって報告された型の場合は、それを削除します。  
  
 APTCA 属性が必要な場合は、型に完全な信頼の継承確認要求を追加します。 これは、信頼されていない型によって継承から保護します。  
  
 違反によって報告された基本型のアセンブリに APTCA 属性を追加することで違反を修正することができます。 こうしない最初に、アセンブリ内のすべてのコードとアセンブリに依存するすべてのコードの処理を要するセキュリティをレビューを実行しなくてもします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を安全に抑制するには、こと、型によって公開されるメンバーを保護された直接または間接的に許可しない機密情報、操作、または破壊的な方法で使用できるリソースにアクセスする、信頼されていない呼び出し元を確認する必要があります。  
  
## <a name="example"></a>例  
 次の例では、2 つのアセンブリと、テスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは APTCA 属性がないと、部分的に信頼された型からは継承できません (によって表される`T2`上記の説明で)。  
  
 [!code-csharp[FxCop.Security.NoAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_1.cs)]  
  
## <a name="example"></a>例  
 によって表される 2 番目のアセンブリ`T1`上記の説明では、完全に信頼された、部分的に信頼された呼び出し元を許可します。  
  
 [!code-csharp[FxCop.Security.YesAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_2.cs)]  
  
## <a name="example"></a>例  
 テストの種類によって表される`X`上記の説明では、部分的に信頼されたアセンブリです。  
  
 [!code-csharp[FxCop.Security.TestAptcaInherit#1](../code-quality/codesnippet/CSharp/ca2117-aptca-types-should-only-extend-aptca-base-types_3.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **Shady がで満たす 2003 年 2 月 22/12時 00分: 00 AM です。**  
**Sunny meadow からテスト:**  
**Sunny meadow で満たす 2003 年 2 月 22/12時 00分: 00 AM です。**   
## <a name="related-rules"></a>関連規則  
 [CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)  
  
## <a name="see-also"></a>関連項目  
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)   
 [部分信頼コードからライブラリを使用します。](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
