---
title: "&#39;TryCast&#39; オペランドは参照型でなければなりませんが、&#39;&lt;typename&gt;&#39; は値型です | Microsoft Docs"
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
  - "BC30792"
  - "vbc30792"
helpviewer_keywords: 
  - "BC30792"
ms.assetid: 3325fce5-dbc0-4d1d-9530-31f4720bfe6e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;TryCast&#39; オペランドは参照型でなければなりませんが、&#39;&lt;typename&gt;&#39; は値型です
`TryCast` 演算子が少なくとも 1 つの引数の値型と共に使用されています。  
  
 `TryCast` は 2 つの引数間の継承または実装のリレーションシップをテストします。 そのため、引数の参照型のみを使用できます。 詳細については、「[Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)」を参照してください。  
  
 **エラー ID:** BC30792  
  
### このエラーを解決するには  
  
-   `DirectCast` または `CType` を使用して変換を実行します。 どちらも値型を使用できます。  
  
## 参照  
 [TryCast Operator](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [DirectCast Operator](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [CType 関数](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)