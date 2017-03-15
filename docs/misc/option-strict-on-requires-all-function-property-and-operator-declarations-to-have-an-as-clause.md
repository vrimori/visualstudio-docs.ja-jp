---
title: "Option Strict On では、すべての関数、プロパティおよび演算子宣言に &#39;As&#39; 句を指定する必要があります | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、すべての関数、プロパティおよび演算子宣言に &#39;As&#39; 句を指定する必要があります
`As` 句を指定しないでプロパティまたは関数の戻り値を宣言しています。`Option Strict` が `On` の場合は、すべての変数、プロパティ、プロシージャ引数、および関数の戻り値を `As` 句で宣言して、データ型を指定する必要があります。たとえば、`Dim MyNum As Short` のようにします。  
  
 **エラー ID:** BC30210  
  
### このエラーを解決するには  
  
1.  `As` キーワードのスペルが間違っていないか確認します。  
  
2.  宣言したプロパティまたは関数の戻り値に対して `As` 句を指定するか、または `Option Strict Off` を有効にします。  
  
## 参照  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Function プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)