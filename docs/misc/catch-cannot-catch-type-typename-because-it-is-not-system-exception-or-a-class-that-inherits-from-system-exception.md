---
title: "型 &#39;&lt;typename&gt;&#39; は、&#39;System.Exception&#39;、または &#39;System.Exception&#39; から継承するクラスではないため、&#39;Catch&#39; でキャッチできません | Microsoft Docs"
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
  - "vbc30392"
  - "bc30392"
helpviewer_keywords: 
  - "BC30392"
ms.assetid: 1d513d1d-38f5-4b4e-95bb-9f1209553803
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型 &#39;&lt;typename&gt;&#39; は、&#39;System.Exception&#39;、または &#39;System.Exception&#39; から継承するクラスではないため、&#39;Catch&#39; でキャッチできません
`Catch` は例外のみをインターセプトできますが、例外から派生していないものを検出しようとしました。  
  
 **エラー ID:** BC30392  
  
### このエラーを解決するには  
  
1.  `Catch` ステートメントを削除するか、または `Catch` の対象を実際の例外に変更します。  
  
## 参照  
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Visual Basic の構造化例外処理の概要](http://msdn.microsoft.com/ja-jp/bb81af80-a735-4873-9711-6151a48e418a)