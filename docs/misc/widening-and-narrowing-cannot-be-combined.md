---
title: "&#39;Widening&#39; と &#39;Narrowing&#39; を組み合わせて使用することはできません | Microsoft Docs"
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
  - "bc33001"
  - "vbc33001"
helpviewer_keywords: 
  - "BC33001"
ms.assetid: 1c576344-083c-45ad-bc71-0489bd3976be
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Widening&#39; と &#39;Narrowing&#39; を組み合わせて使用することはできません
[Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) は [Widening](/dotnet/visual-basic/language-reference/modifiers/widening) と [Narrowing](/dotnet/visual-basic/language-reference/modifiers/narrowing) の両方を指定しています。  
  
 変換演算子を定義するときは、`Widening` または `Narrowing` のいずれかとして宣言する必要があります。 これらは相互に排他的な特性であるため、両方を指定することはできません。  
  
 **エラー ID:** BC33001  
  
### このエラーを解決するには  
  
-   `Operator` ステートメントから `Widening` または `Narrowing` のどちらかのキーワードを削除します。 どちらか一方を指定する必要があります。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)