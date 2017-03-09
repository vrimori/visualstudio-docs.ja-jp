---
title: "ラムダ パラメーター &#39;&lt;parameter&gt;&#39; により、それを囲むブロック内の変数、以前に定義された範囲変数、クエリ式内で暗黙的に宣言された変数が非表示になります。 | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ラムダ パラメーター &#39;&lt;parameter&gt;&#39; により、それを囲むブロック内の変数、以前に定義された範囲変数、クエリ式内で暗黙的に宣言された変数が非表示になります。
ラムダ式で使用されている変数の名前が、同じスコープの中で既に定義されている変数の名前と重複しています。 その変数は、入れ子のラムダ式を囲むコード ブロック内の変数、LINQ クエリ内で既に定義されている範囲変数、LINQ クエリで暗黙的に宣言されている変数のいずれかです。  
  
 **エラー ID:** BC36641  
  
### このエラーを解決するには  
  
-   ラムダ式のすべての変数を一意の名前にして、同じスコープにある既存の変数名と重複しないようにします。  
  
## 参照  
 [Lambda Expressions](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)