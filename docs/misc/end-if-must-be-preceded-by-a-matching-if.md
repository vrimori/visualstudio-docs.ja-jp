---
title: "&#39;End If&#39; の前には、対応する &#39;If&#39; を指定する必要があります | Microsoft Docs"
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
  - "bc30087"
  - "vbc30087"
helpviewer_keywords: 
  - "BC30087"
ms.assetid: 81c056bb-267e-44ef-9a44-3a41273090ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End If&#39; の前には、対応する &#39;If&#39; を指定する必要があります
`End If` ステートメントが発生していますが、対応する `If` ステートメントがありません。`End If` の前に `If` ステートメントを指定する必要があります。  
  
 **エラー ID:** BC30087  
  
### このエラーを解決するには  
  
1.  この `If` ブロックが入れ子になった `If` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `If` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `If` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)