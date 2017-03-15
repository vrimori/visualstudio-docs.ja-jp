---
title: "&#39;&lt;methodname&gt;&#39; のパラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します | Microsoft Docs"
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
  - "vbc32021"
  - "bc32021"
helpviewer_keywords: 
  - "BC32021"
ms.assetid: f51d29ba-c5b3-4731-a426-4c5ba11b4e1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methodname&gt;&#39; のパラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します
プロシージャ呼び出しは、位置による引数を省略した後で、名前によって同じ引数を指定しています。次に例を示します。  
  
```  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... Call ABC(6, , Y:=3)   ' Argument Y omitted by position, supplied by name.  
```  
  
 **エラー ID:** BC32021  
  
### このエラーを解決するには  
  
-   位置によって引数を指定するか、または引数を省略するコンマを削除します。  
  
## 参照  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)