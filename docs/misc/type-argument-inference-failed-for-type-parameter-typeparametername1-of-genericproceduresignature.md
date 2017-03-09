---
title: "&#39;&lt;genericproceduresignature&gt;&#39; の型パラメーター &#39;&lt;typeparametername1&gt;&#39; に対して型引数を推定できませんでした | Microsoft Docs"
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
  - "vbc32116"
  - "bc32116"
helpviewer_keywords: 
  - "BC32116"
ms.assetid: 6bfb02ec-814a-4b1f-a585-6d902a861d00
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;genericproceduresignature&gt;&#39; の型パラメーター &#39;&lt;typeparametername1&gt;&#39; に対して型引数を推定できませんでした
'\<genericproceduresignature\>' の型パラメーター '\<typeparametername1\>' に対して型引数を推定できませんでした。 パラメーター '\<parametername1\>' に渡される引数から推論される型引数が、パラメーター '\<parametername2\>' に渡される引数から推論される型引数と競合します。  
  
 ジェネリック プロシージャが型引数を指定せずに呼び出されており、型の推定によって、型パラメーターの間で競合するデータ型が生成されています。  
  
 通常、ジェネリック プロシージャを呼び出す場合は、ジェネリック プロシージャで定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡す型を推定しようとします。 呼び出しのコンテキストから型パラメーターについて競合するデータ型情報が提供される場合、型の推定は失敗します。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
```  
Public Sub takeTwoValues(Of t)(ByVal x As t, ByVal y As t) End Sub Call takeTwoValues(4, 2.5)  
```  
  
 コンパイラは、最初の引数から型パラメーター `t` に対して `Integer` を推論しますが、2 番目の引数では同じ型パラメーターに対して `Double` を推論するため、`t` に渡すデータ型に関して競合が発生します。  
  
 **エラー ID:** BC32116  
  
### このエラーを解決するには  
  
-   ジェネリック型に型引数を指定し、コンパイラが型引数を推定しなくて済むようにします。  
  
    ```  
    Call takeTwoValues(Of Double)(4, 2.5)  
    ```  
  
     この場合、通常の 2 つの引数はデータ型が異なるため、呼び出し元のコードは両方のデータ型に適合する型引数を渡す必要があります。 この例では、`Integer` は `Double` に拡大変換されます。  
  
     または  
  
-   ジェネリック プロシージャを再定義して、通常のパラメーターに対して異なる型パラメーターを指定し、型の推論による競合が発生しないようにします。  
  
    ```  
    Public Sub takeTwoValues(Of t1, t2)(ByVal x As t1, ByVal y As t2)  
    ```  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)