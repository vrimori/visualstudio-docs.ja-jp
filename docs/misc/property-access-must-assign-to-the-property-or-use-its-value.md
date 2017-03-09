---
title: "プロパティ アクセスはプロパティに割り当てるか､またはその値を使わなければなりません | Microsoft Docs"
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
  - "bc30545"
  - "vbc30545"
helpviewer_keywords: 
  - "BC30545"
ms.assetid: df271c05-1e7a-44e8-bf53-79f06ef916ab
caps.latest.revision: 11
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# プロパティ アクセスはプロパティに割り当てるか､またはその値を使わなければなりません
プロパティへの代入や､その値を使用しないで、プロパティにアクセスしようとしました。 次にコード例を示します。  
  
 [!CODE [VbVbalrErrorSamples#1](VbVbalrErrorSamples#1)]  
  
 **エラー ID:** BC30545  
  
### このエラーを解決するには  
  
-   次の例に示すように、プロパティに値を代入します。  
  
     [!CODE [VbVbalrErrorSamples#3](VbVbalrErrorSamples#3)]  
  
     または  
  
-   次の例に示すように、プロパティの値を使用します。  
  
     [!CODE [VbVbalrErrorSamples#2](VbVbalrErrorSamples#2)]  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Assignment Operators](/dotnet/visual-basic/language-reference/operators/assignment-operators)