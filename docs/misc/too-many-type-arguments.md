---
title: "型引数が多すぎます | Microsoft Docs"
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
  - "vbc36579"
  - "bc36579"
helpviewer_keywords: 
  - "BC36579"
ms.assetid: f59617b2-ca66-45c6-baaa-3c8bdf7f9a55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型引数が多すぎます
ジェネリック メソッドが、型パラメーターよりも多い型引数を指定して呼び出されています。  
  
 ジェネリック メソッドを呼び出すときは、そのメソッドで定義されている型パラメーターごとに 1 つの型引数を指定する必要があります。  
  
 **エラー ID:** BC36579  
  
### このエラーを解決するには  
  
-   型引数リストから型引数を削除して、呼び出すジェネリック メソッドの型パラメーターごとに型引数が 1 つになるようにします。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)