---
title: "&#39;&lt;variablename&gt;&#39; の型を &#39;&lt;variablename&gt;&#39; を含んでいる式から推定することはできません | Microsoft Docs"
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
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;variablename&gt;&#39; の型を &#39;&lt;variablename&gt;&#39; を含んでいる式から推定することはできません
コンパイラは、宣言内で初期値の設定に変数が使用されている場合は、変数のデータ型を推定できません。  
  
 たとえば、`Option Infer` を `On` に設定すると、次の例はコンパイルされません。  
  
-   宣言  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   `For`  ループ  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   `For Each`  ループ  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **エラー ID:** BC30980  
  
### このエラーを解決するには  
  
-   2 つの変数で参照する値が異なる場合は、宣言する変数の名前を変更します。  
  
-   初期値に変数名の代わりにリテラル値を使用します \(代入の右辺\)。  
  
-   `As` 句を使用して、宣言する変数の型を指定します。  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [For Each...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)