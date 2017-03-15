---
title: "型引数が少なすぎます | Microsoft Docs"
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
  - "vbc36578"
  - "bc36578"
helpviewer_keywords: 
  - "BC36578"
ms.assetid: 881b3009-0c9e-4676-b172-c6aabd14ed14
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型引数が少なすぎます
ジェネリック メソッドを呼び出すときに指定された型引数の数が型パラメーターの数を下回っています。  
  
 ジェネリック メソッドを呼び出すときには、そのメソッドで定義されている型パラメーターごとに 1 つずつ型引数を指定する必要があります。  
  
 **エラー ID:** BC36578  
  
### このエラーを解決するには  
  
-   型引数リストに型引数を追加して、呼び出そうとするジェネリック メソッドのそれぞれの型パラメーターに型引数が 1 つずつあるようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)