---
title: "&#39;Group&#39; はこのコンテキストで許可されていません。識別子を指定してください | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36708"
  - "vbc36708"
helpviewer_keywords: 
  - "BC36708"
ms.assetid: ef6b453e-68e7-47c2-997c-9fd1ca074217
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Group&#39; はこのコンテキストで許可されていません。識別子を指定してください
`Group` キーワードが `Aggregate` 句の `Into` セクションに含まれています。`Group` キーワードは、`Group By` 句または `Group Join` 句でのみ有効です。  
  
 **エラー ID:** BC36618  
  
### このエラーを解決するには  
  
-   `Aggregate` 句から `Group` キーワードを削除します。 結果をグループ化する場合は、クエリに `Group By` 句を追加できます。  
  
## 参照  
 [Aggregate Clause](/dotnet/visual-basic/language-reference/queries/aggregate-clause)   
 [Group By 句](/dotnet/visual-basic/language-reference/queries/group-by-clause)   
 [Group Join Clause](/dotnet/visual-basic/language-reference/queries/group-join-clause)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)