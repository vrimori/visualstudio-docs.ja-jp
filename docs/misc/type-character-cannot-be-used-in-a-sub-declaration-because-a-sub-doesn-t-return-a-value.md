---
title: "&#39;Sub&#39; は値を返さないため、&#39;Sub&#39; 宣言で型文字を使用することはできません | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Sub&#39; は値を返さないため、&#39;Sub&#39; 宣言で型文字を使用することはできません
`Sub` プロシージャは、`Function` プロシージャと同様に、引数を受け取り、一連のステートメントを実行できる個別のプロシージャです。`Function` プロシージャと異なり、`Sub` は値を返さないため、型宣言を含めることはできません。  
  
 **エラー ID:** BC30303  
  
### このエラーを解決するには  
  
-   `Sub` プロシージャを `Function` プロシージャに変更します。  
  
## 参照  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)