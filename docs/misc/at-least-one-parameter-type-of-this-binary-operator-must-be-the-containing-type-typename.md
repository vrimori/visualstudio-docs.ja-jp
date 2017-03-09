---
title: "この二項演算子のパラメーターのうち、少なくとも 1 つは包含する型 &#39;&lt;typename&gt;&#39; である必要があります | Microsoft Docs"
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
  - "bc33021"
  - "vbc33021"
helpviewer_keywords: 
  - "BC33021"
ms.assetid: 934d4d2e-d368-46d7-819e-5571cdc0ce4f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この二項演算子のパラメーターのうち、少なくとも 1 つは包含する型 &#39;&lt;typename&gt;&#39; である必要があります
二項演算子の定義では、演算子が定義されているクラスまたは構造体の型ではない型を使用して、両方のパラメーターを指定します。  
  
 クラスまたは構造体で演算子を定義するとき、パラメーターの少なくとも 1 つはそのクラスまたは構造体の型である必要があります。  
  
 **エラー ID:** BC33021  
  
### このエラーを解決するには  
  
-   どちらかまたは両方のパラメーターの型を、演算子が定義されているクラスまたは構造体の型に変更します。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)