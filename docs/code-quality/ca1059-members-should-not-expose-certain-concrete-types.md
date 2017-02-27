---
title: "CA1059: メンバーは特定の具象型を公開できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1059: メンバーは特定の具象型を公開できません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なメンバーは特定の具象型であるか、パラメーターの 1 つまたは戻り値を使用して特定の具象型を公開します。  現在、この規則によって次の具象型の脆弱性が報告されています。  
  
-   <xref:System.Xml.XmlNode?displayProperty=fullName> の派生型。  
  
## 規則の説明  
 具象型は、完全な実装を含む型であるため、インスタンス化できます。  このメンバーを広範囲に使用するには、具象型を推奨インターフェイスと置き換えます。  これにより、メンバーはそのインターフェイスを実装する任意の型を受け入れられるようになったり、そのインターフェイスを実装する型が求められる場所で使用できるようになったりします。  
  
 次の表に、対象となる具象型およびそれと置き換えることが推奨されるインターフェイスを示します。  
  
|具象型|置き換え|  
|---------|----------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> このインターフェイスを使用することで、XML データ ソースの特定の実装からメンバーを切り離します。|  
  
## 違反の修正方法  
 この規則違反を修正するには、具象型を推奨インターフェイスに変更します。  
  
## 警告を抑制する状況  
 具象型によって実現されている特定の機能が必要な場合は、この規則によるメッセージを抑制しても安全です。  
  
## 関連規則  
 [CA1011: 基本型をパラメーターとして渡すことを考慮します](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)