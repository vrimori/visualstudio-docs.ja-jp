---
title: "コンパイラ エラー CS0242 | Microsoft Docs"
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
  - "CS0242"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0242"
ms.assetid: bc86a5a4-89c1-4de4-a874-4dd4cbf592c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0242
問題の操作は void ポインターで定義されていません。  
  
 void ポインターをインクリメントすることはできません。 詳細については、「[unsafe コードとポインター](/dotnet/csharp/programming-guide/unsafe-code-pointers/index)」を参照してください。  
  
 次の例では CS0242 が生成されます。  
  
```  
// CS0242.cs // compile with: /unsafe class TestClass { public unsafe void Test() { void * p = null; p++;   // CS0242, incrementing a void pointer not allowed } public static void Main() { } }  
```