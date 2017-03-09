---
title: "この単項演算子のパラメーターの型は、含む型 &#39;&lt;typename&gt;&#39; である必要があります | Microsoft Docs"
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
  - "vbc33020"
  - "bc33020"
helpviewer_keywords: 
  - "BC33020"
ms.assetid: 9c2c2c5b-6f18-49d2-bd6e-e735a6bced77
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この単項演算子のパラメーターの型は、含む型 &#39;&lt;typename&gt;&#39; である必要があります
単項演算子の定義では、演算子が定義されているクラスまたは構造体以外の型を使用してパラメーターを指定します。  
  
 クラスまたは構造体で演算子を定義する場合、パラメーターの少なくとも 1 つはそのクラスまたは構造体の型である必要があります。 単項演算子の場合は、唯一のオペランドは、そのクラスまたは構造体の型である必要があります。  
  
 **エラー ID:** BC33020  
  
### このエラーを解決するには  
  
-   パラメーターの型を、演算子が定義されているクラスまたは構造体の型に変更します。  
  
-   1 つのデータ型をパラメーターとして受け取り、演算の結果として別のデータ型を返す場合は、代わりに変換演算子を定義します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)