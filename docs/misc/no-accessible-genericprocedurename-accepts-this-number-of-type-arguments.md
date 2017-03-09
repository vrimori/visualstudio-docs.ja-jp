---
title: "この型引数の数を受け入れるアクセス可能な &#39;&lt;genericprocedurename&gt;&#39; がありません | Microsoft Docs"
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
  - "bc32118"
  - "vbc32118"
helpviewer_keywords: 
  - "BC32118"
ms.assetid: 4ee942ba-0fa1-4ec1-9c2c-a0c0dc3f1b17
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この型引数の数を受け入れるアクセス可能な &#39;&lt;genericprocedurename&gt;&#39; がありません
ステートメントが複数のオーバーロードされたバージョンを持つジェネリック プロシージャを呼び出しています。しかし、呼び出しに指定された型引数と同じ数の型パラメーターを定義した、オーバーロードされたバージョンが 1 つもありません。  
  
 ジェネリック バージョンが 1 つしかない場合は、型引数を指定しなくても、そのジェネリック バージョンを呼び出すことができます。また、コンパイラは*型の推定*を試行できます。 詳細については、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「型の推定」を参照してください。 ただし、複数のジェネリック バージョンがある場合は、型引数を指定しない限り、コンパイラがその中の 1 つを選択することはできません。 型引数を 1 つ指定する場合は、オーバーロードされたバージョンの 1 つに定義されている、すべての型パラメーターに対して、型引数を指定する必要があります。  
  
 **エラー ID:** BC32118  
  
### このエラーを解決するには  
  
-   オーバーロードされたバージョンのうち、どれを呼び出すかを決定してから、正しい数の型引数を指定します。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)