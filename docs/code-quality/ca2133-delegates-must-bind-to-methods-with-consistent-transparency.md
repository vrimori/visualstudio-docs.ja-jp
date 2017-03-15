---
title: "CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2133: デリゲートは透過性の整合がとれたメソッドにバインドする必要がある
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
> [!NOTE]
>  この警告は、CoreCLR \(Silverlight Web アプリケーションに固有の CLR バージョン\) を実行しているコードにのみ適用されます。  
  
## 原因  
 この警告は、<xref:System.Security.SecurityCriticalAttribute> が設定されているデリゲートを、透過的なメソッドまたは <xref:System.Security.SecuritySafeCriticalAttribute> が設定されているメソッドにバインドするメソッドに対して適用されます。  この警告は、透過的なデリゲートまたはセーフ クリティカルなデリゲートを、クリティカル メソッドにバインドするメソッドに対しても適用されます。  
  
## 規則の説明  
 デリゲート型、およびそのバインド先のメソッドの透過性は、一貫している必要があります。  透過的デリゲートおよびセーフ クリティカルなデリゲートは、その他の透過的メソッドまたはセーフ クリティカルなメソッドにのみバインドできます。  同様に、クリティカル デリゲートは、クリティカル メソッドにのみバインドできます。  これらのバインディング規則により、あるメソッドをデリゲート経由で呼び出すことができる唯一のコードは、同じメソッドを直接呼び出すことができるコードであるということが保証されます。  たとえば、バインディング規則により、透過的なコードが透過的デリゲートを経由してクリティカル コードを直接呼び出すことを防止できます。  
  
## 違反の修正方法  
 この警告の違反を修正するには、デリゲートまたはそのバインド先のメソッドの透過性を変更して、両者の透過性を等しくする必要があります。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
### コード  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]