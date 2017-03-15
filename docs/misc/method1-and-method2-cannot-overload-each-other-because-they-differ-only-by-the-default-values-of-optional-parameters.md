---
title: "&#39;&lt;method1&gt;&#39; および &#39;&lt;method2&gt;&#39; は、省略可能なパラメーターの既定値しか異ならないため、互いをオーバーロードすることはできません | Microsoft Docs"
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
  - "vbc30305"
  - "bc30305"
helpviewer_keywords: 
  - "BC30305"
ms.assetid: f07f925e-9f95-4885-bdba-eaba2d0483d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;method1&gt;&#39; および &#39;&lt;method2&gt;&#39; は、省略可能なパラメーターの既定値しか異ならないため、互いをオーバーロードすることはできません
オーバーロードしようとしたメソッドは、省略可能なパラメータしか異なっていません。 省略可能なパラメーターを持つメソッドは、省略可能なパラメーターを持つバージョンと持たないバージョンの 2 つのオーバーロードされたメソッドと同じです。 このため、いずれかのバージョンの引数リストと一致する引数リストを使ってメソッドをオーバーロードすることはできません。  
  
 **エラー ID:** BC30305  
  
### このエラーを解決するには  
  
-   省略可能なパラメーター以外の部分が異なっているメソッドでオーバーロードします。  
  
## 参照  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)