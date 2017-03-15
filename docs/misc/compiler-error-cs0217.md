---
title: "コンパイラ エラー CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0217
short circuit 演算子として適用するためには、ユーザー定義の論理演算子 \('operator'\) がその 2 つのパラメーターと同じ戻り値の型を持つ必要があります。  
  
 ユーザー定義型として定義した後にショートサーキット演算子として使用する演算子には、同じ型のパラメータと戻り値が必要です。 ショート サーキット演算子の詳細については、「[&& 演算子](/dotnet/csharp/language-reference/operators/conditional-and-operator)」および「[&#124;&#124; 演算子](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md)」を参照してください。  
  
 次の例では CS0217 が生成されます。  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## 参照  
 [オーバーロードされた演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)