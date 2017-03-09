---
title: "名前付き引数を ParamArray パラメーターに一致させることはできません | Microsoft Docs"
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
  - "bc30587"
  - "vbc30587"
helpviewer_keywords: 
  - "BC30587"
ms.assetid: aff179af-96f2-4157-971e-881d8e08f5f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 名前付き引数を ParamArray パラメーターに一致させることはできません
引数の宣言名、コロンと等号、引数の値の順で記述した名前付き引数を指定しましたが、パラメーター配列を名前で渡すことはできません。 プロシージャを呼び出すときは、パラメーター配列に対してコンマで区切った不特定数の引数を渡しますが、コンパイラは複数の引数を 1 つの名前に関連付けることができません。  
  
 **エラー ID:** BC30587  
  
### このエラーを解決するには  
  
-   名前ではなく位置で引数を渡します。  
  
## 参照  
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)