---
title: '2107: ca レビュー deny し、permitonly の用法 |Microsoft Docs'
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
- CA2107
- ReviewDenyAndPermitOnlyUsage
helpviewer_keywords:
- ReviewDenyAndPermitOnlyUsage
- CA2107
ms.assetid: 366f4a56-ae93-4882-81d0-bd0a55ebbc26
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b317ddb69dea8241ead6bb70d50c3b99d96bd078
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178647"
---
# <a name="ca2107-review-deny-and-permit-only-usage"></a>CA2107: Deny と PermitOnly の用法を再確認します
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ReviewDenyAndPermitOnlyUsage|
|CheckId|CA2107|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 メソッドには、PermitOnly または Deny セキュリティ アクションを指定するセキュリティ チェックが含まれています。

## <a name="rule-description"></a>規則の説明
 [PermitOnly メソッドを使用して](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)と<xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>セキュリティ アクションは、高度な知識を持つユーザーだけが使用する必要がありますの[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]セキュリティ。 コードにこのセキュリティ アクションを使用する場合、セキュリティを再確認する必要があります。

 拒否するセキュリティの要求に対する応答で発生するスタック ウォークの既定の動作を変更します。 コール スタックに呼び出し元の実際のアクセス許可に関係なく、拒否、メソッドの実行中に許可する必要がありますアクセス許可を指定できます。 場合は、スタック ウォークが Deny で保護されているメソッドを検出し、要求されたアクセス許可が拒否されたアクセス許可に含まれる場合、スタック ウォークが失敗します。 PermitOnly には、スタック ウォークの既定の動作も変更します。 これにより、コード、呼び出し元のアクセス許可に関係なく、付与できるアクセス許可のみを指定できます。 場合は、スタック ウォーク PermitOnly で保護されているメソッドを検出して、PermitOnly で指定されているアクセス許可では、要求されたアクセス許可が含まれていない、スタック ウォークが失敗します。

 これらのアクションに依存するコードは、セキュリティの脆弱性で慎重に、制限付きの有用性と動作が多少により評価する必要があります。 次に例を示します。

-   [リンク確認要求](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)Deny または PermitOnly の影響を受けない。

-   Deny または PermitOnly は、スタック ウォークを実行する要求と同じスタック フレームで発生する場合、セキュリティ アクションがある影響しません。

-   パス ベースのアクセス許可の作成に使用される値は、複数の方法で、通常は指定できます。 パスの 1 つのフォームへのアクセスを拒否することは、すべてのフォームへのアクセスは拒否されません。 たとえば、ファイル共有\\\Server\Share はネットワーク ドライブ、共有上のファイルへのアクセスを拒否する、x: にマップする必要がありますを拒否する\\\Server\Share\File、X:\File およびファイルにアクセスするその他のすべてのパス。

-   <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> Deny または PermitOnly に達する前に、スタック ウォークを終了できます。

-   拒否に影響がある場合具体的には、呼び出し元が、拒否によってブロックされているアクセス許可を持つ呼び出し元リソースにアクセスできる保護されたを直接拒否する をバイパスします。 同様に、呼び出し元が拒否されたアクセス許可を持たない場合、拒否せず、スタック ウォークは失敗します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 これらのセキュリティ アクションの使用はすべて、違反となります。 違反を修正するには、これらのセキュリティ アクションを使用しないでください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 セキュリティ レビューの完了後にのみ、この規則による警告を抑制します。

## <a name="example"></a>例
 次の例では、拒否の制限事項を示します。

 次のライブラリには、保護するセキュリティ要求以外はまったく同じ 2 つのメソッドを持つクラスが含まれています。

 [!code-csharp[FxCop.Security.PermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PermitAndDeny/cs/FxCop.Security.PermitAndDeny.cs#1)]

## <a name="example"></a>例
 次のアプリケーションでは、ライブラリからセキュリティで保護されたメソッドに対する拒否の効果を示しています。

 [!code-csharp[FxCop.Security.TestPermitAndDeny#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestPermitAndDeny/cs/FxCop.Security.TestPermitAndDeny.cs#1)]

 この例を実行すると、次の出力が生成されます。

 **オンデマンド: 呼び出し元の拒否にアサートされたアクセス許可を要求時に効果がありません。** 
 **LinkDemand: 呼び出し元の Deny がアサートされたアクセス許可を持つ LinkDemand 上の影響を与えません**。
 **LinkDemand: 呼び出し元の拒否は LinkDemand で保護されているコードに影響を与えません**。
 **LinkDemand: LinkDemand で保護されたコードで有効になるこの拒否がありません。**
## <a name="see-also"></a>関連項目
 <xref:System.Security.CodeAccessPermission.PermitOnly%2A?displayProperty=fullName> <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
 <xref:System.Security.CodeAccessPermission.Deny%2A?displayProperty=fullName>
 <xref:System.Security.IStackWalk.PermitOnly%2A?displayProperty=fullName>
 [安全なコーディングのガイドライン](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)[セキュリティ チェックをオーバーライドする](http://msdn.microsoft.com/en-us/4acdeff5-fc05-41bf-8505-7387cdbfca28) [PermitOnly メソッドの使用](http://msdn.microsoft.com/en-us/8c7bdb7f-882f-45b7-908c-6cbaa1767649)



