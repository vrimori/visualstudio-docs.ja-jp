---
title: "変換演算子によって、ある型から同じ型に変換することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33024"
  - "vbc33024"
helpviewer_keywords: 
  - "BC33024"
ms.assetid: 4b47bcb0-4f0c-4d1c-9274-cce5b8e2b370
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子によって、ある型から同じ型に変換することはできません
変換演算子がパラメーターと戻り値の両方で同じ型で宣言されています。  
  
 型を同じ型に変換しても意味がありません。  
  
 **エラー ID:** BC33024  
  
### このエラーを解決するには  
  
-   パラメーターまたは戻り値のいずれかの型を変更します。 いずれか一方を、この演算子が定義されているクラスまたは構造体の型にする必要があります。 他方を別の型にする必要があります。  
  
-   パラメーターの内容に対して変換を実行する必要がある場合は、[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) を使用して、演算子ではなく `Function` プロシージャを定義します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)