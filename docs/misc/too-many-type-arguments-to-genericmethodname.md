---
title: "&#39;&lt;genericMethodName&gt;&#39; の型引数が多すぎます | Microsoft Docs"
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
  - "bc32043"
  - "vbc32043"
helpviewer_keywords: 
  - "BC32043"
ms.assetid: c4d8f67a-4317-461a-9446-6717cfa1d888
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;genericMethodName&gt;&#39; の型引数が多すぎます
ジェネリックメソッドが、型パラメーターよりも多い型引数を指定して呼び出されています。  
  
 ジェネリック メソッドを呼び出すときは、そのメソッドで定義されている型パラメーターごとに 1 つの型引数を指定する必要があります。  
  
 **エラー ID:** BC32043  
  
### このエラーを解決するには  
  
-   型引数リストから型引数を削除して、呼び出すジェネリック メソッドの型パラメーターごとに型引数が 1 つになるようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)