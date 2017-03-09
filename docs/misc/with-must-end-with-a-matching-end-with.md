---
title: "&#39;With&#39; の終わりには、対応する &#39;End With&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30085"
  - "vbc30085"
helpviewer_keywords: 
  - "BC30085"
ms.assetid: aa88f4d0-be5f-4efe-a4ef-80e6d6124e6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;With&#39; の終わりには、対応する &#39;End With&#39; を指定しなければなりません
`With` ステートメントが発生していますが、対応する `End With` ステートメントがありません。`End With` ステートメントを使用して、`With` ブロックを終了する必要があります。  
  
 **エラー ID:** BC30085  
  
### このエラーを解決するには  
  
-   この `With` ブロックが入れ子になった `With` ブロックのセットの一部である場合は、各ブロックが正しく終了していることを確認します。  
  
-   `End With` ステートメントを `With` ブロックの最後に追加します。  
  
## 参照  
 [With...End With Statement](/dotnet/visual-basic/language-reference/statements/with-end-with-statement)