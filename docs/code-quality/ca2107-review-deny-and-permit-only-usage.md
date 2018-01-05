---
title: "2107: ca レビュー deny し、permitonly の用法 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3d6f514546c298a134785740fe7bbf948031bc74
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Deny と PermitOnly の用法を再確認します
|||  
|-|-|  
|TypeName|ReviewDenyAndPermitOnlyUsage|  
|CheckId|CA2107|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 メソッドには、PermitOnly] または [拒否するセキュリティ アクションを示すセキュリティ チェックが含まれています。  
  
## <a name="rule-description"></a>規則の説明  
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>セキュリティ アクションは、高度な知識を持つユーザーだけが使用する必要がありますの[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]セキュリティ。 コードにこのセキュリティ アクションを使用する場合、セキュリティを再確認する必要があります。  
  
 拒否するセキュリティの要求に応答が発生するスタック ウォークの既定の動作を変更します。 コール スタックに呼び出し元の実際のアクセス許可に関係なく、拒否のメソッドの中に付与する必要がない権限を指定できます。 場合は、スタック ウォークが Deny で保護されているメソッドを検出し、要求されたアクセス許可が拒否されたアクセス許可に含まれている場合、スタック ウォークが失敗します。 PermitOnly は、スタック ウォークの既定の動作も変更されます。 これにより、コードの呼び出し元のアクセス許可に関係なく、許可できる権限のみを指定できます。 場合は、スタック ウォークが PermitOnly で保護されているメソッドを検出し、PermitOnly で指定されているアクセス許可で要求されたアクセス許可が含まれていない場合に、スタック ウォークが失敗します。  
  
 これらの操作に依存するコードは、その制限の利便性と動作が多少のためのセキュリティの脆弱性を慎重に評価されます必要があります。 次に例を示します。  
  
-   [リンク確認要求](/dotnet/framework/misc/link-demands)Deny または PermitOnly では、影響を受けません。  
  
-   Deny または PermitOnly は、スタック ウォークを実行する要求と同じスタック フレームで発生する場合、セキュリティのアクションがある影響しません。  
  
-   通常、パス ベースのアクセス許可を構築するために使用される値を指定するのにはさまざまな方法です。 パスの 1 つのフォームへのアクセスを拒否することも、すべてのフォームへのアクセスは拒否されません。 たとえば、ファイル共有\\\Server\Share がネットワーク ドライブ、共有のファイルへのアクセスを拒否する、x: マップされている必要がありますを拒否する\\\Server\Share\File、X:\File および、ファイルにアクセスするその他のすべてのパス。  
  
-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Deny または PermitOnly に達する前に、スタック ウォークを終了できます。  
  
-   Deny による影響がある場合つまり、呼び出し元が、拒否によってブロックされているアクセス許可を持つ呼び出し元は、リソースにアクセスできます保護されたを直接拒否する をバイパスします。 同様に、呼び出し元が拒否されたアクセス許可を持たない場合、スタック ウォークは Deny がなくても失敗します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 このセキュリティ アクションを使用するには、違反が引き起こすされます。 違反を修正するのには、このセキュリティ アクションを使用しないでください。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 セキュリティ レビューを完了した後にのみ、この規則による警告を抑制します。  
  
## <a name="example"></a>例  
 次の例では、拒否の制限事項を示します。  
  
 次のライブラリには、保護するためのセキュリティ要求を除いて同一である 2 つのメソッドを持つクラスが含まれています。  
  
 [!code-csharp[FxCop.Security.PermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_1.cs)]  
  
## <a name="example"></a>例  
 次のアプリケーションでは、ライブラリからセキュリティで保護されたメソッドに対する拒否の効果を示しています。  
  
 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../code-quality/codesnippet/CSharp/ca2107-review-deny-and-permit-only-usage_2.cs)]  
  
 この例を実行すると、次の出力が生成されます。  
  
 **要求時:: 呼び出し元の拒否はアサートされたアクセス許可を持つ要求時に影響しません。**  
**LinkDemand: 呼び出し元の拒否するには影響しません LinkDemand アサートされたアクセス許可を持つ。**  
**LinkDemand: 呼び出し元の拒否には、LinkDemand で保護されたコードに影響はありません。**  
**LinkDemand: この拒否には、LinkDemand で保護されたコードに影響はありません。**   
## <a name="see-also"></a>参照  
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>   
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>   
 [安全なコーディングのガイドライン](/dotnet/standard/security/secure-coding-guidelines)   

