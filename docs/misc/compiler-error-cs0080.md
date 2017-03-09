---
title: "コンパイラ エラー CS0080 | Microsoft Docs"
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
  - "CS0080"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0080"
ms.assetid: 99035371-37d1-48b2-a8b9-e8a1ebd04f0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0080
制約は非ジェネリック宣言では許可されません。  
  
 検出された構文は、型パラメーターに制約を適用するために、ジェネリック宣言でのみ使用できます。 詳細については、「[ジェネリック](/dotnet/csharp/programming-guide/generics/index)」を参照してください。  
  
 次の例では、MyClass がジェネリック クラスではなく、Foo がジェネリック メソッドではないため、CS0080 が生成されます。  
  
```  
namespace MyNamespace { public class MyClass where MyClass : System.IDisposable // CS0080    //the following line shows an example of correct syntax //public class MyClass<T> where T : System.IDisposable { public void Foo() where Foo : new() // CS0080 //the following line shows an example of correct syntax //public void Foo<U>() where U : struct { } } public class Program { public static void Main() { } } }  
```