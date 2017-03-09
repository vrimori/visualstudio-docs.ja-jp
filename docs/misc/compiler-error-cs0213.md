---
title: "コンパイラ エラー CS0213 | Microsoft Docs"
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
  - "CS0213"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0213"
ms.assetid: 3c1d55e3-2b84-4c28-8206-ef65869a898c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0213
既に fixed が使用されている式のアドレスを取得するために、fixed ステートメントを使用することはできません。  
  
 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) メソッドまたはパラメーター内のローカル変数は既に \(スタック上に\) 固定されているため、[fixed](/dotnet/csharp/language-reference/keywords/fixed-statement) 式ではこれらの 2 つの変数のアドレスを使用できません。 詳細については、「[unsafe コードとポインター](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)」を参照してください。  
  
## 使用例  
 次の例では CS0213 が生成されます。  
  
```  
// CS0213.cs // compile with: /unsafe public class MyClass { unsafe public static void Main() { int i = 45; fixed (int *j = &i) { }  // CS0213 // try the following line instead // int* j = &i; int[] a = new int[] {1,2,3}; fixed (int *b = a) { fixed (int *c = b) { }  // CS0213 // try the following line instead // int *c = b; } } }  
```