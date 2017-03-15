---
title: "ラベルは、メソッドや複数行ラムダの外側では有効ではありません | Microsoft Docs"
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
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ラベルは、メソッドや複数行ラムダの外側では有効ではありません
ラベルをステートメントに追加できるのは、`Sub`、`Function`、property `Get`、property `Set` プロシージャ内においてのみです。 実行可能なステートメントだけがラベルを持つことができ、実行可能なすべてのステートメントはプロシージャ内にある必要があります。  
  
 **エラー ID:** BC30016  
  
### このエラーを解決するには  
  
1.  ステートメントからラベルを削除するか、ステートメントをプロシージャ内に移動します。  
  
## 参照  
 [How to: Label Statements](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement)