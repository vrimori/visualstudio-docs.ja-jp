---
title: "演算子 &#39;&lt;operator&gt;&#39; には、1 個または 2 個のパラメーターを指定する必要があります | Microsoft Docs"
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
  - "bc33016"
  - "vbc33016"
helpviewer_keywords: 
  - "BC33016"
ms.assetid: 70f43905-037e-4040-83c0-f39334b3e07a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 演算子 &#39;&lt;operator&gt;&#39; には、1 個または 2 個のパラメーターを指定する必要があります
単項演算子または 2 項演算子がパラメーターなしで定義されているか、3 個以上のパラメーターを使用して定義されています。  
  
 単項演算子または 2 項演算子には、1 個または 2 個のパラメーターを指定する必要があります。  
  
 **エラー ID:** BC33016  
  
### このエラーを解決するには  
  
-   1 個または 2 個のパラメーターを指定するように、定義を調整します。  
  
-   パラメーターが不要な場合や、3 個以上のパラメーターが必要な場合は、演算子を定義する代わりに、[Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement) を使用して `Function` プロシージャを定義する必要があります。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)