---
title: "コンパイラ エラー CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0081
型パラメーターの宣言は型ではなく識別子でなければなりません。  
  
 ジェネリック メソッドまたは型を宣言する場合は、"T" や "inputType" など、識別子として型パラメーターを指定します。 クライアント コードでメソッドを呼び出すと型が指定されます。これにより、メソッドまたはクラス本体に出現する各識別子が置き換えられます。 詳細については、「[ジェネリック型の型パラメーター](/dotnet/csharp/programming-guide/generics/generic-type-parameters)」を参照してください。  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)