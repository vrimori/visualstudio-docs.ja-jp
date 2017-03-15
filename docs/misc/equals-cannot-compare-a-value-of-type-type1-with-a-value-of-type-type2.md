---
title: "&#39;Equals&#39; で型 &lt;type1&gt; の値と型 &lt;type2&gt; の値を比較することはできません | Microsoft Docs"
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
  - "vbc36621"
  - "bc36621"
helpviewer_keywords: 
  - "BC36621"
ms.assetid: bd40bf57-3a12-407a-8622-7e428850c77c
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Equals&#39; で型 &lt;type1&gt; の値と型 &lt;type2&gt; の値を比較することはできません
`Join` 句または `Group Join` 句の `Equals` 演算子が、定義されていない方法でデータ型を比較しようとしました。`Boolean` 値と `Date` 型の比較などが考えられます。  
  
 **エラー ID:** BC36621  
  
### このエラーを解決するには  
  
-   `Equals` 演算子の各辺の値が共通のデータ型に変換できることを確認します。 これを実現するには、次のようなオプションがあります。  
  
    -   `CType` 関数を使用して、1 つ以上の値を特定の型に変換します。  
  
    -   <xref:System.Convert> クラスまたは変換メソッドを使用して、1 つ以上の値を共通の不変型に変換します。  
  
    -   `ToString` メソッドを使用して値を文字列に変換します。  
  
## 参照  
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [Join Clause](/dotnet/visual-basic/language-reference/queries/join-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)