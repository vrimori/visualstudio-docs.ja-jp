---
title: "&#39;End With&#39; の前には、対応する &#39;With&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30093"
  - "vbc30093"
helpviewer_keywords: 
  - "BC30093"
ms.assetid: b0f1f7d5-0c33-4b97-8043-f0f5b40ca5d7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End With&#39; の前には、対応する &#39;With&#39; を指定しなければなりません
`End With` ステートメントがあるのに、対応する `With` ステートメントがありません。`End With` の前に、対応する `With` ステートメントが必要です。  
  
 **エラー ID:** BC30093  
  
### このエラーを解決するには  
  
1.  この `With` ブロックが入れ子になった `With` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `With` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `With` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [With...End With Statement](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)