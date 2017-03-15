---
title: "コンパイラ エラー CS0157 | Microsoft Docs"
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
  - "CS0157"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0157"
ms.assetid: a5d9d506-81f8-47dd-85b6-85f8170bcbef
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0157
コントロールが finally 句の本体から出られません。  
  
 [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally) 句のすべてのステートメントを実行する必要があります。 詳細については、「[例外処理ステートメント](/dotnet/csharp/language-reference/keywords/exception-handling-statements)」および「[例外と例外処理](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)」を参照してください。  
  
 次の例では CS0157 が生成されます。  
  
```  
// CS0157.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } finally { return;   // CS0157, cannot leave finally clause } } } }  
```