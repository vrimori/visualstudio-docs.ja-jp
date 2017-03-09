---
title: "コンパイラ エラー CS0035 | Microsoft Docs"
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
  - "CS0035"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0035"
ms.assetid: a622113e-98a4-4583-992c-1fb55139320a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0035
演算子 'operator' は型 'type' のオペランドに対してあいまいです  
  
 コンパイラには複数の使用可能な変換がありますが、どの変換が選択されるかは演算子を適用する前はわかりません。 詳細については、次のトピックを参照してください。[テンプレート化されたユーザー定義変換](../misc/templated-user-defined-conversions.md) および[変換演算子](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators).  
  
 次の例では CS0035 が生成されます。  
  
```  
// CS0035.cs class MyClass { private int i; public MyClass(int i) { this.i = i; } public static implicit operator double(MyClass x) { return (double) x.i; } public static implicit operator decimal(MyClass x) { return (decimal) x.i; } } class MyClass2 { static void Main() { MyClass x = new MyClass(7); object o = - x;   // CS0035 // try a cast: // object o = - (double)x; } }  
  
```