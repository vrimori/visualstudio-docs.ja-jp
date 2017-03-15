---
title: "演算子をモジュール内で宣言できません | Microsoft Docs"
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
  - "bc33018"
  - "vbc33018"
helpviewer_keywords: 
  - "BC33018"
ms.assetid: 10a8fd2d-2af7-4f90-9f2a-50c07ebf7589
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子をモジュール内で宣言できません
モジュールの定義に [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement) が記述されています。  
  
 定義しているクラスまたは構造体の一部として、演算子を定義できます。 演算子には、そのクラスまたは構造体を少なくとも 1 つのオペランドとして指定する必要があります。  
  
 演算子ではオペランドの 1 つとしてプログラミング要素のインスタンスを使用する必要があり、クラスと構造体のみがインスタンスを持ちます。 そのため、その他のプログラミング要素の一部として、演算子を定義することはできません。  
  
 **エラー ID:** BC33018  
  
### このエラーを解決するには  
  
-   モジュールの操作を必要とする場合は、[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) を使用して、その操作を実行する `Function` プロシージャを定義します。  
  
-   また、モジュール内にクラスまたは構造体を定義し、そのクラスまたは構造体に対する演算子を定義することもできます。 ただし、その演算子には、そのクラスまたは構造体のインスタンスを少なくとも 1 つのオペランドとして指定する必要があります。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)