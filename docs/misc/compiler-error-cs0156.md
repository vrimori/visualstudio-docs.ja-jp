---
title: "コンパイラ エラー CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0156
引数のない throw ステートメントは、すぐ外側にある catch 句の中に入れ子にされた finally 句の中で使用することはできません。  
  
 パラメーターのない [throw](/dotnet/csharp/language-reference/keywords/throw) ステートメントは、パラメーターが必要ではない **catch** 句の中でのみ使用できます。  
  
 詳細については、「[例外処理ステートメント](/dotnet/csharp/language-reference/keywords/exception-handling-statements)」および「[例外と例外処理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)」をご覧ください。  
  
 次の例では CS0156 が生成されます。  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```