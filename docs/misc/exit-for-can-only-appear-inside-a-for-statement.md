---
title: "&#39;Exit For&#39; は、&#39;For&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit For&#39; は、&#39;For&#39; ステートメント内でのみ使用できます
`Exit For` ステートメントが `For` ループの外側にあります。`Exit For` は、`For` または `For Each` ステートメントとそれに対応する `Next` ステートメントとの間でのみ有効です。  
  
 **エラー ID:** BC30096  
  
### このエラーを解決するには  
  
1.  有効な `For` または `For Each` ステートメントが `Exit For` よりも前にあり、有効な `Next` ステートメントがそれよりも後にあることを確認します。  
  
2.  `For` ループ内の他の制御構造が正しく終了していることを確認します。  
  
## 参照  
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)