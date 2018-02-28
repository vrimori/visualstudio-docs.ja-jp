---
title: "CA2141: 透過的メソッドは、Linkdemand を満たしてはならない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 938bda4d4b5c96b9627cf11aae81c51d269c0e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141: 透過的メソッドは、LinkDemand を満たしてはならない
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 透過的セキュリティ メソッドとマークされていないアセンブリのメソッドを呼び出す、 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性、またはセキュリティ透過的なメソッドを満たす、 <xref:System.Security.Permissions.SecurityAction> `.LinkDemand`型またはメソッドです。  
  
## <a name="rule-description"></a>規則の説明  
 LinkDemand を満たす操作では、セキュリティ機密性の高い意図的でない特権の昇格が発生することができます。 セキュリティ透過的なコードは、セキュリティ クリティカルなコードと同じセキュリティ監査要件の対象ではないために、Linkdemand を満たしていません必要があります。 セキュリティ規則セット レベル 1 アセンブリ内の透過的メソッドには、パフォーマンスの問題が発生することができますが、実行時にフル アクセス要求に変換する満たしている Linkdemand はすべてが発生します。 セキュリティ規則セット レベル 2 のアセンブリは、LinkDemand を満たすために試行された場合、just-in-time (JIT) コンパイラでコンパイルする透過的メソッドは失敗します。  
  
 第 2 レベルのセキュリティ、LinkDemand を満たしているか、非 APTCA アセンブリでメソッドを呼び出すには透過的セキュリティ メソッドによる試行の機能を使用するアセンブリでは生成、<xref:System.MethodAccessException>以外の場合はレベル 1 アセンブリ内、LinkDemand フル アクセス要求になります。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するへのアクセスを使用してメソッドをマーク、<xref:System.Security.SecurityCriticalAttribute>または<xref:System.Security.SecuritySafeCriticalAttribute>属性、またはアクセス メソッドから、LinkDemand を削除します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## <a name="example"></a>例  
 この例では、透過的メソッドは、メソッドが LinkDemand を呼び出すしようとします。 このルールは、このコードで起動されます。  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]