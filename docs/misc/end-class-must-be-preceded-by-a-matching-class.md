---
title: "&#39;End Class&#39; の前には、対応する &#39;Class&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30460"
  - "bc30460"
helpviewer_keywords: 
  - "BC30460"
ms.assetid: 0e6989da-f281-4ac4-8579-b6d627be8de8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Class&#39; の前には、対応する &#39;Class&#39; を指定しなければなりません
`End Class` は、`Class` ブロックを終了するために使用します。そのため、ブロックの最後でだけ記述できます。 冗長な `End Class` があるか、または `End Class` ステートメントが対応する `Class` ブロックの境界の外側にあります。  
  
 **エラー ID:** BC30460  
  
### このエラーを解決するには  
  
-   冗長な `End Class` ステートメントを検索し、削除します。  
  
-   `End Class` ステートメントをコード内の適切な場所に移動します。  
  
## 参照  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)