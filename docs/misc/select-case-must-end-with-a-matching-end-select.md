---
title: "&#39;Select Case&#39; の終わりには、対応する &#39;End Select&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30095"
  - "bc30095"
helpviewer_keywords: 
  - "BC30095"
ms.assetid: f0809aa5-e6c9-43c9-9664-4ff02825c3d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Select Case&#39; の終わりには、対応する &#39;End Select&#39; を指定しなければなりません
`Select` ステートメントまたは `Select Case` ステートメントがありますが、対応する `End Select` ステートメントがありません。`End Select` ステートメントを使用して、`Select` ブロックを終了する必要があります。  
  
 **エラー ID:** BC30095  
  
### このエラーを解決するには  
  
1.  この `Select` ブロックが入れ子になった `Select` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
2.  `End Select` ステートメントを `Select` ブロックの最後に追加します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)