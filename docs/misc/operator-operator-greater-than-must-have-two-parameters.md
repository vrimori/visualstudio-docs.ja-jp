---
title: "演算子 &#39;&lt;operator&gt;&#39; には、2 個のパラメーターを指定する必要があります | Microsoft Docs"
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
  - "bc33015"
  - "vbc33015"
helpviewer_keywords: 
  - "BC33015"
ms.assetid: 506ea996-8abe-4dbe-aff4-d3910bf4399e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子 &#39;&lt;operator&gt;&#39; には、2 個のパラメーターを指定する必要があります
バイナリ演算子が 2 つより少ないパラメーターか、2 つより多いパラメーターで定義されています。  
  
 バイナリ演算子には、厳密に 2 つのパラメーターを指定する必要があります。  
  
 **エラー ID:** BC33015  
  
### このエラーを解決するには  
  
-   2 つのパラメーターを指定するように、定義を調整します。  
  
-   必要なパラメーターが 1 つのみの場合は、単項演算子を定義する必要があります。  
  
-   パラメーターが不要な場合や、3 つ以上のパラメーターが必要な場合は、演算子を定義する代わりに、[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) を使用して `Function` プロシージャを定義する必要があります。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)