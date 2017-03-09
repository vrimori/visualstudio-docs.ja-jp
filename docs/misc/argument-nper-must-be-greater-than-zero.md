---
title: "引数 &#39;NPer&#39; は 0 より大きくなければなりません | Microsoft Docs"
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
  - "vbrRate_NPerMustBeGTZero"
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数 &#39;NPer&#39; は 0 より大きくなければなりません
`NPer` 関数 \(定期定額払いおよび固定金利に基づいて年金の期間を指定する `Double` を返します\) には、0 を超える引数が必要です。  
  
### このエラーを解決するには  
  
-   式の引数のスペルを確認します。 変数名にスペル ミスがあると、数値型の変数が暗黙的に 0 に初期化されることがあります。  
  
-   式の変数 \(特に、他のプロシージャから引数としてプロシージャに渡されたもの\) に対してこれまで実行した操作を確認します。  
  
## 参照  
 [ビルド内にありません: NPer 関数](http://msdn.microsoft.com/ja-jp/56567d16-29f7-4928-b05f-b4cd56d4fd42)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)