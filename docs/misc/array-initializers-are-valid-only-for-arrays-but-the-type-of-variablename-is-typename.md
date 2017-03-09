---
title: "配列初期化子は配列に対してのみ有効ですが、&#39;&lt;variablename&gt;&#39; の型は &#39;&lt;typename&gt;&#39; です | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30679"
  - "vbc30679"
helpviewer_keywords: 
  - "BC30679"
ms.assetid: 3cf34882-7a58-4074-8ebb-52e58199a506
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列初期化子は配列に対してのみ有効ですが、&#39;&lt;variablename&gt;&#39; の型は &#39;&lt;typename&gt;&#39; です
非配列変数を値のリストで初期化しようとしました。  
  
 **エラー ID:** BC30679  
  
### このエラーを解決するには  
  
-   変数を配列として宣言し、初期化します。次に例を示します。  
  
     `Dim intarray As Integer() = {1, 5, 9}`  
  
-   変数を単一の値として初期化します。次に例を示します。  
  
     `Dim intvalue As Integer = 1`  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [変数宣言](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)   
 [配列](/dotnet/visual-basic/programming-guide/language-features/arrays/index)