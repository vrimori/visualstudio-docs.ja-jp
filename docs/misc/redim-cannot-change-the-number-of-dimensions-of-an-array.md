---
title: "&#39;ReDim&#39; によって、配列の次元数を変更することはできません | Microsoft Docs"
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
  - "vbc30415"
  - "bc30415"
helpviewer_keywords: 
  - "BC30415"
ms.assetid: 8ce97188-ff96-4e8c-917c-efc2f94173a3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReDim&#39; によって、配列の次元数を変更することはできません
`ReDim` を使用して、配列のランク \(次元の数\) を変更しようとしました。`ReDim` ステートメントを使用すると、既に正式に宣言されている配列の 1 つ以上の次元のサイズを変更できますが、配列のランクを変更することはできません。  
  
 **エラー ID:** BC30415  
  
### このエラーを解決するには  
  
-   配列のサイズではなく、配列のランクを変更しようとしていることを確認します。可能な場合は、`Dim` を使用して、希望のランクを持つ新しい配列を宣言します。  
  
## 参照  
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [NOTINBUILD Visual Basic の配列の概要](http://msdn.microsoft.com/ja-jp/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)