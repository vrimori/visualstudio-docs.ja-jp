---
title: "メソッド &#39;&lt;procedurename&gt;&#39; に対して推定された型引数には、次のエラーが表示されます: &lt;errorlist&gt; | Microsoft Docs"
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
  - "bc30954"
  - "vbc30954"
helpviewer_keywords: 
  - "BC30954"
ms.assetid: 796592c4-70b7-45be-9322-db09e9095d7d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;procedurename&gt;&#39; に対して推定された型引数には、次のエラーが表示されます: &lt;errorlist&gt;
ジェネリック プロシージャが型引数を指定せずに呼び出され、推定された型引数は 1 つ以上の制約違反となります。  
  
 通常、ジェネリック型を呼び出す場合は、ジェネリック型が定義する型パラメーターごとに型引数を指定します。 型引数を指定しない場合、コンパイラは型パラメーターに渡される型を推定しようとします。 推定された型が 1 つ以上の型パラメーターの制約を満たすことができない場合、コンパイラはこのエラーを生成します。  
  
 型パラメーターの*制約*は、型パラメーターに渡すことができる型引数を制限します。 たとえば、型パラメーターを <xref:System.IComparable%601> インターフェイスを実装するクラスに制限することができます。 詳細については、「[Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)」の「制約」を参照してください。  
  
 **エラー ID:** BC30954  
  
### このエラーを解決するには  
  
-   ジェネリック プロシージャに型引数を指定し、コンパイラが型引数を推定しなくて済むようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)