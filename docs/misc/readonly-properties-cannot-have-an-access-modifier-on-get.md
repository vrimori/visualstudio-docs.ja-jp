---
title: "&#39;ReadOnly&#39; プロパティでは、&#39;Get&#39; でアクセス修飾子を指定することはできません | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;ReadOnly&#39; プロパティでは、&#39;Get&#39; でアクセス修飾子を指定することはできません
`ReadOnly` プロパティの宣言で、[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) と [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) の両方でアクセス レベルを指定しています。  
  
 プロパティには常にアクセス レベルを指定できます。 さらに、このプロパティのアクセス レベルよりも制限が厳しければ、プロパティ プロシージャ \(`Get` または `Set`\) の 1 つを上限として、異なるアクセス レベルを指定できます。 両方のプロパティ プロシージャにアクセス レベルを指定することはできません。  
  
 **エラー ID:** BC31105  
  
### このエラーを解決するには  
  
-   `Get` ステートメントからアクセス修飾子を削除します。 アクセス修飾子は `ReadOnly` プロパティ全体を表し、プロパティに 2 つのアクセス レベルを指定することはできません。  
  
## 参照  
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)