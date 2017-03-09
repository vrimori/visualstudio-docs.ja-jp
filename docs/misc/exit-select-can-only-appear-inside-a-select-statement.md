---
title: "&#39;Exit Select&#39; は、&#39;Select&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "vbc30099"
  - "bc30099"
helpviewer_keywords: 
  - "BC30099"
ms.assetid: 37c65fc8-6ad9-456a-80b8-66288c62ef24
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Select&#39; は、&#39;Select&#39; ステートメント内でのみ使用できます
`Exit Select` ステートメントが `Select` ブロックの外側にあります。`Exit Select` は、`Select` または `Select Case` ステートメントとそれに対応する `End Select` ステートメントとの間でのみ有効です。  
  
 **エラー ID:** BC30099  
  
### このエラーを解決するには  
  
1.  有効な `Select` または `Select Case` ステートメントが `Exit Select` よりも前にあり、有効な `End Select` ステートメントがそれよりも後にあることを確認します。  
  
2.  `Select` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)