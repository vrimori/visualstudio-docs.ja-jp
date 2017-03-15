---
title: "&#39;&lt;genericproceduresignature&gt;&#39; の型パラメーター &#39;&lt;typeparametername&gt;&#39; に対して型引数を推定できませんでした | Microsoft Docs"
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
  - "vbc32051"
  - "bc32051"
helpviewer_keywords: 
  - "BC32051"
ms.assetid: a9c2a0ce-e225-4549-bfd8-d42df5d16bfd
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;genericproceduresignature&gt;&#39; の型パラメーター &#39;&lt;typeparametername&gt;&#39; に対して型引数を推定できませんでした
'\<genericproceduresignature\>' の型パラメーター '\<typeparametername\>' に対して型引数を推定できませんでした。 型引数を、パラメーター '\<parametername\>' に渡される引数から推定できませんでした。  
  
 ジェネリック プロシージャが型引数を指定せずに呼び出されたため、コンパイラはパラメーターのいずれかに渡す型を推定できません。  
  
 通常、ジェネリック プロシージャを呼び出す場合は、ジェネリック プロシージャで定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡す型を推定しようとします。 呼び出しのコンテキストから型パラメーターについて競合するデータ型情報が提供される場合、型の推定は失敗します。  
  
 次のコードでは、このエラーが生成される可能性があります。  
  
```  
Public Sub doSomething(Of t)(ByVal arg1 As t(), ByVal arg2 As t) End Sub Call doSomething(6, 42)  
```  
  
 前の例では、コンパイラは `arg2` に渡される 42 という値に基づいて `t` に対する型 `Integer` を推定します。 ただし、その推定には `arg1` が型 `Integer()` \(つまり、`Integer` の配列\) である必要があり、`arg1` に渡される値 6 はその型と一致しません。  
  
 **エラー ID:** BC32051  
  
### このエラーを解決するには  
  
-   ジェネリック プロシージャに型引数を指定し、コンパイラが型引数を推定しなくて済むようにします。  
  
-   型引数の型に一致する型で通常の引数を指定します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)