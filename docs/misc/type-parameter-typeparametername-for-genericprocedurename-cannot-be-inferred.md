---
title: "&#39;&lt;genericprocedurename&gt;&#39; の型パラメーター &#39;&lt;typeparametername&gt;&#39; を推論できません | Microsoft Docs"
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
  - "vbc32050"
  - "bc32050"
helpviewer_keywords: 
  - "BC32050"
ms.assetid: e4a69ffb-0764-4e5a-8de1-40f881a3f4fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;genericprocedurename&gt;&#39; の型パラメーター &#39;&lt;typeparametername&gt;&#39; を推論できません
型引数リストを指定せずにジェネリック プロシージャが呼び出されており、いずれかの型引数についての型の推定が失敗しました  
  
 ジェネリック プロシージャを呼び出す場合は、通常、そのプロシージャで定義されている型パラメーターごとに型引数を指定します。 しかし、型引数リストを完全に省略することもできます。 その場合、コンパイラは、呼び出しのコンテキストから、各型引数の型を推定しようとします。 詳しくは、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「型の推定」をご覧ください。  
  
 型の推定が失敗する原因の 1 つとしては、型パラメーターと呼び出し元の型の間でランクが一致しないことが考えられます。 次に例を示します。  
  
```  
Public Sub displayLargest(Of t As IComparable)(ByVal arg() As t) ' Insert code to find and display the largest element of arg(). End Sub Public Sub callGenericSub() Dim testValue As Integer findLargest(testValue) Dim testMatrix(,) As Integer findLargest(testMatrix) End Sub  
```  
  
 上記のコードでは、`findLargest` に対する 2 回の呼び出しの両方でエラーが生成されます。型パラメーター `t` には 1 次元配列が必要ですが、呼び出しに基づいてコンパイラが推定する型引数はスカラー \(`testValue`\) と 2 次元配列 \(`testMatrix`\) であるためです。  
  
 **エラー ID:** BC32050  
  
### このエラーを解決するには  
  
-   型の推定と、ジェネリック プロシージャで宣言された型パラメーターとが一致するよう、標準の引数の型を設定します。  
  
     または  
  
-   完全な型引数リストを指定してジェネリック プロシージャを呼び出し、型の推定が不要になるようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)