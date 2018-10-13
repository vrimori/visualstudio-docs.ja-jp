---
title: '2135: レベル 2 のアセンブリは Linkdemand を含んでならない |Microsoft Docs'
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
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4e4b4cd759557defc7761db34841e3d87a285558
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294802"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: レベル 2 のアセンブリは LinkDemand を含んではならない
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、<xref:System.Security.Permissions.SecurityAction>を削除して、メソッドに設定されて、<xref:System.Security.SecurityCriticalAttribute>属性。

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]



