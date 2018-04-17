---
title: 'CA2135: レベル 2 のアセンブリは Linkdemand を含んでいない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0be276db088e30a71e40905423c5c88a5b714d43
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: レベル 2 のアセンブリは LinkDemand を含んではならない
|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 クラスまたはクラス メンバーを使用して、<xref:System.Security.Permissions.SecurityAction>第 2 レベルのセキュリティを使用しているアプリケーションでします。  
  
## <a name="rule-description"></a>規則の説明  
 LinkDemands は、レベル 2 のセキュリティ規則セットでは使用が推奨されていません。 ・ イン タイム (JIT) コンパイル時にセキュリティを適用するために LinkDemands を使用する代わりに、メソッド、型、およびフィールドをマーク、<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を解決するには、削除、<xref:System.Security.Permissions.SecurityAction>型またはメンバーをマークし、<xref:System.Security.SecurityCriticalAttribute>属性。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 次の例で、<xref:System.Security.Permissions.SecurityAction>を削除して、メソッドでマークされて、<xref:System.Security.SecurityCriticalAttribute>属性。  
  
 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]