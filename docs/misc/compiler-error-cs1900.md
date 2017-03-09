---
title: "コンパイラ エラー CS1900 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1900"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1900"
ms.assetid: 08141138-bfea-4af3-a9a0-ec54cf2caa13
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS1900
警告レベルの範囲は 0\-4 です。  
  
 [\/warn](/dotnet/csharp/language-reference/compiler-options/warn-compiler-option) コンパイラ オプションでは、5 つの使用可能な値 \(0、1、2、3、または 4\) の 1 つのみを指定できます。**\/warn** にその他の値を渡すと、CS1900 が発生します。  
  
 次の例では CS1900 が生成されます。  
  
```  
// CS1900.cs // compile with: /W:5 // CS1900 expected class x { public static void Main() { } }  
```