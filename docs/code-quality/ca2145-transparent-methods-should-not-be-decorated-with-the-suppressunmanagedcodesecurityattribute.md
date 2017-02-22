---
title: "CA2145: 透過的メソッドを SuppressUnmanagedCodeSecurityAttribute で修飾してはならない | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: 透過的メソッドを SuppressUnmanagedCodeSecurityAttribute で修飾してはならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過的メソッド、<xref:System.Security.SecuritySafeCriticalAttribute> 属性が設定されたメソッド、またはメソッドを含む型に <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性が設定されています。  
  
## 規則の説明  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 属性で修飾されたメソッドには、それを呼び出すメソッドに対して適用される暗黙的な LinkDemand があります。  この LinkDemand では、呼び出し元のコードがセキュリティ クリティカルなコードである必要があります。  SuppressUnmanagedCodeSecurity を使用するメソッドに <xref:System.Security.SecurityCriticalAttribute> 属性を設定すると、メソッドの呼び出し元に対してこの要件がより明確になります。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドまたは型に対して <xref:System.Security.SecurityCriticalAttribute> 属性を設定します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
### コード  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### コメント