---
title: "コンパイラ エラー CS0218 | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0218
型 \('type'\) に演算子 true および演算子 false の宣言が含まれている必要があります  
  
 ユーザー定義型の演算子を定義し、その演算子をショート サーキット演算子として使用する場合、ユーザー定義演算子には演算子 true と演算子 false を定義する必要があります。 ショート サーキット演算子の詳細については、「[&& 演算子](/dotnet/csharp/language-reference/operators/conditional-and-operator)」および「[&#124;&#124; 演算子](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md)」を参照してください。  
  
 次の例では CS0218 が生成されます。  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## 参照  
 [変換演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators)