---
title: "Option Strict On では、すべてのメソッド パラメーターに &#39;As&#39; 句が必要です | Microsoft Docs"
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
  - "vbc30211"
  - "bc30211"
helpviewer_keywords: 
  - "BC30211"
ms.assetid: 855795ce-8499-4525-a1de-cbb8ba364cd7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On では、すべてのメソッド パラメーターに &#39;As&#39; 句が必要です
メソッドに、`As` 句のないパラメーターが含まれています。`Option Strict` が On の場合は、すべての変数、プロパティ、プロシージャ引数、および関数の戻り値を `As` 句で宣言して、データ型を指定する必要があります。たとえば、「`Sub GetData(ByVal filter As String)`」のようにします。  
  
 **エラー ID:** BC30211  
  
### このエラーを解決するには  
  
-   `As` キーワードのスペルが間違っていないか確認します。  
  
-   宣言された変数に `As` 句を付けるか、`Option Strict` Off に変更します。  
  
## 参照  
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function Statement](/dotnet/visual-basic/language-reference/statements/function-statement)