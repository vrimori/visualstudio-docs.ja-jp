---
title: "&#39;Exit Sub&#39; は、Function または Property では有効ではありません | Microsoft Docs"
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
  - "bc30065"
  - "vbc30065"
helpviewer_keywords: 
  - "BC30065"
ms.assetid: d6426861-ba64-4dca-9100-262c6c058bd9
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Sub&#39; は、Function または Property では有効ではありません
`Exit Sub` は `Function` プロシージャまたは `Property` プロシージャに出現します。`Exit` ステートメントは、出現するブロックと一致する必要があります。  
  
 **エラー ID:** BC30065  
  
### このエラーを解決するには  
  
-   必要に応じて、`Exit Sub` を `Exit Function` または `Exit Property` ステートメントに置き換えます。  
  
## 参照  
 [Sub Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Function プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [Property プロシージャ](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)