---
title: "&#39;Continue Do&#39; は、&#39;Do&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "vbc30782"
  - "bc30782"
helpviewer_keywords: 
  - "BC30782"
ms.assetid: c6b35e63-4d84-449d-9685-41a1bc0a7f35
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue Do&#39; は、&#39;Do&#39; ステートメント内でのみ使用できます
`Continue Do` ステートメントは、`Do...Loop` ループ内でのみ使用できます。  
  
 **エラー ID:** BC30782  
  
### このエラーを解決するには  
  
1.  `Continue Do` ステートメントが `For...Next` ループ内にある場合は、ステートメントを `Continue For` に変更します。  
  
2.  `Continue Do` ステートメントが `While...End While` ループ内にある場合は、ステートメントを `Continue While` に変更します。  
  
3.  それ以外の場合は `Continue Do` ステートメントを削除します。  
  
## 参照  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)