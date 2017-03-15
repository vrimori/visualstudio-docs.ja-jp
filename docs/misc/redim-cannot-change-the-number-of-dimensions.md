---
title: "&#39;ReDim&#39; で次元数を変更することはできません | Microsoft Docs"
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
  - "vbrArray_RankMismatch"
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; で次元数を変更することはできません
`ReDim` ステートメントを使用して、配列のランク \(次元の数\) を変更する操作が行われました。`ReDim` は既に宣言された配列の 1 つ以上の次元のサイズを変更するために使用できますが、配列のランクを変更することはできません。  
  
### このエラーを解決するには  
  
-   次元のサイズではなく、配列のランクを変更しようとしていることを確認します。可能な場合は、`Dim` を使用して、希望のランクを持つ配列を新規に宣言します。  
  
## 参照  
 [NOTINBUILD Visual Basic の配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [NOTINBUILD Visual Basic における多次元配列](http://msdn.microsoft.com/ja-jp/d92cad25-07e2-4d79-8ea4-ab269700f5de)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)