---
title: "コンパイラ エラー CS0255 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0255
stackalloc は catch または finally ブロックで使用されない可能性があります。  
  
 [stackalloc](/dotnet/csharp/language-reference/keywords/stackalloc) キーワードは [catch](/dotnet/csharp/language-reference/keywords/try-catch) または [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally) ブロックで使用できません。 詳細については、「[例外と例外処理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)」を参照してください。  
  
 次の例では CS0255 が生成されます。  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```