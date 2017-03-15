---
title: "配列変数を宣言するために &#39;ReDim&#39; ステートメントを使用することはできません | Microsoft Docs"
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
  - "bc30811"
  - "vbc30811"
helpviewer_keywords: 
  - "BC30811"
ms.assetid: 9227a06e-a997-4b16-9977-19e2bce9035b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 配列変数を宣言するために &#39;ReDim&#39; ステートメントを使用することはできません
`ReDim` は既存の配列のサイズを変更するためにのみ使用できます。  
  
 **エラー ID:** BC30811  
  
### このエラーを解決するには  
  
-   宣言されるときに、配列のサイズを指定します。例を示します。  
  
    ```  
    Dim X(20) As Integer  
    ```  
  
## 参照  
 [Arrays Summary](/dotnet/visual-basic/language-reference/keywords/arrays-summary)   
 [ReDim Statement](/dotnet/visual-basic/language-reference/statements/redim-statement)   
 [ReDim Statement Changes in Visual Basic](http://msdn.microsoft.com/ja-jp/b4da14db-ff23-490f-b3c6-d7ae1b649532)