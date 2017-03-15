---
title: "CA1820: 文字列の長さを使用して空の文字列をテストします | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1820: 文字列の長さを使用して空の文字列をテストします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|分類|Microsoft.Performance|  
|互換性に影響する変更点|なし|  
  
## 原因  
 文字列が、<xref:System.Object.Equals%2A?displayProperty=fullName> を使用して空の文字列と比較されています。  
  
## 規則の説明  
 <xref:System.String.Length%2A?displayProperty=fullName> プロパティまたは <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> メソッドを使用して文字列を比較する方法は、<xref:System.Object.Equals%2A> を使用する場合よりもはるかに高速です。  この理由として、<xref:System.Object.Equals%2A> の方が、<xref:System.String.IsNullOrEmpty%2A> または <xref:System.String.Length%2A> プロパティ値を取得するときに実行される命令数よりも多くの MSIL 命令を実行されることと、ゼロと比較されることが挙げられます。  
  
 null 文字列の場合、<xref:System.Object.Equals%2A> と <xref:System.String.Length%2A> \=\= 0 の動作は異なることに注意してください。  null 文字列について <xref:System.String.Length%2A> プロパティの値を取得しようとすると、共通言語ランタイムによって <xref:System.NullReferenceException?displayProperty=fullName> がスローされます。  null 文字列と空の文字列を比較すると、共通言語ランタイムによって例外はスローされません。この比較では `false` が返ります。  null のテストは、これらの 2 つの手法の相対的なパフォーマンスに大きな影響を与えません。  [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] が対象の場合、<xref:System.String.IsNullOrEmpty%2A> メソッドを使用します。  それ以外の場合、できれば <xref:System.String.Length%2A> \=\= の比較を使用します。  
  
## 違反の修正方法  
 この規則違反を修正するには、比較に <xref:System.String.Length%2A> プロパティを使用するように変更し、null 文字列をテストします。  [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] が対象の場合、<xref:System.String.IsNullOrEmpty%2A> メソッドを使用します。  
  
## 警告を抑制する状況  
 パフォーマンスが問題ではない場合、この規則による警告を抑制しても安全です。  
  
## 使用例  
 次の例では、空の文字列を検索するときに使用できる技法を紹介します。  
  
 [!CODE [FxCop.Performance.StringTest#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest#1)]