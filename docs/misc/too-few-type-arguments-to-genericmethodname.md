---
title: "&#39;&lt;genericMethodName&gt;&#39; の型引数が少なすぎます | Microsoft Docs"
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
  - "bc32042"
  - "vbc32042"
helpviewer_keywords: 
  - "BC32042"
ms.assetid: e887b068-4e84-4cb4-9649-94fe162a821e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;genericMethodName&gt;&#39; の型引数が少なすぎます
ジェネリック メソッドが、型パラメーターよりも少ない型引数を指定して呼び出されています。  
  
 ジェネリック メソッドを呼び出すときは、そのメソッドで定義されている型パラメーターごとに 1 つの型引数を指定する必要があります。  
  
 **エラー ID:** BC32042  
  
### このエラーを解決するには  
  
-   型引数リストに型引数を追加して、呼び出そうとするジェネリック メソッドのそれぞれの型パラメーターに対して型引数が 1 つあるようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)