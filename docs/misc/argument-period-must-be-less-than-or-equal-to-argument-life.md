---
title: "引数 &#39;Period&#39; は &#39;Life&#39; 引数以下でなければなりません | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 引数 &#39;Period&#39; は &#39;Life&#39; 引数以下でなければなりません
資産の減価償却費計算の対象期間を指定する `Period` 引数の値が `Life` 引数の値より大きくなっています。  
  
### このエラーを解決するには  
  
-   `Life` 引数と `Period` 引数の両方が同じ単位で指定されていることを確認します。 たとえば、`Life` を月単位で指定する場合は、`Period` も月単位で指定します。  
  
## 参照  
 [NOT IN BUILD: DDB 関数](http://msdn.microsoft.com/ja-jp/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NOT IN BUILD: SYD 関数](http://msdn.microsoft.com/ja-jp/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)