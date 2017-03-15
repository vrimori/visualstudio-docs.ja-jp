---
title: "&#39;&lt;method1&gt;&#39; と &#39;&lt;method2&gt;&#39; は、&#39;ParamArray&#39; として宣言されているパラメーターが異なるだけなので、お互いにオーバーロードすることはできません | Microsoft Docs"
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
  - "bc30368"
  - "vbc30368"
helpviewer_keywords: 
  - "BC30368"
ms.assetid: 6111df0c-fc3e-40b2-b536-effbd132ef72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;method1&gt;&#39; と &#39;&lt;method2&gt;&#39; は、&#39;ParamArray&#39; として宣言されているパラメーターが異なるだけなので、お互いにオーバーロードすることはできません
`ParamArray` パラメーターのみが異なる 2 つのメソッドをオーバーロードしようとしました。 コンパイラでは、`ParamArray` パラメーターを持つプロシージャはパラメーター配列に渡される内容が互いに異なる無数のオーバーロードを含むものと見なされます。  
  
 **エラー ID:** BC30368  
  
### このエラーを解決するには  
  
-   メソッドが `ParamArray` パラメーター以外のもので区別されていることを確認します。  
  
## 参照  
 [Considerations in Overloading Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Parameter Arrays](/dotnet/visual-basic/programming-guide/language-features/procedures/parameter-arrays)