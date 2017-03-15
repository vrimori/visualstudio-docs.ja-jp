---
title: "コンパイラ エラー CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0199
静的読み取り専用フィールド 'name' には、静的コンストラクター内を除き、ref または out を渡すことはできません  
  
 [readonly](/dotnet/csharp/language-reference/keywords/readonly) 変数では、それが [ref](/dotnet/csharp/language-reference/keywords/ref) または [out](/dotnet/csharp/language-reference/keywords/out) パラメーターとして渡されるコンストラクターと同じように [static](/dotnet/csharp/language-reference/keywords/static) を使用する必要があります。 詳細については、「[パラメーターの引き渡し](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)」を参照してください。  
  
## 使用例  
 次の例では CS0199 が生成されます。  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```