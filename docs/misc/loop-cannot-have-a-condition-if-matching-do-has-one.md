---
title: "対応する &#39;Do&#39; に条件がある場合、&#39;Loop&#39; に条件を指定することはできません | Microsoft Docs"
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
  - "vbc30238"
  - "bc30238"
helpviewer_keywords: 
  - "BC30238"
ms.assetid: 81513cb5-69e7-4d62-b33e-e54cb8c5e8bf
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 対応する &#39;Do&#39; に条件がある場合、&#39;Loop&#39; に条件を指定することはできません
`Loop` ステートメントに `While` 句または `Until` 句が含まれ、対応する `Do` ステートメントにもそのような句が含まれています。 ループ内の `Do` ステートメントと `Loop` ステートメントの 1 つにのみ、条件を指定できます。  
  
 **エラー ID:** BC30238  
  
### このエラーを解決するには  
  
-   `Do` ステートメントまたは `Loop` ステートメントのいずれかから `While` 句または `Until` 句を削除します。  
  
## 参照  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)