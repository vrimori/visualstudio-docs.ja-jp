---
title: "コンパイラ エラー CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0215
演算子 true または false の戻り値の型はブール型でなければなりません  
  
 ユーザー定義の [true](/dotnet/csharp/language-reference/keywords/true) と [false](/dotnet/csharp/language-reference/keywords/false) 演算子は [bool](/dotnet/csharp/language-reference/keywords/bool) の戻り値型を持つ必要があります。 詳細については、「[オーバーロードされた演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)」を参照してください。  
  
 次の例では CS0215 が生成されます。  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```