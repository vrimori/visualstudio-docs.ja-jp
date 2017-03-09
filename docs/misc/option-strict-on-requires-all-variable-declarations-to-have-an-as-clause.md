---
title: "Option Strict On では、すべての変数宣言に &#39;As&#39; 句が必要です | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、すべての変数宣言に &#39;As&#39; 句が必要です
宣言に、`As` 句を使用せずに宣言された変数が含まれています。`Option Strict` が `On` の場合は、すべての変数、プロパティ、プロシージャ引数、および関数の戻り値を `As` 句で宣言して、データ型を指定する必要があります。たとえば、`Dim MyNum As Short` のようにします。  
  
 **エラー ID:** BC30209  
  
### このエラーを解決するには  
  
1.  `As` キーワードのスペルが間違っていないか確認します。  
  
2.  宣言された変数に `As` 句を指定するか、`Option Strict Off` に変更します。  
  
## 参照  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [変数宣言](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)