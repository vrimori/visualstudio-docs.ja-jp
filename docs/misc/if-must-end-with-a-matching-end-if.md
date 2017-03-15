---
title: "&#39;If&#39; の終わりには、対応する &#39;End If&#39; を指定しなければなりません。 | Microsoft Docs"
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
  - "bc30081"
  - "vbc30081"
helpviewer_keywords: 
  - "BC30081"
ms.assetid: e5905d59-56bb-4daf-aca5-5ff847fc62f6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;If&#39; の終わりには、対応する &#39;End If&#39; を指定しなければなりません。
`If` ステートメントがあるのに、対応する `End If` ステートメントがありません。`End If` ステートメントを使用して、`If` ブロックを終了する必要があります。  
  
 **エラー ID:** BC30081  
  
### このエラーを解決するには  
  
1.  この `If` ブロックが入れ子になった `If` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `End If` ステートメントを `If` ブロックの最後に追加します。  
  
## 参照  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)