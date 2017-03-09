---
title: "変換演算子によって Object に変換することはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33028"
  - "vbc33028"
helpviewer_keywords: 
  - "BC33028"
ms.assetid: 064b478c-85a1-4e13-a292-d8aebb079cad
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 変換演算子によって Object に変換することはできません。
変換演算子が、戻り値の型 [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type) を使用して宣言されます。  
  
 コンパイル時に [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、任意の参照型から継承階層内の任意の型、つまり派生元または派生先の型に存在する定義済みの変換が考慮されます。`Object` は [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] の汎用データ型であるため、すべての型が `Object` から派生します。  
  
 コンパイラでは、この変換が既に定義されていると見なされるため、この変換を再定義することはできません。  
  
 **エラー ID:** BC33028  
  
### このエラーを解決するには  
  
-   この演算子の定義を完全に削除します。 これは既に定義されています。  
  
## 参照  
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [汎用データ型としてのオブジェクト \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/5315bf21-2b22-45ab-98cd-5631dffbcb2f)