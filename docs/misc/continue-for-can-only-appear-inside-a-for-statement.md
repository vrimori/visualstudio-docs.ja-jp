---
title: "&#39;Continue For&#39; は、&#39;For&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "bc30783"
  - "vbc30783"
helpviewer_keywords: 
  - "BC30783"
ms.assetid: 70891018-27c8-4d36-b168-8cc7177d70cb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Continue For&#39; は、&#39;For&#39; ステートメント内でのみ使用できます
`Continue For` ステートメントは、`For...Next` ループ内でのみ使用できます。  
  
 **エラー ID:** BC30783  
  
### このエラーを解決するには  
  
1.  `Continue For` ステートメントが `Do...Loop` 内にある場合は、ステートメントを `Continue Do` に変更します。  
  
     または  
  
     `Continue For` ステートメントが `While...End While` ループ内にある場合は、ステートメントを `Continue While` に変更します。  
  
2.  それ以外の場合は `Continue For` ステートメントを削除します。  
  
## 参照  
 [Continue Statement](/dotnet/visual-basic/language-reference/statements/continue-statement)   
 [For...Next ステートメント](/dotnet/visual-basic/language-reference/statements/for-next-statement)