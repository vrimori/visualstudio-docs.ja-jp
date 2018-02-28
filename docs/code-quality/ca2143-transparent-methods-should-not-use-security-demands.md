---
title: "Ca 2143: 透過的メソッドはセキュリティ確認要求を使用しない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 073ce1d22662b46a19bf5cf36305df63500347a7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: 透過的メソッドは、セキュリティ確認要求を使用してはならない
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 Tranparent 型またはメソッドが宣言とマークされている、 <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand`要求時またはメソッドの呼び出し、<xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>メソッドです。  
  
## <a name="rule-description"></a>規則の説明  
 透過的セキュリティ コードでは、操作のセキュリティ検証を行うことができないため、アクセス許可を要求できません。 透過的セキュリティ コードは、フル アクセス要求を使用して、セキュリティ上の決定を行う必要があります。セーフ クリティカルなコードでは、透過的なコードを使用してフル アクセス要求を行うことはできません。 セキュリティ確認要求などのセキュリティ チェックを実行するすべてのコードは、代わりに上安全-重要にする必要があります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 一般に、この規則違反を修正するを使用してメソッドをマーク、<xref:System.Security.SecuritySafeCriticalAttribute>属性。 要求を削除することもできます。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 ルールは、透過的メソッドは、宣言セキュリティ確認要求のために、次のコードのファイルです。  
  
 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## <a name="see-also"></a>参照  
 [CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)