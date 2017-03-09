---
title: "アクセス可能な非ジェネリック &#39;&lt;procedurename&gt;&#39; が見つかりません | Microsoft Docs"
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
  - "vbc32117"
  - "bc32117"
helpviewer_keywords: 
  - "BC32117"
ms.assetid: a7bf8b67-8a0a-499e-9992-dc00e09b7ff4
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# アクセス可能な非ジェネリック &#39;&lt;procedurename&gt;&#39; が見つかりません
ステートメントが、オーバーロードされたバージョンが複数あるプロシージャを呼び出しましたが、オーバーロードされたバージョンはすべてジェネリックであり、呼び出しで型引数は指定されていません。  
  
 ジェネリック バージョンが 1 つのみで、型引数を指定しないで呼び出す場合は、コンパイラは*型の推定*を試行できます。 詳細については、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「型の推定」を参照してください。 ただし、複数のジェネリック バージョンがある場合は、型引数を指定しない限り、コンパイラがその中の 1 つを選択することはできません。 型引数を 1 つ指定する場合は、オーバーロードされたバージョンの 1 つで定義されているすべての型パラメーターに対して、型引数を指定する必要があります。  
  
 **エラー ID:** BC32117  
  
### このエラーを解決するには  
  
-   型引数リストを指定してプロシージャを呼び出します。  
  
## 参照  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)