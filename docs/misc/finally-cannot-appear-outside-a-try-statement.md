---
title: "&#39;Finally&#39; を &#39;Try&#39; ステートメントの外に置くことはできません。 | Microsoft Docs"
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
  - "vbc30382"
  - "bc30382"
helpviewer_keywords: 
  - "BC30382"
ms.assetid: 0314d8d2-18bc-4bbd-858c-0a18408b52fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Finally&#39; を &#39;Try&#39; ステートメントの外に置くことはできません。
`Finally` は `Try...Catch...Finally` ブロックを終了するために使用します。そのため、ブロックの最後で 1 回のみ出現できます。 不要な `Finally` ステートメントがあるか、または `Finally` ステートメントが、対応する `Try` ブロックの境界の外側にあります。  
  
 **エラー ID:** BC30382  
  
### このエラーを解決するには  
  
1.  不要な `Finally`ステートメントを見つけて削除します。  
  
2.  `Finally` ステートメントをコード内の適切な場所に移動します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)