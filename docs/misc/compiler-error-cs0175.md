---
title: "コンパイラ エラー CS0175 | Microsoft Docs"
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
  - "CS0175"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0175"
ms.assetid: cedd769d-8258-4235-a321-362981b9f84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0175
キーワード 'base' の使用はこのコンテキストでは有効ではありません。  
  
 [base](/dotnet/csharp/language-reference/keywords/base) キーワードを使用して、基底クラスの特定のメンバーを指定する必要があります。 詳細については、「[コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/constructors)」を参照してください。  
  
 次の例では CS0175 が生成されます。  
  
```  
// CS0175.cs using System; class BaseClass { public int TestInt = 0; } class MyClass : BaseClass { public static void Main() { MyClass aClass = new MyClass(); aClass.BaseTest(); } public void BaseTest() { Console.WriteLine(base); // CS0175 // Try the following line instead: // Console.WriteLine(base.TestInt); base = 9;   // CS0175 // Try the following line instead: // base.TestInt = 9; } }  
```