---
title: "&#39;End Select&#39; の前には、対応する &#39;Select Case&#39; を指定する必要があります | Microsoft Docs"
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
  - "bc30088"
  - "vbc30088"
helpviewer_keywords: 
  - "BC30088"
ms.assetid: 9de8c0d4-4ce9-45cf-98d6-8f68bba507a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Select&#39; の前には、対応する &#39;Select Case&#39; を指定する必要があります
`End Select` ステートメントが発生していますが、対応する `Select` または `Select Case` ステートメントがありません。`End Select` の前に `Select` または `Select Case` ステートメントを指定する必要があります。  
  
 **エラー ID:** BC30088  
  
### このエラーを解決するには  
  
1.  この `Select` ブロックが入れ子になった `Select` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `Select` ブロック内の他の制御構造が正しく終了していることを確認します。  
  
3.  この `Select` ブロックが正しく書式設定されていることを確認します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)