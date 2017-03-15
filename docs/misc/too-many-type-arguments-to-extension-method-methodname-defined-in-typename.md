---
title: "&#39;&lt;typeName&gt;&#39; で定義された拡張メソッド &#39;&lt;methodName&gt;&#39; の型引数が多すぎます | Microsoft Docs"
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
  - "bc36591"
  - "vbc36591"
helpviewer_keywords: 
  - "BC36591"
ms.assetid: 504c9b1f-f511-4198-8970-136d1a1bdafe
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typeName&gt;&#39; で定義された拡張メソッド &#39;&lt;methodName&gt;&#39; の型引数が多すぎます
ジェネリック拡張メソッドが、型パラメーターよりも多い型引数を指定して呼び出されています。  
  
 ジェネリック メソッドを呼び出すときは、そのメソッドで定義されている型パラメーターごとに 1 つの型引数を指定する必要があります。  
  
 **エラー ID:** BC36591  
  
### このエラーを解決するには  
  
-   型引数リストから型引数を削除して、呼び出すジェネリック メソッドの型パラメーターごとに型引数が 1 つになるようにします。  
  
## 参照  
 [拡張メソッド](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)