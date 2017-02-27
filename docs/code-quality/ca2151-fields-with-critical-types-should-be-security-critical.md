---
title: "CA2151: クリティカル型のフィールドはセキュリティ クリティカルである必要があります | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09db9d25-7d58-4725-a252-4a07baadf046
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA2151: クリティカル型のフィールドはセキュリティ クリティカルである必要があります
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName||  
|CheckId|CA2151|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過的セキュリティ フィールドまたはセーフ クリティカル フィールドが宣言されました。  その型は、セキュリティ クリティカルとして指定されています。  たとえば、次のようにします。  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      Type1 m_field; // CA2151, transparent field of critical type  
   }  
  
```  
  
 この例では、`m_field` はセキュリティ クリティカルな型の透過的セキュリティ フィールドです。  
  
## 規則の説明  
 セキュリティ クリティカルな型を使用するには、型を参照するコードがセキュリティ クリティカルであるか、セキュリティ セーフ クリティカルである必要があります。  これは、参照が間接的である場合にも当てはまります。  たとえば、クリティカルな型を持つ透過的フィールドを参照する場合、コードはセキュリティ クリティカルであるか、セキュリティ セーフである必要があります。  そのため、透過的セキュリティまたはセキュリティ セーフ クリティカルなフィールドが存在すると、透過的なコードはこのフィールドにアクセスできないので、紛らわしくなります。  
  
## 違反の修正方法  
 この規則違反を修正するには、フィールドを <xref:System.Security.SecurityCriticalAttribute> 属性でマークするか、フィールドによって参照される型を透過的セキュリティまたはセーフ クリティカルにします。  
  
```c#  
// Fix 1: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   [SecurityCritical]  
   class Type1 { } // Security Critical type  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
// Fix 2: Make the referencing field security critical  
[assembly: AllowPartiallyTrustedCallers]  
  
   class Type1 { } // Type1 is now transparent  
  
   class Type2 // Security transparent type  
   {  
      [SecurityCritical]  
      Type1 m_field; // Fixed: critical type, critical field  
   }  
  
```  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
### コード  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2151-fields-with-critical-types-should-be-security-critical_1.cs)]  
  
### コメント