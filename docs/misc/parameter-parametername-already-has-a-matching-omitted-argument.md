---
title: "パラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します | Microsoft Docs"
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
  - "vbc36566"
  - "bc36566"
helpviewer_keywords: 
  - "BC36566"
ms.assetid: b37af6bc-abd0-4436-bf8a-a467e3603342
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# パラメーター &#39;&lt;parametername&gt;&#39; には、一致する省略された引数が既に存在します
プロシージャ呼び出しは、位置による引数を省略した後で、名前によって同じ引数を指定しています。 例を次に示します。  
  
```vb#  
Public Sub ABC(ByVal X As Byte, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) ' ... ' Argument Y is omitted by position, but supplied by name. Call ABC(6, , Y:=3)     
```  
  
 **エラー ID:** BC36566  
  
### このエラーを解決するには  
  
-   位置による引数を指定するか、または引数を省略するコンマを削除します。  
  
## 参照  
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)