---
title: "コンパイラ エラー CS0192 | Microsoft Docs"
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
  - "CS0192"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0192"
ms.assetid: d3fb6d18-dbf3-42c3-a280-afe55b97c2d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0192
静的読み取り専用フィールド 'name' には、静的コンストラクター内を除き、ref または out を渡すことはできません  
  
 [readonly](/dotnet/csharp/language-reference/keywords/readonly) キーワードでマークされたフィールド \(変数\) は、コンストラクター内部を除き、[ref](/dotnet/csharp/language-reference/keywords/ref) パラメーターまたは [out](/dotnet/csharp/language-reference/keywords/out) パラメーターに渡すことはできません。 詳細については、「[フィールド](/dotnet/csharp/programming-guide/classes-and-structs/fields)」を参照してください。  
  
 `readonly` フィールドが [static](/dotnet/csharp/language-reference/keywords/static) であり、コンストラクターが `static` としてマークされていない場合にも、CS0192 が生成されます。  
  
## 使用例  
 次の例では CS0192 が生成されます。  
  
```  
// CS0192.cs class MyClass { public readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // OK } public void PassReadOnlyRef() { TestMethod(ref TestInt);   // CS0192 } public static void Main() { } }  
```