---
title: "XML リテラルは、かっこで囲まれている場合を除いて、ここでは使用できません。 | Microsoft Docs"
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
  - "bc31198"
  - "vbc31198"
helpviewer_keywords: 
  - "BC31198"
ms.assetid: 97b16076-39ff-430a-9c65-073d01bcb08e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML リテラルは、かっこで囲まれている場合を除いて、ここでは使用できません。
XML リテラル宣言が使用されている式内の場所が、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラにとってあいまいです。 つまり、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] コンパイラでは、小なり記号 \(\<\) が、比較演算子と XML リテラルの開始のどちらを意図しているか判断できません。 次にコード例を示します。  
  
 \[Visual Basic\]  
  
```  
' Generates an error. Dim queryResult = From element In elements _ Where <sample>Value</sample> = "Value" _ Select element  
```  
  
 **エラー ID:** BC31198  
  
### このエラーを解決するには  
  
-   次の例に示すように、かっこで XML リテラル宣言を囲みます。  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where (<sample> Value</sample>) = "Value" _ Select element  
    ```  
  
-   次の例に示すように、既存の XML リテラルを参照するようにコードを変更します。  
  
    ```vb#  
    Dim queryResult = From element In elements _ Where e.<sample>.Value = "Value" _ Select element  
    ```  
  
## 参照  
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML Axis Properties](/dotnet/visual-basic/language-reference/xml-axis/xml-axis-properties)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)