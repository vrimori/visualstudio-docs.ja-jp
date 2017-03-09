---
title: "範囲変数 &lt;variable&gt; により、それを囲むブロック内の変数、または以前にクエリ式で定義された範囲変数が非表示になります。 | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 範囲変数 &lt;variable&gt; により、それを囲むブロック内の変数、または以前にクエリ式で定義された範囲変数が非表示になります。
クエリの範囲変数の名前は、同じスコープ内に以前に定義した変数か、クエリ内に以前に定義した範囲変数と同じ名前になります。  
  
 **エラー ID:** BC30978  
  
### このエラーを解決するには  
  
-   クエリ内のすべての範囲変数の名前が同じスコープ内の既存の変数名と重複しない一意の名前であることを確認します。  
  
-   入れ子にしたクエリで制御変数名が重複する場合には、各クエリをかっこで囲み、範囲変数ごとにスコープを分けます。  
  
## 参照  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)