---
title: "バイナリ &#39;If&#39; 演算子の 1 番目と 2 番目のオペランドの共通型を推論できません | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# バイナリ &#39;If&#39; 演算子の 1 番目と 2 番目のオペランドの共通型を推論できません
バイナリ 'If' 演算子の 1 番目と 2 番目のオペランドの共通型を推論できません。 一方が他方に対する拡大変換を持つ必要があります。  
  
 バイナリ `If` 演算子では、引数の 1 つともう 1 つの引数の間に拡大変換が必要です。 たとえば、`Integer` と `String` の間にはどちらの方向にも拡大変換がないため、次のコードでこのエラーが発生します。  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **エラー ID:** BC33110  
  
### このエラーを解決するには  
  
-   コードで可能な場合は、オペランドの 1 つに明示的な変換を提供します。  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   別の条件構造を使用して、コードを書き直します。  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## 参照  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)