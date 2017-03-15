---
title: "Sub または Set の &#39;Return&#39; ステートメントで値を返すことはできません | Microsoft Docs"
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
  - "bc30647"
  - "vbc30647"
helpviewer_keywords: 
  - "BC30647"
ms.assetid: d4c05c28-d650-4f49-976e-650d84802036
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub または Set の &#39;Return&#39; ステートメントで値を返すことはできません
`Sub` プロシージャおよびプロパティ `Set` プロシージャが値を返すことができません。  
  
 **エラー ID:** BC30647  
  
### このエラーを解決するには  
  
-   現在のプロシージャを関数に変更するか、または現在のプロシージャがプロパティの一部である場合には `Get` プロパティ プロシージャに変更します。  
  
-   `ByRef` キーワードを使用して参照渡しでパラメーターの値を変更すると、`Sub` プロシージャから値を効率的に返すことができます。  
  
## 参照  
 [Return Statement](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)