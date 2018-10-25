---
title: 'CA2135: レベル 2 のアセンブリは LinkDemand を含んではならない'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08f8719a7b9434a774d00003a1b135e18c06eacb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49898188"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: レベル 2 のアセンブリは LinkDemand を含んではならない

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 クラスまたはクラス メンバーを使用して、<xref:System.Security.Permissions.SecurityAction>レベル 2 のセキュリティを使用しているアプリケーションでします。

## <a name="rule-description"></a>規則の説明
 LinkDemands は、レベル 2 のセキュリティ規則セットでは使用が非推奨とされます。 メソッド、型、およびフィールドをマーク ・ イン タイム (JIT) コンパイル時にセキュリティを適用するために LinkDemands を使用する代わりに、<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、削除、<xref:System.Security.Permissions.SecurityAction>型またはメンバーをマークし、<xref:System.Security.SecurityCriticalAttribute>属性。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、<xref:System.Security.Permissions.SecurityAction>を削除して、メソッドに設定されて、<xref:System.Security.SecurityCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]