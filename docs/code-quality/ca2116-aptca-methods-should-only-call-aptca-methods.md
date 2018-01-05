---
title: "CA2116: APTCA メソッドは APTCA メソッドを呼び出すだけ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a3a7818c3d758e8e92724af37dfe955f9a466746
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116: APTCA メソッドは APTCA メソッドのみを呼び出すことができます
|||  
|-|-|  
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|  
|CheckId|CA2116|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 アセンブリ内のメソッド、<xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>属性は、属性を持たないアセンブリでメソッドを呼び出します。  
  
## <a name="rule-description"></a>規則の説明  
 既定では、アセンブリに厳密な名前のパブリックまたはプロテクト メソッドは暗黙的にによって保護、[リンク確認要求](/dotnet/framework/misc/link-demands)は完全な信頼のみ完全に信頼されている呼び出し元は、厳密な名前のアセンブリにアクセスできます。 マークされたアセンブリの厳密な名前、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性には、この保護はありません。 属性には、アセンブリにイントラネットまたはインターネットから実行されるコードなど、完全な信頼がない呼び出し元にアクセスできるように、リンク確認要求が無効にします。  
  
 APTCA 属性が完全に信頼されたアセンブリでは、上に存在し、アセンブリが部分的に信頼された呼び出し元は許可されていない別のアセンブリ内のコードの実行、セキュリティ上の弱点が可能性があります。 場合は 2 つのメソッド`M1`と`M2`、次の条件を満たしている、悪意のある呼び出し元がメソッドを使用できる`M1`を保護する暗黙的な完全信頼リンク確認要求をバイパスする`M2`:  
  
-   `M1`APTCA 属性を持つ完全に信頼されたアセンブリでは、パブリック メソッドが宣言されます。  
  
-   `M1`メソッドを呼び出す`M2`外`M1`のアセンブリ。  
  
-   `M2`アセンブリは APTCA 属性がないと、そのため、実行してはならない、または部分的に信頼されている呼び出し元の代わり。  
  
 部分的に信頼された呼び出し元`X`メソッドを呼び出すことができます`M1`、`M1`を呼び出す`M2`です。 `M2` APTCA 属性、その直接の呼び出し元がありません (`M1`) は完全な信頼のリンク要求を満たす必要があります`M1`完全な信頼があり、したがってこのチェックに適合します。 セキュリティ上のリスクがあるため`X`を保護する、リンク確認要求を満たすには参加しません`M2`呼び出し元が信頼されていないからです。 そのため、APTCA 属性を持つメソッド属性を持たないメソッドを呼び出していません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 APCTA 属性が必要な場合は、完全信頼のアセンブリを呼び出すメソッドを保護する要求を使用します。 ユーザーが要求は、メソッドによって公開される機能に依存の正確なアクセス許可。 可能であれば場合、は、基になる機能が部分的に信頼された呼び出し元に公開されないようにする完全な信頼の要求を持つメソッドを保護します。 これが可能でない場合は、公開されている機能を効果的に保護するアクセス許可のセットを選択します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を安全に抑制するには、メソッドによって公開される機能は直接または間接的にできないことに機密情報、操作、または破壊的な方法で使用できるリソースにアクセスする呼び出し元を確認する必要があります。  
  
## <a name="example"></a>例  
 次の例では、2 つのアセンブリと、テスト アプリケーションを使用して、この規則で検出されるセキュリティの脆弱性を示しています。 最初のアセンブリは APTCA 属性がないと部分的に信頼された呼び出し元にアクセスできないように (によって表される`M2`上記の説明で)。  
  
 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]  
  
## <a name="example"></a>例  
 2 番目のアセンブリが完全に信頼されていると、部分的に信頼された呼び出し元を許可 (によって表される`M1`上記の説明で)。  
  
 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]  
  
## <a name="example"></a>例  
 テスト アプリケーション (によって表される`X`上記の説明で) が部分的に信頼されています。  
  
 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **完全な信頼: 要求の要求に失敗しました。**  
**ClassRequiringFullTrust.DoWork が呼び出されました。**   
## <a name="related-rules"></a>関連規則  
 [CA2117: APTCA 型は APTCA 基本型のみを拡張することができます](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)  
  
## <a name="see-also"></a>参照  
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)   
 [部分信頼コードからのライブラリの使用](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)   
 [リンク確認要求](/dotnet/framework/misc/link-demands)   
 [データとモデリング](/dotnet/framework/data/index)