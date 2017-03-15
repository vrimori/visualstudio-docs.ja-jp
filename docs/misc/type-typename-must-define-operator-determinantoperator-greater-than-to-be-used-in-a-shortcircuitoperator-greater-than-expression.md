---
title: "型 &#39;&lt;typename&gt;&#39; を &#39;&lt;shortcircuitoperator&gt;&#39; 式で使用するには、演算子 &#39;&lt;determinantoperator&gt;&#39; を定義する必要があります | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33035"
  - "vbc33035"
helpviewer_keywords: 
  - "BC33035"
ms.assetid: 50a0a39f-63cd-4100-aea9-91b5b6ab5bbf
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; を &#39;&lt;shortcircuitoperator&gt;&#39; 式で使用するには、演算子 &#39;&lt;determinantoperator&gt;&#39; を定義する必要があります
[AndAlso Operator](/dotnet/visual-basic/language-reference/operators/andalso-operator) または [OrElse Operator](/dotnet/visual-basic/language-reference/operators/orelse-operator) がクラスまたは構造体型のオペランドを使用していますが、そのクラスまたは構造体に必要な演算子が定義されていません。  
  
 ショート サーキット演算子 \(`AndAlso` または `OrElse`\) を直接定義していないので、対応する論理演算子および決定演算子を定義する必要があります。 次の表に、必要な演算子を示します。  
  
|ショートサーキット演算子|論理演算子|決定演算子|  
|------------------|-----------|-----------|  
|`AndAlso`|[And Operator](/dotnet/visual-basic/language-reference/operators/and-operator)|[IsFalse Operator](/dotnet/visual-basic/language-reference/operators/isfalse-operator)|  
|`OrElse`|[Or Operator](/dotnet/visual-basic/language-reference/operators/or-operator)|[IsTrue Operator](/dotnet/visual-basic/language-reference/operators/istrue-operator)|  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] はこれらの論理および決定演算子を使用して、`AndAlso` または `OrElse` のショート サーキットのロジックを構築します。 これを正しく行うために、両方のオペランドと `And` または `Or` の定義の戻り値は包含型でなければなりません。つまり、`And` または `Or` を定義しているクラスまたは構造体の型でなければなりません。  
  
 **エラー ID:** BC33035  
  
### このエラーを解決するには  
  
-   `AndAlso` 演算子または `OrElse` 演算子のオペランドの型に使用するクラスまたは構造体の内部に、`And` 演算子と `IsFalse` 演算子を定義するか、または `Or` 演算子と `IsTrue` 演算子を定義します。`And` または `Or` のオペランドは、必ずそれを定義しているクラスまたは構造体の型にします。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Logical and Bitwise Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators)