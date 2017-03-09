---
title: "引数 &#39;&lt;argumentname&gt;&#39; は、1 から 255 の範囲内になければなりません | Microsoft Docs"
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
  - "vbrArgument_Range1toFF1"
ms.assetid: a447f9a6-1c90-4c71-abff-81170331e4c5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数 &#39;&lt;argumentname&gt;&#39; は、1 から 255 の範囲内になければなりません
引数は、0 から 255 の範囲外であるため無効です。  
  
### このエラーを解決するには  
  
1.  式の引数のスペルを確認します。 変数名にスペル ミスがあると、数値型の変数が暗黙的に 0 に初期化されることがあります。  
  
2.  式の変数 \(特に、他のプロシージャから引数としてプロシージャに渡されたもの\) に対してこれまで実行した操作を確認します。  
  
## 参照  
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)