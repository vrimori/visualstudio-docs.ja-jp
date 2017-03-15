---
title: "演算子は &#39;Public&#39; として宣言されなければなりません。 | Microsoft Docs"
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
  - "vbc33011"
  - "bc33011"
helpviewer_keywords: 
  - "BC33011"
ms.assetid: 67fc0dee-4ef5-4afc-a63a-f7d20bce7954
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子は &#39;Public&#39; として宣言されなければなりません。
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) には [Public](/dotnet/visual-basic/language-reference/modifiers/public) キーワードが含まれていません。  
  
 `Operator` プロシージャには、`Public` と [Shared](/dotnet/visual-basic/language-reference/modifiers/shared) の両方のキーワードが必要であり、変換演算子にも [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) または [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) のいずれかのキーワードが必要です。  
  
 **エラー ID:** BC33011  
  
### このエラーを解決するには  
  
-   `Public` キーワードを `Operator` ステートメントに追加します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)