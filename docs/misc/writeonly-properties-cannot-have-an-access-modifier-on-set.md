---
title: "&#39;Set&#39; で &#39;WriteOnly&#39; プロパティにアクセス修飾子を指定することはできません。 | Microsoft Docs"
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
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Set&#39; で &#39;WriteOnly&#39; プロパティにアクセス修飾子を指定することはできません。
`WriteOnly` プロパティ宣言は、[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) と [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) の両方でアクセス レベルを指定します。  
  
 プロパティのアクセス レベルを常に指定することができます。 さらに、このプロパティのアクセス レベルよりも制限が厳しければ、プロパティ プロシージャ \(`Get` または `Set`\) の 1 つを上限として、異なるアクセス レベルを指定できます。 プロパティ プロシージャの両方にアクセス レベルを指定することはできません。  
  
 **エラー ID:** BC31104  
  
### このエラーを解決するには  
  
-   アクセス修飾子を `Set` ステートメントから削除します。 アクセス修飾子は `WriteOnly` プロパティ全体を表し、プロパティに 2 つのアクセス レベルを指定することはできません。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)