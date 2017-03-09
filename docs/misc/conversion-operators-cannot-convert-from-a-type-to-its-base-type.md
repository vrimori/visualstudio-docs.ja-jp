---
title: "変換演算子によって、ある型からその基本型に変換することはできません | Microsoft Docs"
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
  - "bc33026"
  - "vbc33026"
helpviewer_keywords: 
  - "BC33026"
ms.assetid: 3533cf71-6a52-4fd0-a1f2-127c4ecd56ae
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子によって、ある型からその基本型に変換することはできません
変換演算子に、パラメーター型の派生元の戻り値の型が宣言されています。  
  
 コンパイル時に [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、任意の参照型から継承階層内の任意の型、つまり派生元または派生先の型に存在する定義済みの変換が考慮されます。 このような変換は実行時に失敗する可能性がありますが、コンパイラは実行結果を予測できないため、これらの変換のコンパイルはすべて許可されます。  
  
 コンパイラでは、この変換が既に定義されていると見なされるため、この変換を再定義することはできません。  
  
 **エラー ID:** BC33026  
  
### このエラーを解決するには  
  
-   この演算子の定義を完全に削除します。 これは既に定義されています。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)