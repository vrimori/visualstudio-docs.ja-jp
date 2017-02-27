---
title: "CA2242: NaN に対して正しくテストします | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242: NaN に対して正しくテストします
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|分類|Microsoft.Usage|  
|互換性に影響する変更点|なし|  
  
## 原因  
 式が <xref:System.Single.Nan?displayProperty=fullName> または <xref:System.Double.Nan?displayProperty=fullName> に対して値をテストしています。  
  
## 規則の説明  
 算術演算が定義されていない場合、結果として非数値を表す <xref:System.Double.NaN?displayProperty=fullName> が返されます。  ある値と <xref:System.Double.NaN?displayProperty=fullName> が等値であることをテストする式は、常に `false` を返します。  ある値と <xref:System.Double.NaN?displayProperty=fullName> が非等値であることをテストする式は、常に `true` を返します。  
  
## 違反の修正方法  
 この規則違反を修正し、値が <xref:System.Double.NaN?displayProperty=fullName> を表すかどうかを正確に判定するには、<xref:System.Single.IsNan%2A?displayProperty=fullName> または <xref:System.Double.IsNan%2A?displayProperty=fullName> を使用して値をテストします。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 次の例は、値を <xref:System.Double.NaN?displayProperty=fullName> に対して正しくテストしない 2 つの式と <xref:System.Double.IsNaN%2A?displayProperty=fullName> を正しく使用して値をテストする式を示しています。  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]