---
title: "&#39;Delegate&#39; の後には、&#39;Sub&#39; または &#39;Function&#39; が必要です | Microsoft Docs"
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
  - "vbc30278"
  - "bc30278"
helpviewer_keywords: 
  - "BC30278"
ms.assetid: fee206b9-8dc0-436f-9909-abd8c17957f8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Delegate&#39; の後には、&#39;Sub&#39; または &#39;Function&#39; が必要です
`Delegate` ステートメントに、`Sub` または `Function` プロシージャが指定されていません。`Sub` または `Function` キーワードは、`Delegate` キーワードの直後に配置する必要があります。  
  
 **エラー ID:** BC30278  
  
### このエラーを解決するには  
  
1.  `Sub` または `Function` キーワードを `Delegate` の直後に配置します。  
  
2.  適切なプロシージャ名、引数リスト、および戻り値の型を指定します。  
  
## 参照  
 [Delegate Statement](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/index)