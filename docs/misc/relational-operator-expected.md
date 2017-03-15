---
title: "関係演算子が必要です | Microsoft Docs"
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
  - "bc30239"
  - "vbc30239"
helpviewer_keywords: 
  - "BC30239"
ms.assetid: c5701568-77a1-441b-a0f7-f7b36cbd17e3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 関係演算子が必要です
`Case` ステートメントに `Is` 句が含まれていますが、`=` や `>` などの比較演算子がありません。`Case` ステートメントに演算子が含まれていない場合、`=` を指定したと見なされ、`Is` は使用されません。  
  
 **エラー ID:** BC30239  
  
### このエラーを解決するには  
  
-   `Is` キーワードを削除するか、後に比較演算子を使用します。  
  
## 参照  
 [Select...Case Statement](/dotnet/visual-basic/language-reference/statements/select-case-statement)   
 [Comparison Operators in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators)   
 [Comparison Operators](/dotnet/visual-basic/language-reference/operators/comparison-operators)