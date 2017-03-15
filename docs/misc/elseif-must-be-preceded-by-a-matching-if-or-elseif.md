---
title: "&#39;ElseIf&#39; の前には、対応する &#39;If&#39; または &#39;ElseIf&#39; が必要です | Microsoft Docs"
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
  - "bc36005"
  - "vbc36005"
helpviewer_keywords: 
  - "BC36005"
ms.assetid: bcebae85-b438-4839-bada-2f8f8dcc8a86
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ElseIf&#39; の前には、対応する &#39;If&#39; または &#39;ElseIf&#39; が必要です
`ElseIf` ステートメントがありますが、対応する `If` ステートメントがありません。`ElseIf` の前に、`If` ステートメントまたは別の `ElseIf` ステートメントが必要です。  
  
 **エラー ID:** BC36005  
  
### このエラーを解決するには  
  
1.  この `If` ブロックが入れ子になった制御構造のセットの一部である場合は、各構造が正しく終了しているかどうかを確認します。  
  
2.  `If` ブロック内で入れ子になっている他の制御構造が正しく終了していることを確認します。  
  
3.  この `If` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Decision Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/decision-structures)