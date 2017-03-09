---
title: "&#39;Continue While&#39; は、&#39;While&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "vbc30784"
  - "bc30784"
helpviewer_keywords: 
  - "BC30784"
ms.assetid: b26c77b2-36ae-4dce-b048-f7c4b196faa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue While&#39; は、&#39;While&#39; ステートメント内でのみ使用できます
`Continue While` ステートメントは、`For...Next` ループ内でのみ使用できます。  
  
 **エラー ID:** BC30784  
  
### このエラーを解決するには  
  
1.  `Continue While` ステートメントが `Do...Loop` ループ内にある場合は、ステートメントを `Continue Do` に変更します。  
  
2.  `Continue While` ステートメントが `For...Next` ループ内にある場合は、ステートメントを `Continue For` に変更します。  
  
3.  それ以外の場合は `Continue While` ステートメントを削除します。  
  
## 参照  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)