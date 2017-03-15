---
title: "&#39;Catch&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません | Microsoft Docs"
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
  - "bc30441"
  - "vbc30441"
helpviewer_keywords: 
  - "BC30441"
ms.assetid: 0e4756b4-1f29-4073-88c5-8f8c93ba6c9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Catch&#39; の終わりには、対応する &#39;End Try&#39; を指定しなければなりません
`Catch` ステートメントが、一致する `End Try` ステートメントなしでコードに記述されています。`Catch` ステートメントは、`End Try` ステートメントで終了する必要があります。  
  
 **エラー ID:** BC30441  
  
### このエラーを解決するには  
  
1.  `Catch` ステートメントを削除します。  
  
2.  ブロックを終了するための `End Try` ステートメントを追加します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)