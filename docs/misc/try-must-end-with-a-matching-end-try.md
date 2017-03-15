---
title: "&#39;Try&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30384"
  - "vbc30384"
helpviewer_keywords: 
  - "BC30384"
ms.assetid: 898300b4-c091-4105-aeb0-9bd559ff6b6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Try&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません
`Try` は `Try` ブロックを開始するために使用します。ブロックの先頭にのみ指定でき、対応する `End Try` ステートメントでブロックを終えます。`Try` が重複しているか、`Try` ブロックの最後に `Finally` が使用されませんでした。  
  
 **エラー ID:** BC30384  
  
### このエラーを解決するには  
  
1.  余分な `Try` を見つけて削除するか、ブロックの最後に対応する `End Try` を指定します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)