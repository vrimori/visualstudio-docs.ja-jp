---
title: "Option Strict On では、演算子 &#39;&lt;operatorname&gt;&#39; に対して Object 型のオペランドを使用することはできません。 | Microsoft Docs"
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
  - "bc32013"
  - "vbc32013"
helpviewer_keywords: 
  - "BC32013"
ms.assetid: cd197da8-2676-453b-884b-3231fb6f909d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、演算子 &#39;&lt;operatorname&gt;&#39; に対して Object 型のオペランドを使用することはできません。
Option Strict On では、演算子 '\<operatorname\>' に対して Object 型のオペランドを使用することはできません。 Is 演算子を使用して、オブジェクト ID をテストします。  
  
 `Option Strict` が `On` である場合、`=` などの算術比較演算子が、1 つまたは複数のオブジェクト変数と共に使用されます。  
  
 **エラー ID:** BC32013  
  
### このエラーを解決するには  
  
1.  オブジェクト変数に数値が含まれており、算術比較する場合は、`Option Strict Off` をオンにします。  
  
2.  `Is` 演算子を使用して、オブジェクト ID を比較します。  
  
## 参照  
 [Comparison Operators](/dotnet/visual-basic/language-reference/operators/comparison-operators)   
 [Is Operator](/dotnet/visual-basic/language-reference/operators/is-operator)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)