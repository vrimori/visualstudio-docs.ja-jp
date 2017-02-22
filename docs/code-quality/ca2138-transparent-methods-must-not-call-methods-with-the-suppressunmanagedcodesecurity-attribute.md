---
title: "CA2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: 透過的メソッドは、SuppressUnmanagedCodeSecurity 属性を持つメソッドを呼び出してはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性が適用されたメソッドを、透過的セキュリティ メソッドが呼び出します。  
  
## 規則の説明  
 この規則は、P\/Invoke \(プラットフォーム呼び出し\) 呼び出しを使用するなどの方法で、ネイティブ コードを直接呼び出す透過的メソッドに対して適用されます。  <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性が設定された P\/Invoke メソッドと COM 相互運用メソッドでは、呼び出し元のメソッドに対して LinkDemand が実行されます。  透過的セキュリティ コードは LinkDemands を満たすことができないため、SuppressUnmanagedCodeSecurity 属性が設定されたメソッドを呼び出すことも、SuppressUnmanagedCodeSecurity 属性が設定されたクラスのメソッドを呼び出すこともできません。  メソッドは失敗するか、要求がフル アクセス要求に変換されます。  
  
 この規則に違反すると、レベル 1 の透過的セキュリティ モデルでは <xref:System.MethodAccessException> が発生し、レベル 1 の透過性モデルでは <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> に対するフル アクセス要求が発生します。  
  
## 違反の修正方法  
 この規則違反を修正するには、<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性を削除し、<xref:System.Security.SecurityCriticalAttribute> 属性または <xref:System.Security.SecuritySafeCriticalAttribute> 属性をメソッドに適用する必要があります。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]