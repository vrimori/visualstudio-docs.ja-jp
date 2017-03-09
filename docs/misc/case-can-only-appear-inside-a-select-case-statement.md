---
title: "&#39;Case&#39; は、&#39;Select Case&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "vbc30072"
  - "bc30072"
helpviewer_keywords: 
  - "BC30072"
ms.assetid: da808bc3-f154-444a-b547-3cf55beff8a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case&#39; は、&#39;Select Case&#39; ステートメント内でのみ使用できます
`Case` ステートメントが `Select` ブロックの外側にあります。`Case` ステートメントは、`Select` または `Select Case` ステートメントとそれに対応する `End Select` ステートメントとの間でのみ使用できます。  
  
 **エラー ID:** BC30072  
  
### このエラーを解決するには  
  
-   `Case` ステートメントを削除するか、または `Select` ブロック内に移動します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)