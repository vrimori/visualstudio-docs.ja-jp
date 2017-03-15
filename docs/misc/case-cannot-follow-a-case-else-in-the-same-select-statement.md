---
title: "&#39;Case&#39; を、同一の &#39;Select&#39; ステートメント内で &#39;Case Else&#39; の後に置くことはできません | Microsoft Docs"
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
  - "bc30321"
  - "vbc30321"
helpviewer_keywords: 
  - "BC30321"
ms.assetid: eeedbceb-2c8d-4acb-b84c-8b42c058f083
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; を、同一の &#39;Select&#39; ステートメント内で &#39;Case Else&#39; の後に置くことはできません
`Case Else` ステートメントでは、最初の `Case` で一致するものが見つからない場合に実行するステートメントを指定します。`Case` ステートメントが、同じ `Select` ブロック内で `Case Else` の後に見つかりました。  
  
 **エラー ID:** BC30321  
  
### このエラーを解決するには  
  
-   `Case Else` を `Case` ステートメントの後ろの適切な位置に移動します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)