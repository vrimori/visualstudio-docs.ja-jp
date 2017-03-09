---
title: "&#39;Structure&#39; 制約が指定された型パラメーターを制約として使用することはできません | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Structure&#39; 制約が指定された型パラメーターを制約として使用することはできません
`Structure` 制約が指定された型パラメーターが、別の型パラメーターの制約として使用されています。  
  
 `Structure` 制約では、その型パラメーターに渡される型引数が値型であることが要求されます。 ただし、値型を実装または継承することはできないため、型パラメーターを制約として使用しても意味はなく、他の型パラメーターに対し、実装または継承を要求することになります。  
  
 このことは、両方の型引数がまったく同じ型の場合にのみ意味があります。 この場合、ジェネリック型に型パラメーターは 1 つのみ必要となります。  
  
 このエラーは次のようなステートメントで発生することがあります。  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 `t1` に渡される型は値型である必要があるため、`t2` に渡される型は、`t1` に渡される型を実装または継承できません。  
  
 **エラー ID:** BC32114  
  
### このエラーを解決するには  
  
-   `Structure` に制限された型パラメーターを、他の型パラメーターの制約リストから削除します。  
  
-   両方の型パラメーターに同じ値型が必要な場合は、1 つの型パラメーターのみを持つジェネリック型を定義します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)