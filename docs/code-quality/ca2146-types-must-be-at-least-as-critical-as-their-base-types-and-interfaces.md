---
title: "CA2146: 型は、基本型およびインターフェイスと同程度以上、重要でなければならない | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2146: 型は、基本型およびインターフェイスと同程度以上、重要でなければならない
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|分類|Microsoft.Security|  
|互換性に影響する変更点|あり|  
  
## 原因  
 透過データ型は、<xref:System.Security.SecuritySafeCriticalAttribute> または <xref:System.Security.SecurityCriticalAttribute> が適用されたデータ型から派生します。<xref:System.Security.SecuritySafeCriticalAttribute> 属性が適用されたデータ型は、<xref:System.Security.SecurityCriticalAttribute> 属性が適用されたデータ型から派生します。  
  
## 規則の説明  
 派生型に透過的セキュリティ属性が設定されていて、この属性が基本型または実装されたインターフェイスほど重要ではない場合に、この規則が適用されます。  クリティカルな基本型から派生したり、クリティカルなインターフェイスを実装したりできるのは、クリティカルなデータ型だけです。また、セーフ クリティカルな基本型から派生したり、セーフ クリティカルなインターフェイスを実装したりできるのは、クリティカルまたはセーフ クリティカルなデータ型だけです。  レベル 2 の透過性でこの規則に違反すると、派生型に対して例外 <xref:System.TypeLoadException> が発生します。  
  
## 違反の修正方法  
 この違反を修正するには、派生型または実装するデータ型に透過属性を適用します。この透過属性は、基本型またはインターフェイスと同程度以上に重要です。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]