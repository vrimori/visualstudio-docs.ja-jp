---
title: "コンパイラ エラー CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0170
フィールド 'field' は、割り当てられていない可能性があります  
  
 構造内のフィールドが、最初に初期化しないで使用されています。 この問題を解決するには、初期化されていないフィールドをまず確認し、そのフィールドにアクセスする前に初期化します。 構造体の初期化に関する詳細については、「[構造体](/dotnet/csharp/programming-guide/classes-and-structs/structs)」、および「[構造体の使用](/dotnet/csharp/programming-guide/classes-and-structs/using-structs)」をご覧ください。  
  
 次の例では CS0170 が生成されます。  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```