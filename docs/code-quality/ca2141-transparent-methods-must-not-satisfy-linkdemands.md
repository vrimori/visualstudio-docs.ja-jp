---
title: "CA2141: 透過的メソッドは、LinkDemand を満たしてはならない | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2141: 透過的メソッドは、LinkDemand を満たしてはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過的セキュリティ メソッドは、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) 属性が適用されていないアセンブリ内のメソッドを呼び出します。また、透過的セキュリティ メソッドは、データ型またはメソッドに対する <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` の要件を満たします。  
  
## 規則の説明  
 LinkDemand を満たすという操作は、予期しない特権の昇格を引き起こす場合があるため、セキュリティに対する配慮が必要な操作です。  透過的セキュリティ コードには、セキュリティ クリティカルなコードと同じセキュリティ監査要件が適用されないため、透過的セキュリティ コードが LinkDemands の要件を満たすことはできません。  セキュリティ規則のセット \(レベル 1 アセンブリ\) 内の透過的メソッドにより、要件を満たされた LinkDemands が実行時にフル アクセス要求へ変換されます。このため、パフォーマンスに関する問題が発生することがあります。  セキュリティ規則のセット \(レベル 2 アセンブリ\) において透過的メソッドが LinkDemand の要件を満たそうとした場合、透過的メソッドによる Just\-In\-Time \(JIT\) コンパイラでのコンパイルが失敗します。  
  
 レベル 2 のセキュリティを使用するアセンブリにおいて、透過的セキュリティ メソッドが LinkDemand の要件を満たそうとした場合や非 APTCA アセンブリを呼び出そうとした場合は、<xref:System.MethodAccessException> が発生します。レベル 1 アセンブリの場合は、LinkDemand がフル アクセス要求になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、アクセス元のメソッドに <xref:System.Security.SecurityCriticalAttribute> 属性または <xref:System.Security.SecuritySafeCriticalAttribute> 属性を適用するか、アクセス先のメソッドから LinkDemand を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 この例では、LinkDemand が定義されたメソッドを透過的メソッドから呼び出そうとしています。  こうしたコードを記述すると、この規則が適用されます。  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]