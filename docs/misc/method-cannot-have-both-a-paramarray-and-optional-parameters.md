---
title: "メソッドに ParamArray と Optional パラメーターの両方を指定することはできません | Microsoft Docs"
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
  - "vbc30046"
  - "bc30046"
helpviewer_keywords: 
  - "BC30046"
ms.assetid: 41066df8-c9ee-4f67-9f6c-4f62e3abc7be
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッドに ParamArray と Optional パラメーターの両方を指定することはできません
`ParamArray` 引数は自動的に省略可能であり、プロシージャ宣言内で唯一の省略可能な引数である必要があります。 先行する引数はすべて必須である必要があります。  
  
 **エラー ID:** BC30046  
  
### このエラーを解決するには  
  
-   宣言内の省略可能な引数を削除します。  
  
## 参照  
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)