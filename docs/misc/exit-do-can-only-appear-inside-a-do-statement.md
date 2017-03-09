---
title: "&#39;Exit Do&#39; は、&#39;Do&#39; ステートメント内でのみ使用できます | Microsoft Docs"
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
  - "bc30089"
  - "vbc30089"
helpviewer_keywords: 
  - "BC30089"
ms.assetid: 0e1d0b35-e42b-4b90-b8a2-91fd6ef44f06
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Do&#39; は、&#39;Do&#39; ステートメント内でのみ使用できます
`Exit Do` ステートメントが `Do` ループの外側にあります。`Exit Do` は、`Do` ステートメントとそれに対応する `Loop` ステートメントとの間でのみ有効です。  
  
 **エラー ID:** BC30089  
  
### このエラーを解決するには  
  
1.  有効な `Do` ステートメントが `Exit Do` よりも前にあり、有効な `Loop` ステートメントがそれよりも後にあることを確認します。  
  
2.  `Do` ループ内の他の制御構造が正しく終了していることを確認します。  
  
## 参照  
 [Do...Loop Statement](/dotnet/visual-basic/language-reference/statements/do-loop-statement)