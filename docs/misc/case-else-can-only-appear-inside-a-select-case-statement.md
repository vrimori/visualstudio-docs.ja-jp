---
title: "&#39;Case Else&#39; は、&#39;Select Case&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "bc30071"
  - "vbc30071"
helpviewer_keywords: 
  - "BC30071"
ms.assetid: 9a4f8ccb-717a-4d18-91b4-4a373202c38a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Case Else&#39; は、&#39;Select Case&#39; ステートメント内でのみ使用できます
`Case Else` ステートメントが `Select` ブロックの外側にあります。`Case Else` ステートメントは、`Select` または `Select Case` ステートメントとそれに対応する `End Select` ステートメントとの間でのみ使用できます。  
  
 **エラー ID:** BC30071  
  
### このエラーを解決するには  
  
-   `Case Else` ステートメントを削除するか、または `Select` ブロック内に移動します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)