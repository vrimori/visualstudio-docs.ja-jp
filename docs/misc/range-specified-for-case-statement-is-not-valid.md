---
title: "&#39;Case&#39; ステートメントに指定された範囲が無効です | Microsoft Docs"
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
  - "vbc40052"
  - "bc40052"
helpviewer_keywords: 
  - "BC40052"
ms.assetid: a11d92f6-dc13-46a0-a8ca-5a962a0ed968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; ステートメントに指定された範囲が無効です
`Case` ステートメントに無効な範囲が指定されています。  
  
 同じ式を複数の異なる値と比較する場合、`If...Then...Else` ステートメントの代わりに `Select...Case` ステートメントを使用できます。`If` および `ElseIf` ステートメントは各ステートメントで異なる式を評価できますが、`Select` ステートメントでは、1 つの式を 1 回のみ評価し、それをすべての比較に使用します。 各 `Case` ステートメントには、複数の値、値の範囲、または値と比較演算子の組み合わせを含めることができます。  
  
 **エラー ID:** BC40052  
  
### このエラーを解決するには  
  
-   すべての値が含まれるように範囲を変更するか、`Case Else` ステートメントを使用して未定義の値をキャッチします。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Decision Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)