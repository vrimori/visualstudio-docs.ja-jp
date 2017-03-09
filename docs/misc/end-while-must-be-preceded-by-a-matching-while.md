---
title: "&#39;End While&#39; の前には、対応する &#39;While&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30090"
  - "bc30090"
helpviewer_keywords: 
  - "BC30090"
ms.assetid: 302b26b8-8fa4-4e49-86f0-d7c49fec485f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End While&#39; の前には、対応する &#39;While&#39; を指定しなければなりません
`End While` ステートメントがありますが、対応する `While` ステートメントがありません。`End While` の前に、対応する `While` ステートメントが必要です。  
  
 **エラー ID:** BC30090  
  
### このエラーを解決するには  
  
1.  この `While` ブロックが入れ子になった `While` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `While` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `While` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [While...End While Statement](/dotnet/visual-basic/language-reference/statements/while-end-while-statement)