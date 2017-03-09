---
title: "&#39;Exit While&#39; は、&#39;While&#39; ステートメント内でのみ使用できます。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30097"
  - "bc30097"
helpviewer_keywords: 
  - "BC30097"
ms.assetid: cf0a3e09-5252-4198-bb27-c103c98d9f19
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit While&#39; は、&#39;While&#39; ステートメント内でのみ使用できます。
`Exit While` ステートメントが `While` ブロックの外側にあります。`Exit While` は、`While` ステートメントとそれに対応する `End While` ステートメントとの間でのみ有効です。  
  
 **エラー ID:** BC30097  
  
### このエラーを解決するには  
  
1.  有効な `While` ステートメントが `Exit While` よりも前にあり、有効な `End While` ステートメントがそれよりも後にあることを確認します。  
  
2.  `While` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
## 参照  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)