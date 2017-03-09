---
title: "ループの境界とステップの変数が同じ型に拡大変換されないため、&#39;&lt;variablename&gt;&#39; の型があいまいです | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ループの境界とステップの変数が同じ型に拡大変換されないため、&#39;&lt;variablename&gt;&#39; の型があいまいです
コードに `For...Next` ループが含まれていますが、次の条件が満たされているため、コンパイラはそのループの中でループ コントロール変数のデータ型を推論できません。  
  
-   ループ コントロール変数のデータ型が `As` 句で指定されていません。  
  
-   ループ境界とステップ変数に少なくとも 2 つのデータ型が含まれています。  
  
-   複数のデータ型変換の可能性があります。  
  
-   候補の中に最適な型がないため、ループ コントロール変数の型の選択があいまいです。  
  
 たとえば、次のループには、`Integer` 型のループ境界と `UInteger` 型のループ境界が 1 つずつあります。  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 `Integer` と `UInteger`、および `UInteger` と `Integer` の間で変換が可能ですが、どちらも縮小変換であり、最適な選択ではありません。  
  
 次の例では、`Double` 型の 3 つ目の変数が追加されています。`Integer` と `UInteger` の両方に `Double` に対する標準の拡大変換があるため、`Double` への変換が最適な選択となります。 型の推定によって、ループ コントロール変数 `i` にデータ型 `Double` が割り当てられます。  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **エラー ID:** BC30983  
  
### このエラーを解決するには  
  
-   いずれかの変数を、他の変数にとって拡大変換がある型に明示的に変換します。たとえば、次のようにします。  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   `As` 句を使用して、コントロール変数の型を指定します。  
  
    ```  
    For i As Double = m To n   
    ```  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)