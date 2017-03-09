---
title: "&#39;Equals&#39; 演算子の両辺で、少なくとも 1 つの範囲変数を参照しなければなりません。 | Microsoft Docs"
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
  - "vbc36622"
  - "bc36622"
helpviewer_keywords: 
  - "BC36622"
ms.assetid: 8d301227-131d-4977-b3ff-1fc4e427f8fa
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; 演算子の両辺で、少なくとも 1 つの範囲変数を参照しなければなりません。
'Equals' 演算子の両辺で、少なくとも 1 つの範囲変数を参照しなければなりません。 範囲変数 \<variable\(s\)\> が 'Equals' 演算子の片側にあり、範囲変数 \<variable\(s\)\> がもう一方になければなりません。  
  
 LINQ クエリで結合するコレクションで示されている範囲変数が、示されているコレクションに応じて `Equals` 演算子の反対側になければなりません。 つまり、結合するコレクションで示されている範囲変数は、`Equals` 演算子を挟んで、結合対象のもう一方のコレクションの範囲変数の反対側になければなりません。 別個のコレクションの範囲変数を `Equals` 演算子の同じ側に一緒に配置することはできません。  
  
 結合対象の各コレクションの少なくとも 1 つの変数が、`Equals` 演算子のそれぞれの側で参照される必要があります。  
  
 **エラー ID:** BC36622  
  
## 参照  
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [From Clause](/dotnet/visual-basic/language-reference/queries/from-clause)   
 [Select Clause](/dotnet/visual-basic/language-reference/queries/select-clause)