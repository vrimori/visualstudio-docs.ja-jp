---
title: "&#39;End Using&#39; の前には、対応する &#39;Using&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc36007"
  - "vbc36007"
helpviewer_keywords: 
  - "BC36007"
ms.assetid: 10fb31ba-9b6c-403f-bacc-c7b5df14f1dd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Using&#39; の前には、対応する &#39;Using&#39; を指定しなければなりません
一致する `Using` 宣言を先に記述することなく、`End Using` ステートメントを記述しています。  
  
 **エラー ID:** BC36007  
  
### このエラーを解決するには  
  
-   `End Using` ステートメントが重複している場合は、削除します。  
  
-   [Using Statement](/dotnet/visual-basic/language-reference/statements/using-statement) が不足している場合は、指定します。  
  
-   `End Using` ステートメントをコード内の適切な場所に移動します。  
  
## 参照  
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)