---
title: "&#39;Else&#39; の前には、対応する &#39;If&#39; または &#39;ElseIf&#39; が必要です | Microsoft Docs"
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
  - "bc30086"
  - "vbc30086"
helpviewer_keywords: 
  - "BC30086"
ms.assetid: 5e76b3c6-571f-4a6f-b524-26150cb6e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Else&#39; の前には、対応する &#39;If&#39; または &#39;ElseIf&#39; が必要です
`Else` ステートメントがありますが、対応する `If` ステートメントがありません。`Else` の前に `If` ステートメントを指定する必要があります。  
  
 **エラー ID:** BC30086  
  
### このエラーを解決するには  
  
1.  この `If` ブロックが入れ子になった `If` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `If` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `If` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)