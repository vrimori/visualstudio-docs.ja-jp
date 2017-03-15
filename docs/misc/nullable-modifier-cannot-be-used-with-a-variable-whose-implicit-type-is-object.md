---
title: "null 許容修飾子は、暗黙的な型が &#39;Object&#39; である変数と共に使用することはできません | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# null 許容修飾子は、暗黙的な型が &#39;Object&#39; である変数と共に使用することはできません
変数宣言に null 許容型修飾子 \(?\) が含まれていますが、型が指定されていないか、宣言する変数に値を割り当てることによって型を推論できるように記述されていません。  
  
 **エラー ID:** BC33112  
  
### このエラーを解決するには  
  
-   null 許容変数を宣言するときに、型を指定します。 型は <xref:System.Object> にはできません。  
  
-   Null 許容変数を宣言するときに、値を割り当てます。 割り当てた値から、null 許容変数の型が推論されます。 値の型は <xref:System.Object> にはできません。  
  
## 参照  
 [Nullable Value Types](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)