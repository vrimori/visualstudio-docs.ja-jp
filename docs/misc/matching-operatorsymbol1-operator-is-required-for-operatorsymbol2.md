---
title: "&#39;&lt;operatorsymbol2&gt;&#39; に 合致する演算子 &#39;&lt;operatorsymbol1&gt;&#39; が必要です。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;operatorsymbol2&gt;&#39; に 合致する演算子 &#39;&lt;operatorsymbol1&gt;&#39; が必要です。
この演算子は、必要な合致する演算子が定義されていない場合に定義されます。  
  
 次の演算子は、一致するペアとして定義する必要があります。  
  
-   `=` および `<>`  
  
-   `>` および `<`  
  
-   `>=` および `<=`  
  
-   `IsTrue` および `IsFalse`  
  
 クラスまたは構造体でこれらの演算子のいずれかを定義する場合は、同じクラスまたは構造体で、合致する演算子も定義する必要があります。  
  
 合致する演算子を明示的に使用しない場合でも、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] でそれを使用する必要がある場合があります。 たとえば、[For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement) でカウンター変数として使用するクラスまたは構造体を定義する場合、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] には、`>=` および `<=` 演算子の両方 \(および `+` 演算子\) が必要です。  
  
 **エラー ID:** BC33033  
  
### このエラーを解決するには  
  
-   同じクラスまたは構造体で、合致する演算子を定義します。 この演算子は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] で予期しない状況で使用される可能性があるため、できるだけ明確に定義します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operators and Expressions](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)