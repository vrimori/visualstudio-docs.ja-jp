---
title: "&lt;error&gt;: &#39;&lt;classname1&gt;&#39; は &#39;&lt;classname2&gt;&#39; から継承されます | Microsoft Docs"
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
  - "bc30256"
  - "vbc30256"
helpviewer_keywords: 
  - "BC30256"
ms.assetid: 170a12ee-87ef-4a49-8c84-ebf57fac435e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;error&gt;: &#39;&lt;classname1&gt;&#39; は &#39;&lt;classname2&gt;&#39; から継承されます
循環継承階層が検出されました。 クラスの継承元として自分自身が指定されているか、このクラスを直接的あるいは最終的な継承元とする別のクラスが指定されています。  
  
 このメッセージは、循環継承のパスをトレースするために複数回表示される可能性があります。  
  
 **エラー ID:** BC30256  
  
### このエラーを解決するには  
  
-   循環継承パスにある少なくとも 1 つの `Inherits` ステートメントを削除して、循環をブレークしてください。  
  
## 参照  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)