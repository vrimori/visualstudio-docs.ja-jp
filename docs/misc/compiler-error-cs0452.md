---
title: "コンパイラ エラー CS0452 | Microsoft Docs"
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
  - "CS0452"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0452"
ms.assetid: 50a87734-fe07-4bce-891d-a76e131db6cc
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# コンパイラ エラー CS0452
型 'type name' は、ジェネリック型のパラメーター 'parameter name'、またはメソッド 'identifier of generic' として使用するために、参照型でなければなりません  
  
 このエラーは、`struct` や `int` などの値型を、ジェネリック型または参照型制約のあるジェネリック メソッドのパラメーターとして渡した場合に発生します。  
  
## 使用例  
 次のコードではエラー CS0452 が生成されます。  
  
```  
// CS0452.cs using System; public class BaseClass<S> where S : class { } public class Derived1 : BaseClass<int> { } // CS0452 public class Derived2<S> : BaseClass<S> where S : struct { } // CS0452  
```  
  
## 参照  
 [型パラメーターの制約](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)