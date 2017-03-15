---
title: "変換演算子は、&#39;Widening&#39; または &#39;Narrowing&#39; のいずれかとして宣言されなければなりません | Microsoft Docs"
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
  - "vbc33017"
  - "bc33017"
helpviewer_keywords: 
  - "BC33017"
ms.assetid: 5972d955-ce1d-4348-a021-167eecb3a507
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子は、&#39;Widening&#39; または &#39;Narrowing&#39; のいずれかとして宣言されなければなりません
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) に、[Widening](/dotnet/visual-basic/language-reference/modifiers/widening) も [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) も指定されていません。  
  
 変換演算子を定義するときは、`Widening` または `Narrowing` のいずれかとして宣言する必要があります。 これらは相互に排他的な特性であるため、両方を指定することはできません。  
  
 **エラー ID:** BC33017  
  
### このエラーを解決するには  
  
-   変換演算子を `Widening` と `Narrowing` のどちらにするかを決定し、`Operator` ステートメントに正しいキーワードを含めます。 どちらか一方を指定する必要があります。  
  
## 参照  
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)