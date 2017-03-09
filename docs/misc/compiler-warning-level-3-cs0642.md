---
title: "コンパイラの警告 (レベル 3) CS0642 | Microsoft Docs"
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
  - "CS0642"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0642"
ms.assetid: e2df58c0-9b7e-4e50-8e31-e0134955f62c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラの警告 (レベル 3) CS0642
empty ステートメントが間違っている可能性があります  
  
 条件付きステートメントの後にセミコロンがあると、コードが予定どおりに実行されないことがあります。  
  
 **\/nowarn** コンパイラ オプションまたは `#pragmas warning` を使用すると、この警告を無効にできます。詳細については、「[\/nowarn \(Suppress Specified Warnings\)](/dotnet/csharp/language-reference/compiler-options/nowarn-compiler-option)」または「[\#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)」を参照してください。  
  
 次の例では CS0642 が生成されます。  
  
```  
// CS0642.cs // compile with: /W:3 class MyClass { public static void Main() { int i; for (i = 0; i < 10; i += 1);   // CS0642 semicolon intentional? { System.Console.WriteLine (i); } } }  
```