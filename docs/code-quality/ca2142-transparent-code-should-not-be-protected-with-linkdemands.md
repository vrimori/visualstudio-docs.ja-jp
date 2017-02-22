---
title: "CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない | Microsoft Docs"
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
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2142: 透過的コードは、LinkDemand を使用して保護されてはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過的メソッドが、<xref:System.Security.Permissions.SecurityAction> またはその他のセキュリティ確認要求を必要としています。  
  
## 規則の説明  
 この規則は、アクセスするために LinkDemands を要求する透過的メソッドに対して適用されます。  透過的セキュリティ コードでは、操作のセキュリティ検証を行うことができないため、アクセス許可を要求できません。  透過的メソッドは、セキュリティに中立的であると見なされるため、セキュリティ上の決定を行うことができません。  また、セキュリティ上の決定を行うセーフ クリティカルなコードでは、透過的なコードを使用して事前にそのような決定を行うことはできません。  
  
## 違反の修正方法  
 この規則への違反を修正するには、透過的メソッドのリンク確認要求を削除するか、メソッドがセキュリティ確認要求などのセキュリティ チェックを実行する場合はメソッドに対して <xref:System.Security.SecuritySafeCriticalAttribute> 属性を設定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例では、メソッドが透過的であり、かつメソッドに対して <xref:System.Security.Permissions.SecurityAction> を含む LinkDemand <xref:System.Security.PermissionSet> が設定されているため、メソッドにこの規則が適用されます。  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 この規則による警告は抑制しないでください。