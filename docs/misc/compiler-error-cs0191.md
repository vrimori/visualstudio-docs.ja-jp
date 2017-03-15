---
title: "コンパイラ エラー CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0191
プロパティまたはインデクサー 'name' は読み取り専用なので、割り当てることはできません  
  
 [readonly](/dotnet/csharp/language-reference/keywords/readonly) フィールドでは、コンストラクターまたは宣言時の割り当てだけを行うことができます。 詳細については、「[コンストラクター](/dotnet/csharp/programming-guide/classes-and-structs/constructors)」を参照してください。  
  
 `readonly` フィールドが [static](/dotnet/csharp/language-reference/keywords/static) であり、コンストラクターが `static` としてマークされていない場合にも、CS0191 が発生します。  
  
## 使用例  
 次の例では CS0191 が生成されます。  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```