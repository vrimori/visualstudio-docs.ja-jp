---
title: "&#39;Exit Try&#39; は、&#39;Try&#39; ステートメント内部でのみ使用できます | Microsoft Docs"
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
  - "vbc30393"
  - "bc30393"
helpviewer_keywords: 
  - "BC30393"
ms.assetid: b8651df3-a32f-478c-a6d8-aa0ef584155f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Try&#39; は、&#39;Try&#39; ステートメント内部でのみ使用できます
`Exit Try` は、`Try` ブロック ステートメント内でのみ使用できます。 冗長な `Exit Try` ステートメントがあるか、または `Exit Try` ステートメントが対応する `Try` ブロックの境界の外側にあります。  
  
 **エラー ID:** BC30393  
  
### このエラーを解決するには  
  
1.  不要な `Exit Try` ステートメントを見つけて削除します。  
  
2.  `Exit Try` ステートメントをコード内の適切な場所に移動します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)