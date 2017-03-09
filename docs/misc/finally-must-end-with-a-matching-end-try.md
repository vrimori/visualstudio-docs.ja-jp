---
title: "&#39;Finally&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません | Microsoft Docs"
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
  - "vbc30442"
  - "bc30442"
helpviewer_keywords: 
  - "BC30442"
ms.assetid: 36cce657-186c-4ba0-a760-abcef9529f18
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません
`Finally` ステートメントが、一致する `End Try`ステートメントなしでコードに記述されています。`Finally` ステートメントは、`End Try` ステートメントで終了する必要があります。  
  
 **エラー ID:** BC30442  
  
### このエラーを解決するには  
  
1.  `Finally` ステートメントを削除します。  
  
2.  ブロックを終了するための `End Try` ステートメントを追加します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)