---
title: "単一の型指定子で宣言された複数の変数で、明示的な初期化を行うことはできません | Microsoft Docs"
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
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 単一の型指定子で宣言された複数の変数で、明示的な初期化を行うことはできません
複数の変数が同一行で宣言された場合は、初期化できません。  
  
 **エラー ID:** BC30671  
  
### このエラーを解決するには  
  
1.  各項目を別個に宣言および初期化します。  
  
2.  複数の項目を一緒に宣言し、次に各項目を初期化します。次に例を示します。  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## 参照  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [変数宣言](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)